Lectures 8-10

## Assembly segments
A segment in assembly tells the [[1_C and Assembly#Assembling|assembler]]/[[1_C and Assembly#Linking|linker]] which part is what section. 

### Code segment
Notice at the beginning of any assembly `.S` file, we have:
```nasm
   .text
```

This tells the assembler/linker that what's about to follow **is code**. 

This is important to the [[3_Processor#Memory|Von Neumann architecture]] since **both the data** we work with **and the program itself** will be stored in [[1_Memory#The memory|memory]].

### Data segment
The `.data` segment can store values that will be initialized when the program starts as **static values**.

In assembly, we can do:
```nasm
.data
my_value:
	.quad 1234
```
, which is the same as doing:
```c
static int64_t my_value = 1234;
```

The **label** that we use in assembly code works the same way as data. In this case, the label `my_value` is used to store the `.quad` (64-bit "quad word", see [[6_Operand Size#Ambiguous case|operand size]]) value of `1234`.

We can also use `.fill` to create an initialized array-like **memory space**. `.fill` takes how many entries, how many bytes per entry, and an initial value.

```nasm
.data
my_array:
	.fill 100, 8, 0
```
is the same as:
```c
static int64_t array[100] = 0;
```

### BSS segment
The `.bss` segment is similar to the `.data` segment, but is an **uninitialized** static memory. 

For example, this assembly code:
```nasm
.bss
my_array:
	.fill 100, 8
```
is the same as:
```c
static int64_t array[100];
```

The `.bss` data takes **almost no space** in the executable since we are only telling the assembler that we **need this much** uninitialized bytes.


---
## Static memory in assembly
If we use the [[#Data segment]] to initialize static memory, we can access it in assembly using the label. For example:

```nasm
.data
n:
	.quad 1234
```

Here, `n` is a numeric **memory address** to our 64-bit value. 

### Summary
This is the summary table of everything below:

| Mode                                               | Example            | Meaning                       |
| -------------------------------------------------- | ------------------ | ----------------------------- |
| Indirect [[#Loading pointer\|→]]                   | `(%rbx)`           | `memory[rbx]`                 |
| Indirect [[#Loading pointer\|→]]                   | `label`            | `label`                       |
| Indirect (not PIE) [[#Loading pointer\|→]]         | `(label)`          | `memory[label]`               |
| Indexed [[#Scaling\|→]]                            | `(%rbx, %rcx)`     | `memory[rbx + rcx]`           |
| Scaled [[#Scaling\|→]]                             | `(%rbx, %rcx, 8)`  | `memory[rbx + (rcx * 8)]`     |
| Offset [[#Offset\|→]]                              | `4(%rbx)`          | `memory[rbx + 4]`             |
| Scaled + Offset [[#Offset\|→]]                     | `4(%rbx, %rcx, 8)` | `memory[rbx + (rcx * 8) + 4]` |
| RIP relative (PIE) [[#RIP relative addressing\|→]] | `label(%rip)`      | `memory[label]`               |


### Accessing
To access the value from the address, we use parenthesis `()` the same way as we access the [[5_Stack#Stack pointer|stack pointer]]:
```nasm
mov (n), %rdi
```
This moves the value at address `n` (`$1234`) into `%rdi`.
- `n = [address]`
- `rdi = 1234`

### Loading pointer
To move the numeric **memory address** (pointer) into a register, we need to use the instruction `lea` (*Load Effective Address*) like follows:
```nasm
lea n, %rbx
```

Now, `%rbx` contains the memory address that `n` has. We can access the value with `%rbx`:
```nasm
mov (%rbx), %rdi
```
This moves the value at address `%rbx` (`1234`) into `%rdi`.
- `n = [address]`
- `rbx = [address same as above]`
- `rdi = 1234`

### Using arrays
With `lea`, we can now work with arrays. We can **copy** (`lea`) **the start address** of the array and increment the value as we go. 

For example, if we have a static array:
```nasm
.data
arr:
	.quad 6
	.quad 7
	.quad 8
	.quad 9
```

We can access each one by:
```nasm
lea arr, %rbx         # copy address from arr to rbx

mov (%rbx), %r8

add $8, %rbx
mov (%rbx), %r9

add $8, %rbx
mov (%rbx), %r10

add $8, %rbx
mov (%rbx), %r11
```

This moves the 4 values in the array into `%r8` - `%r11`.
- `arr = [address at start]`
- `rbx = [address at start] +8 +8 +8`
- `r8 = arr[0]`
- `r9 = arr[1]`
- `r10 = arr[2]`
- `r11 = arr[3]`


If we want to access the $n$<sup>th</sup> element, we will need to add to the address by $(8\times n)$, since each element takes up 8 bytes.

Since $8=2^{3}$, we can use the [[5_Bit Shifting#Bit shift|bit shifting]] trick to **shift left 3 digits** instead of multiplying by 8.

For example, to access the fourth element, we put `3` into `%rcx`:
```nasm
lea arr, %rbx
mov $3, %rcx         # set rcx = 3

shl $3, %rcx         # multiply rcx by 8
add %rcx, %rbx
mov (%rbx), %r8
```

- `arr = [address at start]`
- `rcx = 3 * 8 = 24`
- `rbx = [address at start] + 24`
- `r8 = arr[3]`

### Scaling
Accessing the $n$<sup>th</sup> element in an array like above is very common, and assembly gives us a shortcut for it.

In the same parenthesis that we use to access the memory `(%rbx)`, we can add:
- **second** component: **how far** to add from this address (*this must be a register*)
- **third** component: **how much** to multiply (*one of* 1,2,4,8)

Similar to the code above, we can do:
```nasm
lea arr, %rbx
mov $3, %rcx

mov (%rbx, %rcx, 8), %r8
```

- `arr = [address at start]`
- `rcx = 3` (unlike above, this does not modify `%rcx`)
- `rbx = [address at start] + 24`
- `r8 = arr[3]`

### Offset
As mentioned in [[5_Stack#Stack pointer|stack pointer]], another way to access value at the address $n$ bytes after the start, is to put $n$ before the parenthesis.

For example, to access the fourth element, we need to offset the address by $3 \times 8 = 24$, since each element takes up 8 bytes.

This does not modify the pointer.

We can do:
```
lea arr, %rbx
mov 24(%rbx), %r8
```

- `arr = [address at start]`
- `rbx = [address at start]`
- `r8 = arr[3]`


We can also use a combination of **Scaling+Offsetting**. Notice that using:
- `(%rbx, %rcx, 8)` means $\text{rbx} + (8 \times \text{rcx})_{}$
- `24(%rbx)` means $\text{rbx}+24$

If we use both, like:
```nasm
mov $3, %rcx
mov 4(%rbx, %rcx, 8), %r8
```

This will access the memory location:
$$
\text{rbx} +(8 \times 3) +4
$$
or essentially the **second half** of the **fourth element** of the array at `%rbx`.


---
## Position Independent Executable (PIE)
A *Position Independent Executable* (**PIE**) is a code that can be loaded **anywhere** in the memory. 

Our code above uses **literal memory address** (`n` and `arr`), so it is not position independent. Position independent code uses **relative memory address**, and the exact address or `n` and `arr` can change.

### RIP relative addressing
This is one way to turn **literal** address into **relative** address. The [[1_C and Assembly#Linking|linker]] can promise that the static address will be a certain offset **relative to the** [[3_Processor#Instruction Cycle|instruction pointer]] (`%rip`).

Instead of using:
```nasm
lea arr, %rbx
```

We can use:
```asm
lea arr(%rip), %rbx
```

Now, this code will work everywhere on the memory.

