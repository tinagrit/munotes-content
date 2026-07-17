Lecture 8

## Bit shift
In base 10, if we have a number like $670$, we can:
- multiply it by $\times10$ by **adding a zero** at the end: $670\times 10 = 6700$
- divide it by $/10$ by **removing a zero** at the end: $670 / 10=67$

In binary, the same thing happens in base 2. If we have a number like $0110_{2}=6_{10}$, we can:
- multiply it by $\times 2$ by **adding a zero** at the end: $0110_{2} \times 2_{10}=01100_{2}$
- divide it by $/2$ by **removing a zero** at the end: $0110_{2}/2_{10}=011_{2}$

> [!tip] Note
> If there is a $1$ at the end, like $0111_{2}=7_{10}$, removing the one at the end will divide the number by $/2$ and **round down**.

While multiplying and dividing in binary, we need to preserve the **number of bits**. If we have:
- more bits than before, the **first bit** is omitted
- fewer bits than before, we need to [[1_Integers#Sign extending|sign extend]] to pad

Doing multiplication and division this way is **way faster** than using normal [[1_Integers#Multiplication and Division|integer operations]]. If we want to multiply/divide a number by a power of 2, like $2^{n}$, we can shift the number by $n$ digits.

Sometimes, doing **shifting+adding** is faster than **multiplying**. This is, however, unclear in modern processors:
$$
\begin{align}
(x \times 2^{5})+x &  & x \times 33
\end{align}
$$

### Bit shifting in assembly
In assembly, we can use these instructions to bit shift by $n$ digits:

| Instruction    | Action                                                  |
| -------------- | ------------------------------------------------------- |
| `shl $2, %rdi` | shift left                                              |
| `shr $2, %rdi` | shift right, zero extend                                |
| `sar $2, %rdi` | shift right, [[1_Integers#Sign extending\|sign extend]] |

For example, if we want to multiply a number by $\times 33$ using $(x \times 2^{5})+x$, we can do:
```nasm
mov %rdi, %rax
shl $5, %rax
add %rdi, %rax
```

