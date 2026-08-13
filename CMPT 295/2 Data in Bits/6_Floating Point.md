Lectures 13-15

## IEEE Floating Point
Like [[1_Integers|integers]], we can also represent decimal values in binary. In base 10, after the decimal point, the value is gets smaller by a factor of 10:
$$
5.25_{10}=(5\times 10^{0})+(2\times 10^{-1})+(5\times 10^{-2})
$$

The same thing goes with base 2. The first position after the decimal point is $\times 2^{-1}$, then $\times 2^{-2}$, $\dots$. 
$$
\begin{align}
5.25_{10}=101.01_{2} & = (1\times 2^{2})+(1\times 2^{0})+(1\times 2^{-2}) \\
 & =4+1+0.25 \\
 & =5.25_{10}
\end{align}
$$

Not every value has an exact representation in binary, such as $0.1_{10}$, which is repeating in binary $0.0 \overline{0011}_{2}$.

To use bits to represent decimals, there is a standard **IEEE 754** for floating point values. We can decide to use 32 or 64 bits to represent. There are 3 parts in the representation:
- **Sign** ($s$): `0` for positive, `1` for negative
- **Exponent** ($E$), is an unsigned integer
- **Mantissa** ($M$), or *significand*, is a decimal value between $0$ - $2$

The number this represents is:
$$
\boxed{ x = (-1)^{s}\cdot M \cdot 2^{E} }
$$
where $E$ is the largest power of $2$ less than or equal to $x$, then
$$
\boxed{ M=\dfrac{x}{(-1)^{s}\cdot2^{E}}}
$$

For example, to represent $5.25$:
Since $5.25$ is positive, then $s=0$

The highest power of $2$ less than or equal to $5.25$ is $4=2^{2}$ $\implies E=2$

Now, we use the above formula to find $M$:
$$
M=\dfrac{5.25}{1\cdot 2^{2}}=1.3125
$$

Under this standard, we have:
$$
\begin{align}
s=0 &  & E=2 &  & M=1.3125
\end{align}
$$
The process of turning this into binary is below.

### Bits for E and M
- 32-bit (*single precision*, `float`) uses 1 bit for $s$, 8 for $exp$, and 23 for $frac$.
- 64-bit (*double precision*, `double`) uses 1 bit for $s$, 11 for $exp$, and 52 for $frac$.

![[Screenshot 2026-08-13 at 1.07.24 AM.png|500]]

These numbers are balanced between **precision** and **range**
- More bits for $exp$ mean larger range, and more precision around zero
- More bits for $frac$ mean more precision overall

Other standards exist such as *bfloat16* and *Half precision*, which have specific use cases, such as machine learning which prioritizes range over precision.

The range for 32-bit is $\pm 3.40\times 10^{38}$.
The range for 64-bit is $\pm 1.80 \times 10^{308}$.

### Calculating exp
In IEEE 754, $exp$ is calculated as:
$$
exp=E+bias
$$
$exp$ is the 8- or 11-bit unsigned integer in the binary, and the bias is either:
- 127 for 32-bit
- 1,023 for 64-bit

In our $5.25$ case earlier, if we are using 32-bit, the $E$ is $2$, therefore $2=exp-127\implies exp=129$

$129$ in 8-bit binary is $exp=10000001_{2}$

### Calculating frac
In IEEE 754, $frac$ is the decimal part of $M$ (ignore the whole number). If we want to turn $frac$ back into $M$, **add 1**.

In our $5.25$ case earlier, the $M$ is $1.3125$, and:
$$
\begin{align}
1.3125 & =(1\times 2^{0})+(1\times 2^{-2})+(1\times 2^{-4}) \\
 & =1.0101_{2}
\end{align}
$$
Ignoring the whole number part, we get $0101_{2}$ as our $frac$.

Since $frac$ must be 23- or 52- bit, we need to pad 0 at the back. In this case:
$$
frac=01010000000000000000000_{2}
$$

By putting $sign$, $exp$, and $frac$ together, we have our IEEE 754 representation of $5.25$:
$$
01000000101010000000000000000000_{2}
$$

### Denormalized value
This is a special case for IEEE 754 floating point, when the $exp$ is all $0$s. This means that $E$ is always $E=1-bias$, and $M$ is the $frac$ as decimal value but **without adding 1**.

This is to handle **very small numbers** close to $0$.

For example, this is a denormalized value:
$$
00000000001001011000000000000000_{2}
$$
This is approximately:
$$
\begin{align}
(-1)^{s}\cdot M \cdot 2^{E} & = (-1)^{0}\cdot 0.29296875\cdot 2^{-126} \\
 & \approx3.4438311\times 10^{-39}
\end{align}
$$

