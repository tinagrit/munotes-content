Lecture 10

> [!tip] Aside
> This note is not about memory, but about how the Intel syntax is different than the AT&T syntax that we've been doing.

## Intel syntax
The [[2_Registers#Writing assembly|x86-64 assembly]] has **2 distinct syntaxes**, AT&T and Intel. We've been using the AT&T syntax, but the Intel syntax is more common.

They are different syntaxes of the **same architecture**. These will be translated to the same [[1_C and Assembly#Assembling|machine code]].

### Basic Instructions
To translate from AT&T to Intel, 
- **remove the** `%` from registers
- **remove the** `$` from literals
- **switch operand order** from (source, destination) to (destination, source)

Therefore, if this is our AT&T syntax:
```nasm
mov %rdi, %rax
add $7, %rax
```

This is the equivalent Intel syntax:
```nasm
mov rax, rdi
add rax, 7
```

### Addressing memory
To [[2_Memory in Assembly#Static memory in assembly|address memory]] in the Intel syntax, use the square bracket `[]` with arithmetic-looking expression:

If this is the AT&T syntax:
```nasm
4(%rbx, %rcx, 8)
```

This is the equivalent Intel syntax:
```nasm
[rbx + rcx*8 + 4]
```

The Intel syntax way of writing is **not arbitrary arithmetic** expression, it is a fixed pattern.

