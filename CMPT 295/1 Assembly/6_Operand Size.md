Lecture 4

## Operand Size
In assembly, we an do operands on 64-, 32-, 16-, or 8-bit operands. Smaller operands might be **faster**, and take **less memory**.

Using the [[2_Registers#Calling Convention|Calling Convention]], usually the size is **automatically inferred** from the size of the register. For example,
```nasm
add $1, %rax    # 64-bit
add $1, %eax    # 32-bit
add $1, $ax     # 16-bit
add $1, %al     # 8-bit
```

Recall that:
![[chart02.png|450]]

### Ambiguous case
When it is **ambiguous** and the assembler can't infer the size, we may need to **be specific**. Otherwise, we don't need to.

For example,
```nasm
mov $1, (%rsp)
```

The assembler doesn't know how many bytes around `%rsp` to write. In this case, we add **one letter to the end** of the instruction to specify size.

| Instruction | Meaning   | Size   | Assembler literal |
| ----------- | --------- | ------ | ----------------- |
| `movb`      | byte      | 8-bit  | `.byte`           |
| `movw`      | word      | 16-bit | `.word`           |
| `movl`      | long word | 32-bit | `.long`           |
| `movq`      | quad word | 64-bit | `.quad`           |

### Immediate values
The constants in the assembly code, like `$1` for 1, can only be **up to 32-bit values**.

Although the following `addq` is a 64-bit add, the constant cannot be larger than $2^{32}-1$:
```nasm
addq $1234, %rax
```

This will fail with "*operand type mismatch*" since the argument is $2^{60}$:
```nasm
addq $1152921504606846976, %rax
```

This is due to the **64-bit** [[3_Processor#Instructions|instruction register]] not being to store 64-bit constants **in the instruction**.

The exception is `movabs` that can move 64-bit value into a register:
```nasm
movabs $1152921504606846976, %rcx
```

