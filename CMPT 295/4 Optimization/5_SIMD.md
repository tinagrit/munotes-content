Lecture 16

## Data Parallelism
Data parallelism utilizes vector **SIMD** (*single instruction multiple data*) operations. This is done by giving the processor vectors of values, and ask it to do the same operation on all of them. 

![[Screenshot 2026-08-11 at 6.53.55 PM.png|400]]

This is still working **one instruction at a time**, but the one instruction can take on many values at once.

### SIMD registers
The `%xmm(n)` registers present in [[6_Floating Point|floating point]] are SIMD registers in x86-64, specifically they are the [[2_Registers#Calling Convention|lower]] 128 bits of the 256 bit registers `%ymm(n)`.

An SIMD register can hold any type of data the processor can deal with, as many as will fit.

### SIMD instructions
The SIMD vector instructions are generally named "vector" or "packed", often the 256-bit vector versions have a "v" prefix.

The vector instructions require separate source and destination operands. This means:
```nasm
vaddpd %ymm0, %ymm1, %ymm2
```
translates to:
```c
ymm2 = ymm0 + ymm1;
```

The floating point instructions include:

| Instruction         | Meaning                         |
| ------------------- | ------------------------------- |
| `vaddpd` / `addps`  | Add packed double / single      |
| `vsubpd` / `vsubps` | Subtract packed double / single |
| `vmulpd` / `vmulps` | Multiply packed double / single |
| `vdivpd` / `vdivps` | Divide packed double / single   |

The integer instructions include:

| Instruction                               | Meaning                                          |
| ----------------------------------------- | ------------------------------------------------ |
| `vpaddb` / `vpaddw` / `vpaddd` / `vpaddq` | Packed add byte / word / long / quadword         |
| `vpsubb` / `vpsubw` / `vpsubd` / `vpsubq` | Packed subtract byte / word / long / quadword    |
|                                           | ... same format for multiply, shift, and compare |

The move instructions include:

| Instruction | Meaning                                  |
| ----------- | ---------------------------------------- |
| `vmovupd`   | Move unaligned packed double             |
| `vmovapd`   | Move aligned packed double               |
| `vmovups`   | Move unaligned packed single             |
| `vmovaps`   | Move aligned packed single               |
| `vmovdqa`   | Move double quadword integers, aligned   |
| `vmovdqu`   | Move double quadword integers, unaligned |
(see [[7_Data Alignment#Alignment|data alignment]])

These move instructions require that the data we want are **adjacent in memory**. We can work with an array of integers, but if we have a struct like:
```c
struct rgb {
	uint8_t red;
	uint8_t green;
	uint8_t blue;
}
```
and we want to extract the `red`s, it is hard to get them into SIMD registers to get started.

### Summing an array
We will be writing assembly code to sum an array of `double` using SIMD. Using the `%ymm(n)` 256-bit registers, we can work with **4 doubles at a time**.

We will assume that the array length is divisible by 4.

Using the function signature:
```c
double sum(double* arr, uint64_t len);
```

We will use `%ymm0` as the accumulator, and `%rcx` as a counter
```nasm
sum:
	vxorpd %ymm0, %ymm0, %ymm0    # ymm0 = 0
	mov $0, %rcx                  # rcx = 0
sum_loop:
	cmp %rsi, %rcx                # if rcx >= len
	jae sum_return                # , return
	
	vaddpd (%rdi, %rcx, 8), %ymm0, %ymm0   
	                              # ymm0 += arr[rcx*8]
	
	add $4, %rcx                  # rcx += 4
	jmp sum_loop
```

Here, in the main loop, we are adding 4 to the counter (`%rcx`) at a time, because we are working with 4 `double`s at a time.

At the end of the loop, we are left with a slightly awkward `%ymm0`, with each 64-bit increment including the sum of each quarter of the array:
![[Screenshot 2026-08-11 at 7.28.06 PM.png|500]]

The full code for the ***horizontal add*** is as follows:
```nasm
vextractf128 $0x1, %ymm0, %xmm1
vaddpd %xmm1, %xmm0, %xmm0
vshufpd $0b01, %xmm0, %xmm0, %xmm1
vaddsd %xmm1, %xmm0, %xmm0
ret
```


---
## Vectorclass
Vectorclass is a library in C++ to allow access to SIMD functionality **without writing assembly**.

This library provides C++ types to represent values packed into SIMD registers:

| Type     | Contents  | Count |
| -------- | --------- | ----- |
| `Vec4q`  | `int64_t` | 4     |
| `Vec8i`  | `int32_t` | 8     |
| `Vec16s` | `int16_t` | 16    |
| `Vec4d`  | `double`  | 4     |
| `Vec8f`  | `float`   | 8     |

These types also include a constructor that takes either a single constant to put the same value in every fields, or values to set each field.

```cpp
Vec8f v1 = Vec8f(0.0);
Vec8f v2 = Vec8f(0,1,2,3,4,5,6,7);
```

The normal operations are also ***overloaded*** to do element-by-element operations on the values.

```cpp
v1 += v2;
v1 = v1 * v2;
```

The types include a `load()` method to load values from a memory location to a register
```cpp
double array[4] = {1,2,3,4};
Vec4d a;
a.load(array);
```

, a `store()` method to store values from a register to memory, and a `horizontal_add()` function to help add the register. The same `sum()` from above would look like this in Vectorclass:

```cpp
double sum(double* arr, uint64_t len) {
	Vec4d acc = Vec4d(0);
	Vec4d tmp;
	
	for (uint64_t i = 0; i < len; i += 4) {
		tmp.load(array + i);
		acc += tmp;
	}
	
	return horizontal_add(acc);
}
```

