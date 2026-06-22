Lectures 7 & 8

> [!failure] This note is incomplete.

## Bit mask

### Odd and even
When we test for even/odd integers in C, this is how it is usually done:
```c
if (n % 2 == 0) {
	printf("even");
} else {
	printf("odd");
}
```

If we want, we can implement this in assembly using [[1_Integers#Division|idiv]], this computes `rdx = rdi % 2`:
```asm
mov $2, %r8
mov $0, %rdx
mov %rdi, %rax
idiv %r8
```

One problem is that doing division is **very expensive**, and we don't need to do that. 

In binary, if the right-most bit is `1`, it is **odd**, if it is `0`, it is **even**. For example:
- $6_{10}=0110_{2}$ ends with $0$, and therefore even
- $7_{10}=0111_{2}$ ends with $1$, and therefore odd

The `and` instruction does **bit-wise AND** bit-by-bit, doing: 
- `1 & 1 = 1`
- `1 & 0 = 0`
- `0 & 1 = 0`
- `0 & 0 = 0`

The number $1_{10}$ is $0001_{2}$, only having `1` in the right-most bit. Therefore, if we **AND** this with anything, we can find out if the right-most bit is 0 or 1.

![[chart17.png|350]]

In assembly, we can do:
```asm
mov %rdi, %rdx
and $1, %rdx
```
and will return `1` for odd, and `0` for even. This is about **10 times faster** than the `idiv` solution.

### Check any bit
In this case, we check the right-most bit to see if the number is odd or even. Turns out, we can use the same method to **check any digit**. 

For example, to examine bits 2 and 3, we can **AND** with $0110_{2}$:

![[chart18.png|200]]

This process is called **bit masking**. Computers are very fast at bit manipulation, if we can phrase our problem as one.

This does **not** mean that we should change our C code. One of the compiler's job is to **optimize the code**. We should write readable code, and let the compiler optimize.

