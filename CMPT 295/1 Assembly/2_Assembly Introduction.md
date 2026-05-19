Lecture 1

## Writing assembly
Learning assembly can help us understand:
- machine architecture
- how the machine architecture affects the code we write in a programming language
- what the compiler is/isn't doing, or can/can't do on our behalf
- a rare case where implementing some critical logic in assembly can be worth it

We are using **x86-64 assembly** with the **AT&T syntax**, *not* the Intel syntax. If you see a lot of punctuation like `%` and `$` everywhere, that's AT&T syntax.

### add10 Example
We are writing a function `add10` in assembly and call it in C. This function should add 10 to the given 64-bit integer.

Consider the header **add10.h**:
```c
#include <stdint.h>
int64_t add10(int64_t n);
```

and the test C program **add10_test.c**:
```c
#include <stdint.h>
#include <stdio.h>
#include "add10.h"

int main() {
	int64_t n = 1234;
	int64_t m = add10(n);
	printf("%ld + 10 = %ld\n", n, m);
}
```

We are writing the following **add10.S** with assembly:
```asm
	.section .note.GNU-stack, ""
	.global add10
	.text

add10:
	mov %rdi, %rax
	add $10, %rax
	ret
```

Here, `add10` is the **label**, a marker for a location in memory. The location of the next instruction (`mov`) is referred to as the label.

The instruction `mov` has two **operands**, `%rdi` and `%rax`
- `%rdi` is the **source**
- `%rax` is the **destination**
- `mov` **copies** the value from the source to the destination

Both `%rdi` and `%rax` are **x86-64 registers**, a storage location inside the processor, large enough to hold one 64-bit value.

The instruction `add` **adds** one integer to another. In this syntax, `$` is placed in front of **literal numeric values**. This line is equivalent to the C's `rax += 10;`.

The instruction `ret` returns `%rax` from the function.

The first 3 lines are the **headers** to the assembly code.
- `.section` says we won't be putting executable code on the stack, which is a security problem
- `.global` exports the `add10` label so the linker can see it
- `.text` marks the start of a code section

Using `gcc` and `as` as shown in [[1_C and Assembly#Assembling|Assembling C]], we can compile the **.c** and **.S** into **.o**, then into an executable as shown in [[1_C and Assembly#Linking|Linking C]]:
```shell
$ gcc -Wall -c add10_test.c
$ as --warn add10.S -o add10.o
$ gcc add10.o add10_test.o -o add10_test
```

Now we can get the output we expect:
```shell
$ ./add10_test
1234+10 = 1244
```


---
## Registers
Assembly functions can take arguments and return results. This implementation is determined by the calling convention, specifically the **System V AMD64 ABI** that is used in *Linux* and *macOS*.

Having a calling convention lets different compilers and tools **interoperate** with each other. 

Registers are a small number of **very fast storage** locations in the processor. The names in x86-64 registers are historic, and no longer relevant.

### Arguments and return
In the System V calling convention, these are the **non call-preserved registers**:
- Integer arguments are passed in order `%rdi`, `%rsi`, `%rdx`, `%rcx`, `%r8`, `%r9`
- Integer return value must be put in `%rax`
- Floating point arguments are passed in `%xmm0` to `%xmm7`
- Floating point return value must be put in `%xmm0`

| Register         | Name        | Use               |
| ---------------- | ----------- | ----------------- |
| `%rax`           | accumulator | return / anything |
| `%rcx`           | counter     | arg4 / anything   |
| `%rdx`           | data        | arg3 / anything   |
| `%rsi`           | source      | arg2 / anything   |
| `%rdi`           | destination | arg1 / anything   |
| `%r8`            |             | arg5 / anything   |
| `%r9`            |             | arg6 / anything   |
| `%r10`           |             | anything          |
| `%r11`           |             | anything          |
| `%xmm0`-`%xmm15` |             | floating point    |

Each register also has names for the **small fragments** of it. For example, within the 64-bit `%rax`, there's `%eax`, `%ax`, `%ah`, `%al` representing each part of `%rax`:

![[chart02.png|450]]

### Preservation
Some registers are **call-preserved**. Functions *must* guarantee that these register values will not be changed. This is because there is no equivalent of **local variables** for the registers, and our code needs to maintain data across function calls.

These registers are **preserved**: `%rbx`, `%rsp`, `%r12`, `%r13`, `%r14`, `%r15`.

| Register | Name                | Use      |
| -------- | ------------------- | -------- |
| `%rbx`   | base                | anything |
| `%r12`   |                     | anything |
| `%r13`   |                     | anything |
| `%r14`   |                     | anything |
| `%r15`   |                     | anything |
| `%rsp`   | stack pointer       |          |
| `%rbp`   | base pointer        |          |
| `%rip`   | instruction pointer |          |
