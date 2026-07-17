Lectures 11-12

## Branch Hazards
When the instruction includes a [[4_Conditions#Comparing|conditional branch]], for example:

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

As the processor puts the next instructions into the [[1_Data Hazards#Data Pipeline|pipeline]], when it reaches `jl` (jump if less than), it **doesn't know which** instruction to put next until the comparison is finished. This is a **branch hazard**.

For the execution to be correct, it will have to [[1_Data Hazards#Data Hazards|stall]] like data would.

### Branch Predictor
Modern processors will **make a prediction** on which branch will be executed next, and put those instructions into the pipeline, **speculatively**.

Predictions are based on **past behaviour** at that branch. A conditional branch with **consistent** behaviour will be well predicted, but one with random behaviour will not be predicted as well. A [[1_C and Assembly#Running a C code|Haswell]] CPU can predict repetitive patterns of jumps of at least **29 branches**.

If the processor guesses correctly, then there is no penalty for the branch.

If it guesses wrong, it is a **branch misprediction**. The instructions that were put in the pipeline must be discarded, and the correct instructions must be started.

![[Screenshot 2026-07-16 at 11.22.33 PM.png|400]]

Mispredictions are generally worse than a stall. They are more likely to affect running time of real code.

### Avoiding branches: cmov
If we want to reduce branch mispredictions, we have to make branches consistent. However, the **most reliable** way to avoid branch mispredictions, is to **not have branches**.

Some problems, like checking whether a number is **odd or even**, can be done using [[3_Bit Masking#Bit mask|bit manipulation]], removing the need for branches.

Not every problem has a bit manipulation solution, though. We can still use **conditional moves** (`cmov`) to reduce branches. `cmov` does a move operation, like `mov`, **only if** the [[4_Conditions#Comparing|flag condition]] is true.

The checking conditions are the same as for the conditional branches:

| Instruction | Move if          | Condition | Value    |
| ----------- | ---------------- | --------- | -------- |
| `cmova`     | above            | $x>y$     | unsigned |
| `cmovae`    | above or equal   | $x\geq y$ | unsigned |
| `cmovb`     | below            | $x<y$     | unsigned |
| `cmovbe`    | below or equal   | $x\leq y$ | unsigned |
| `cmovg`     | greater          | $x>y$     | signed   |
| `cmovge`    | greater or equal | $x\geq y$ | signed   |
| `cmovl`     | less             | $x<y$     | signed   |
| `cmovle`    | less or equal    | $x\leq y$ | signed   |
| `cmove`     | equal            | $x=y$     |          |
| `cmovne`    | not equal        | $x\neq y$ |          |

For example, this assembly code:
```nasm
cmp %rsi, %rdi
cmovne %r10, %r11
```

is roughly equivalent to this C code:
```c
if (rdi != rsi) { r11 = r10; }
```


> [!tip] The compiler is a better assembly programmer than us.
> For general programming, the C compiler **might** be able to automatically convert an `if`/`else` into a conditional move or better implementation, depending on the **complexity** of the code, and the **compiler**.

