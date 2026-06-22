Lectures 2 & 3

## Control flow
In assembly, instructions are executed by line, one after the other. Control flow structures help us move around the code.

### Calling
Think of the labels as function names. `call` calls the function and after it is done, returns to the next instruction after `call`.

For example, this assembly code:
```nasm
add10:
	mov %rdi, %rax
	add $10, %rax
	ret
	
_start:
	mov $0, %rdi
	call add10
	add $5, %rax
	call syscall_exit
```

Using the `as` [[1_C and Assembly#Assembling|assembler]], code execution starts at the `_start` label.

First, it puts `0` into the `%rdi` [[2_Registers#Registers|register]].
![[chart06.png|400]]

Then, it calls `add10`. We move the execution up to the `add10` label. It moves the value of `%rdi` to `%rax`.
![[chart07.png|400]]

Then, it adds `10` to `%rax`.
![[chart08.png|400]]

We now hit a `ret` return, which means we go back to the `_start` code right after we called `add10`. In this case, the next instruction adds `5` to `%rax`.
![[chart09.png|400]]

Then, we call `syscall_exit`, a helper function to exit the program in Linux.

### Jumping
Jumping moves the [[3_Processor#Instruction Cycle|instruction pointer]] to the label that we are jumping to. When using `jmp`, execution continues happening at the new address, and will *not* come back to the caller code, unlike `call`.

We can make a simple infinite loop like follows:
```nasm
setup:
	mov $0, %rcx
loop:
	add $1, %rcx
	jmp loop
```

Here, we put `0` into `%rcx` during setup. When we get to `loop`, we add `1` to `%rcx`, then **jump** back to the beginning of the `loop` label, adding `1` more. It will keep doing this forever.

### Comparing
To fully make control flow structures that we have in C, such as `if` `else` `while` `for`, we need a way to compare 2 values.

We can use `cmp` to make conditional jumps, aka. **only jump** if condition is true.

For example, we can make a max function as follows:
```nasm
max:
	cmp %rsi, %rdi
	jl rdi_is_less
	mov %rdi, %rax
	ret
rdi_is_less:
	mov %rsi, %rax
	ret
```

Here, in the `max` label, `cmp` compares the values of `%rdi` to `%rsi`.

> [!warning] Note
> `cmp` compares **backwards** (destination to source). If we want to check if `%rdi` is less than `%rsi`, we need to put `%rsi` first, then `%rdi`.

`jl` means "*jump if less than*", meaning that if `%rdi` is less than `%rsi`, we jump to the label `rdi_is_less`. Otherwise, continue execution.

If we continue execution, we put the value of `%rdi` into the return `%rax`, then return.

If we jump to `rdi_is_less`, we put the value of `%rsi` into the return `%rax`, then return.

Apart from `jl`, these are some other possible jumps:

| Instruction | Jump if          | Condition | Value    |
| ----------- | ---------------- | --------- | -------- |
| `ja`        | above            | $x>y$     | unsigned |
| `jae`       | above or equal   | $x\geq y$ | unsigned |
| `jb`        | below            | $x<y$     | unsigned |
| `jbe`       | below or equal   | $x\leq y$ | unsigned |
| `jg`        | greater          | $x>y$     | signed   |
| `jge`       | greater or equal | $x\geq y$ | signed   |
| `jl`        | less             | $x<y$     | signed   |
| `jle`       | less or equal    | $x\leq y$ | signed   |
| `je`        | equal            | $x=y$     |          |
| `jne`       | not equal        | $x\neq y$ |          |

Using these tools, we can make any control flow logic that is possible in C. For example, to make a loop, we can use a conditional jump to `jmp` to the top of the current label.

### Testing
We can also test 1 value if it is positive, negative, or zero using `test x, x`.

For example, we can make an "is zero" function as follows:
```nasm
is_zero:
	test %rdi, %rdi
	jne non_zero
	mov $1, %rax
	ret
non_zero:
	mov $0, %rax
	ret
```

Here, in the `is_zero` label, `test` checks if `%rdi` is zero.

`jne` means "*jump if not equal*" or in this case, "*jump if not zero*", meaning that if `%rdi` is not zero, we jump to the label `non_zero`. Otherwise, continue execution.

If we continue execution, we return 1 to signify `TRUE` for is_zero.
If we jump to `non_zero`, we return 0 to signify `FALSE` for is_zero.

The conditional jumps are the same as above, but using `test`, the new meaning is as follows:

| Instruction | Jump if          | Condition | Value  |
| ----------- | ---------------- | --------- | ------ |
| `jg`        | positive         | $x>0$     | signed |
| `jge`       | positive or zero | $x\geq 0$ | signed |
| `jl`        | negative         | $x<0$     | signed |
| `jle`       | negative or zero | $x\leq 0$ | signed |
| `je`        | zero             | $x=0$     |        |
| `jne`       | not zero         | $x\neq 0$ |        |

### Status flags
When we do a "jump if greter than", `cmp` and `jg` are in two different instructions. The `cmp` or `test` sets a 1-bit **status flag** (*EFLAGS register*) to store the result of the comparison.

The way `cmp` works is by **subtracting** the two results, and store the sign in EFLAGS.
- `sub %rdi, %rax` subtracts the two, sets EFLAGS, and puts the result in `%rax`
- `cmp %rdi, %rax` subtracts the two, sets EFLAGS, and do nothing

Some examples of status flags include the **zero flag**, **carry flag**, **sign flag**, and **overflow flag**.

The **zero flag** (*ZF*) is set to `1` when the two arguments are **equal** (then subtraction would be 0).

The **carry flag** (*CF*) is set to `1` when the last arithmetic operation is carried/borrowed forward, like in addition. We can use `jc` for *jump if carry* or `jnc` for *jump if no carry*.

The **sign flag** (*SF*) is set to `1` when the last result was **negative** for signed integers. We can use `js` for *jump if sign (negative)* or `jns` for *jump if no sign* (positive).

The **overflow flag** (*OF*) is set to `1` when the last result had **signed overflow**. We can use `jo` for *jump if overflow* or `jno` for *jump if no overflow*.

| Instruction | Jump if             | Condition     |
| ----------- | ------------------- | ------------- |
| `jc`        | carried forward     | $\text{CF}=1$ |
| `jnc`       | not carried forward | $\text{CF}=0$ |
| `js`        | sign (negative)     | $\text{SF}=1$ |
| `jns`       | no sign (positive)  | $\text{SF}=0$ |
| `jo`        | overflow            | $\text{OF}=1$ |
| `jno`       | no overflow         | $\text{OF}=0$ |

