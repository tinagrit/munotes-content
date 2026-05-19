Lecture 1

## Running a C code
In the command line, we would use commands like `gcc` or `clang` to compile a C code.

For example, if we have a source code **hello.c** that we want to compile, we can use:
```shell
$ gcc hello.c -o hello
```

We can also add these options to specify what we really want:
- add more warnings: `-Wall -Wpedantic`
- use a modern C standard: `-std=c17`
- target a reasonably-recent CPU architecture: `-march=haswell`
```shell
$ gcc -Wall -Wpedantic -std=c17 -march=haswell hello.c -o hello
```

Then run the compiled executable with:
```shell
$ ./hello
```

Under the hood, there are many steps to get to the executable.

![[chart01.png|700]]


### Multi-file C
We can include multiple C files into one executable for things like libraries and modularization to work.

For example, in **hello.c**, we can use functions from **lib.c** by including the header file **lib.h** with function signatures.

**hello.c**:
```c
#include <stdio.h>
#include "lib.h"

int main() {
	...
```

> [!tip] Note
> `#include` with <...> is for system files, and `#include` with "..." is for files in the current directory.

**lib.h**:
```c
#pragma once
int myFunction(int a, int b);
```

> [!tip] Note
> The `#pragma once` tells the compiler to only `#include` this file once.

When we compile these files, we can include all the relevant files to `gcc`, including the source code for **lib.c**:
```shell
$ gcc lib.c hello.c -o hello
```

### Preprocessing
After running `gcc`, the first thing the C compiler does, is to run the code **through the preprocessor**.

This parses **preprocessor directives** likes `#include` and `#define`.
- For `#include`, it does string manipulation to **concatenate** many C source codes.
- For `#define`, it does string manipulation to **search and replace** the variable name to its value. It has some knowledge of C syntax, and won't replace names within string literals.

The preprocessor's **output** is the compiler's **input**.

### Compiling
The compiler takes the preprocessor's output into something that can be executed. 

We can use the `-S` option to compile the C code to **assembly code**.

```shell
$ gcc -S hello.c
```

This generates **hello.s**.

If we have a function like the following in **hello.c**:
```c
int weighted_add(int a, int b, int weight) {
    return a + b*weight;
}
```

We should get an assembly code similar to the following in **hello.s**:
```asm
weighted_add:
    ⋮
	imull	-12(%rbp), %eax
    ⋮
	addl	%edx, %eax
    ⋮
	ret
```

The **.s** file is **assembly code**, which is a somewhat human-readable description of the logic that needs to **run on the processor**, and **can be assembled**.

A **.S** (capital S) denotes hand-written assembly, as opposed to compiler-generated assembly. **.S** files are run through the C preprocessor, but **.s** files are not.

> [!warning] Note
> Assembly code is **architecture-specific**. We are working with **x86-64** assembly code. The code would look different on ARM or RISC-V.

### Assembling
The assembler takes a **.s** code and assemble it to bytes that can be sent to the processor to execute.

We can use the **GNU assembler** `as` to assemble the assembly code:
```shell
$ as hello.s -o hello.o
```

We can also use the `-c` option in `gcc` to generate the **.o** directly from a C source code:
```shell
$ gcc -c hello.c
```

Both of these methods generate **hello.o**.

The **.o** file is **object file**, a machine code as a fragment of an executable program. Machine code consists of instructions, which are what the processor's instruction register needs.

For example, with this instruction that means "move the contents of register `rdi` to `rax`":
```asm
mov %rdi, %rax
```

It gets translated to these three bytes, represented in binary or hexademical
```
01001000 10001001 11111000
48 89 F8
```

### Linking
We can use `gcc` as a linker to turn the object file into an executable:
```shell
$ gcc hello.o -o hello
```

If `gcc` receives an object **.o** file, it skips preprocessing and compiling, and only does the linking.

Linker is usually done with `ld`, however, this won't work:
```shell
$ ld hello.o -o hello
```
```output
ld: warning: cannot find entry symbol _start; defaulting to 0000000000401000
ld: program.o: in function `printf':
/usr/include/x86_64-linux-gnu/bits/stdio2.h:112: undefined reference to `__printf_chk'
```

This is because it is missing `printf` and `_start`
- `printf` definition is under `libc.a`, which can be included with the `-lc` option
- `_start` is the entry point of the program. This logic is provided by the C runtime (**crt**) to set up the process and call the `main` function. We need to include `crt1.o`.
- We also need to tell the linker the "*dynamic linker*" to find shared libraries

```shell
$ ld -o hello hello.o -lc /usr/lib/x86_64-linux-gnu/crt1.o --dynamic-linker /lib64/ld-linux-x86-64.so.2
```