### Not a number
This is another special case for IEEE 754 floating point, when the $exp$ is all $1$s.
- If the $frac=0$ and $sign=0$, this means $+\infty$
- If the $frac=0$ and $sign=1$, this means $-\infty$
- If the $frac \neq 0$, this is ***not a number*** or ***NaN***. This is used to represent math errors like $\sqrt{ -1 }$ or $\frac{1}{0}$.

### Floating point errors
Floating point values are **approximation** for real numbers, but aren't exactly real numbers $\mathbb{R}$. Firstly, they are not associative:
$$
(a+b)+c \neq a+(b+c)
$$
This is due to a different **accumulation of error** between different order of operations. This is why [[6_Compiler Optimization#Auto-vectorization|auto-vectorization]] doesn't work well on floating point values.

Secondly, some numbers that are difficult to represent in floating point, such as $0.10$ that we found to be repeating in binary, this might be true in the program:
$$
\$0.20+\$0.10\neq \$0.30
$$
For money calculations, it is recommended that dollar values are **converted into cents** (or the smallest unit of the currency), treat them as integers, and convert them into dollars as they are displayed.
$$
\textcent 20+\textcent 10=\textcent 30
$$

Thirdly, there are two valid values of zero: $+0.0$ and $-0.0$, which `==` will return as `false`.

Comparing floating point values for equality is **almost never the right thing** to do.


---
## x86 Floating Point
The two-commonly used types of floating point: 
- 32-bit `float` single precision (~8 decimal digits)
- 64-bit `double` double precision (~15 decimal digits)

### x87 instructions
In [[2_Registers#Writing assembly|x86-64 CPUs]], there are two sets of registers and instructions that deal with floating points. The x87 instructions were legacy, used registers `ST0` to `ST7` as a stack, and used instructions like `fdiv`.

The x87 instruction set is not a part of this course.

### Floating point registers
The floating point instructions utilize the [[5_SIMD#SIMD registers|vector]] registers. The 128-bit version of these registers start with `%xmm(n)`, from `%xmm0` to `%xmm15`. None of these registers are [[2_Registers#Call Preservation|call-preserved]].

### Floating point calling convention
In integer [[2_Registers#Calling Convention|calling convention]], the **arguments** are placed in `%rdi`, `%rsi`, ..., and the **return** value must be put in `%rax`.

In floating point, the **arguments** are placed in `%xmm0`, `%xmm1`, ..., `%xmm8`. The **return** value must be put in `%xmm0`.

If the arguments are mixed between integers and floating point, `%rdi` is the **first integer** argument, and `%xmm0` is the **first floating point** argument.

```c
uint64_t f(uint64_t a, uint64_t b, double x, double y);
```

For this function, `a` is in `%rdi`, `b` is in `%rsi`, `x` is in `%xmm0`, and `y` is in `%xmm1`.

### Floating point instructions
Instructions for floating point includes `s` for "*scalar*" (not [[5_SIMD#SIMD instructions|vector]]), and `s` for single precision or `d` for double precision.

| Instruction       | Meaning                  |
| ----------------- | ------------------------ |
| `addsd` / `addss` | Add double / single      |
| `subsd` / `subss` | Subtract double / single |
| `mulsd` / `mulss` | Multiply double / single |
| `divsd` / `divss` | Divide double / single   |
These instructions work exactly like the [[1_Integers#Multiplication and Division|integer instructions]].

For **comparing**, use `comisd` (*compare scalar double*). This sets the [[4_Conditions#Status flags|status flag]] the exact same way as [[4_Conditions#Comparing|integer comparison]]. We can also use [[2_Branch Hazards#Avoiding branches cmov|conditional moves]].

**Moving** is slightly more complicated. We cannot "move" a constant immediate value like `3.14` into an `%xmm(n)` register. These are the workarounds:

1. If we want to set a register to `0`, consider using `pxor` instead. XORing the same register will turn it to zero. This will set `%xmm0` to `0.0`:
```nasm
pxor %xmm0, %xmm0
```

2. Since `movabs` [[6_Operand Size#Immediate values|allows]] us to move a 64-bit immediate value into a register, we can move a binary representation of the floating point into a register like `%rdi`, then use `movq` to move it to an `%xmm(n)`. For example, this moves the approximation of $\pi$ to `%xmm1`:
```nasm
movabs $0x400921fb54442d18, %rdi
movq %rdi, %xmm1
```

3. We can set the binary representation of the floating point in the [[2_Memory in Assembly#Static memory in assembly|static memory]], then reference it in the `movq`. For example, this moves the approximation of $\pi$ to `%xmm1`:
```nasm
.data
pi:
	.quad 0x400921fb54442d18
```

```nasm
movq pi(%rip), %xmm1
```

