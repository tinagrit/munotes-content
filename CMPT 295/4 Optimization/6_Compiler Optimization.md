Lectures 16-17, 19

## C to Assembly Optimizing
Usually, the compiler is a [[2_Branch Hazards#Avoiding branches cmov|better assembly programmer]] than humans. There are many ways to write C with bad performance, which we can avoid, such as bad algorithm, unpredictable branches, etc.

Almost always, **having an idea** what assembly the compiler will write for us is more important than hand-writing that assembly. Since machine generated code is difficult to read, there are tools to **help annotate** assembly.

### Compiler Explorer
[Link to the Compiler Explorer →](https://godbolt.org/)

The compiler explorer runs our code through a compiler and show us the assembly output, helpfully annotated.

When hovering on a C/C++ code line on the left, the associated assembly is highlighted on the right.

![[Screenshot 2026-07-31 at 12.07.18 PM.png]]

In this example, C++ line 8 is highlighted, and on the right, `vpadd` is used for vectorized add, and `addl` is used in case the array isn't divisible by 8.

Using `-O0` will generate assembly more closely resembling the logic in C++, and using `-O3` will generate **more aggressive** compilation, with higher **optimization**, but less readable.

### Inline assembly
If we don't like the assembly made by the compiler, and really **want to control** the output, it's possible to write inline assembly in C and C++.

We also have to give the compiler enough information to integrate it with the code. We need to say which C variables we're changing, reading, and which registers we're going to overwrite the contents of:

```c
__asm__(
    assembly_code
    : output_operands
    : input_operands
    : registers_used
);
```

For example,
```cpp
uint64_t a, b, c, d;
a = 100;
b = 200;
c = 3;
d = 4;
__asm__(
    "mov $5000, %%rax\n"
    "mov %%rax, %0\n"
    "add %2, %0\n"
    "mov %3, %1\n"
    : "+r"(c), "+r"(d)  // %0 and %1 in the assembly
    : "r"(a), "r"(b)    // %2 and %3 in the assembly
    : "rax"             // %rax is clobbered
);
```

This should be the **last resort**. Inline assembly is almost certainly a bad idea. It makes the C code non-portable, and has all of the danger of assembly.

### Intrinsics
In [[5_SIMD#Vectorclass|vectorclass]], we use a C++ function to ask the compiler **directly** to vectorize the code. We can also ask the compiler to use a **different assembly instruction**.

**Compiler intrinsics** are functions that have some special meaning to the compiler. Typically, they mean use _this_ assembly instruction, or some fallback if it's not available.

For example, the function `_mm256_add_ps()` is asking the compiler to use the instruction `vaddps` in assembly, or as we've seen in [[4_Tools#Measuring cycles|code timing]], `__rdtsc()` means the instruction `rdtsc` in assembly.

### The Optimizer
Most of the time, we won't need inline assembly or intrinsics, and the compiler is smart enough to turn the code into an optimized assembly.

There are other flags apart from `-O0` and `-O3`:
- `-O0` no optimization (default)
- `-O1` basic optimizations that don't take too much compile time
- `-O2` most optimizations
- `-O3` aggressive optimization
- `-Og` optimize for debugging, similar to `-O1`
- `-Os` optimize for small executable, similar to `-O2`

`-O3` ***could*** sometimes cause worse performance because it's so aggressive with its choices, but most of the time it is faster since it turns on auto-[[5_SIMD|vectorization]].

One example of an optimization that a compiler could do, is by **combining addition and multiplication**. Recall [[2_Memory in Assembly#Loading pointer|loading effective pointer]] (*lea*). `lea` can do basic arithmetic in one instruction. `5(%rdi, %rdi, 4)` would mean `5+(rdi + rdi*4)` and `lea` can put the result into another register. This can help us avoid adding and multiplying in separate instructions.

The compiler will also do things like moving expressions out of a loop if they don't need to be repeated.

The optimizer will sometimes replace a branch with a [[2_Branch Hazards#Avoiding branches cmov|cmov]].

Therefore, with these optimizations being automated, we should **write readable, expressive, clear, idiomatic code**. Let the optimizer figure out how to rearrange our code to be fast.

Don't try to be clever, until profiling and the Compiler Explorer prove it's necessary.

### Auto-vectorization
Since [[5_SIMD|Vectorization]] helps speed up code, we would **like to utilize** it whenever appropriate. We also don't want to be writing assembly or having to use low-level tools like intrinsics.

Some auto-vectorization happens at `-O2`, but mostly at `-O3`.

Sometimes, a specific feature of the code must be present for auto-vectorization to work, for example:
```c
void add_four_double(double* a, double* b, double* __restrict c) {
    c[0] = a[0] + b[0];
    c[1] = a[1] + b[1];
    c[2] = a[2] + b[2];
    c[3] = a[3] + b[3];
}
```

Here, the vectorization with `vaddpd` only works if we include `__restrict` to the third argument `c`. This promises that there's **no way to modify** from **anywhere else**, and that there is no aliases.

The compiler would usually fail to vectorize [[6_Floating Point|floating point]] values, because by rearranging the algebra of floating point, it can produce a **different result** due to the accumulation of error. ($a+b \neq b+a$ in floating point)

We can also tell the compiler to **ignore that restriction**, by including the flag `-funsafe-math-optimizations`, which will allow the compiler to vectorize floating point operations. However, this should be done **with caution** since it will affect the rounding errors.

### Tail Calls
If we have a function that returns the result of another function (possibly [[5_Stack#Recursion|recursive]]), like this:
```c
int f1(???) {
	???
	return f2(???);
}
```

This is what it would look like in assembly:
```nasm
	...
	call f1

f1:
	...
	call f2
	ret

f2:
	...
	ret
```

After `f2` is done, there is **nothing left to do** in `f1` except for returning. The `ret` from `f2` would pop the stack and go back to the instruction at `f1`, then `ret` from `f1` again.

Some compilers may do **tail call optimization**, where a `call` is replaced with `jmp`s instead, for tail call cases.

```nasm
	...
	call f1

f1:
	...
	jmp f2

f2:
	...
	ret
```

