Lectures 4-6

## Unsigned Counting
In **base 10** that we use, each **digit** can be one of 10 values (0-9). Each position increases the value by a factor of 10.
$$
345_{10}=(3\times 10^{2})+(4\times 10^{1})+(5\times 10^{0})
$$

If we have a 4-digit base 10 number, the smallest number representable is $0$, and the largest number is $9999_{10}$, which is $10^{4}-1$.

> [!tip] Note
> The subscript represents the **base** of the number. For example, $1110_{2}$ (1110 in base 2) is equal to $14_{10}$ (14 in base 10).

Computers, however, count in **base 2** or binary. Each digit can be one of 2 values (0, 1).
$$
\begin{align}
1001_{2} & =(1\times 2^{3})+(0\times 2^{2})+(0\times 2^{1})+(1\times 2^{0}) \\
 & =8+1 \\
 & =9_{10}
\end{align}
$$

If we have a 4-digit base 2 number, the smallest number representable is also $0$, and the largest number is $1111_{2}$, which is $2^{4}-1=15_{10}$.

Just like in decimal, leading zeros don't change anything. All of these mean $15_{10}$:
$$
\begin{align}
1111_{2} &  & 00001111_{2} &  & 000000001111_{2}
\end{align}
$$

### Unsigned addition
If we have two binary represented numbers, we can do **arithmetic** on them. 

In base 10, when we add numbers, we add them column by column. If there is an overflow, the $1$ is **carried over** to the next digit.

![[chart12.png|500]]

In base 2, the same thing is done. The $1$ can be **carried over** (set by [[4_Conditions#Status flags|status flag]] `CF`) to the next digit. Note that $1_{2}+0_{2}=1_{2}$ and $1_{2}+1_{2}=10_{2}$.

![[chart13.png|500]]

### Unsigned overflow
If we have a 4-digit base 2 number, the maximum number that we can represent is $15$. If we try doing $15+1$, we get:

![[chart16.png|200]]

In arithmetic like this, if the result is longer than the inputs, the **last carry** (leading $1$) is **discarded** making $1111_{2}+0001_{2}=0000_{2}=0$, which is incorrect.

There was an **unsigned overflow**. We've exceeded the range of values representable with the number of digits. 

The [[4_Conditions#Status flags|status flag]] `CF` is set when there is an unsigned overflow. We can use `jc` and `jnc` to detect this flag.


---
## Signed Counting
To represent **negative numbers** in binary, we could simply set the first bit to `0` for positive, and `1` for negative. One problem that this introduces is that we will have $+0$ and $-0$ as separate numbers.

Instead, we can use **two's complement**. Positive numbers start with `0`, and are the same as [[#Unsigned Counting|unsigned]]. Negative numbers start with `1`, and follows the following algorithm:

To negate any number:
1. Start with binary representation (e.g. $21_{10}=00010101_{2}$)
2. **Flip** all the bits (e.g. $00010101 \implies 11101010$)
3. **Add 1** to the number (e.g. $11101010 +1=11101011$)

Therefore, $-21_{10}=11101011_{2}$ in two's complement.

If we have a 4-digit base 2 number, the smallest number representable is $-2^{4-1}=-8$, and the largest number is $2^{4-1}-1=7$.

### Sign extending
For negative numbers, we can add leading $1$s to extend the bits. This is called **sign extending**. All of these mean $-21_{10}$:
$$
\begin{align}
11101011_{2} &  & 111111101011_{2} &  & 1111111111101011_{2}
\end{align}
$$

Note that if $11101011_{2}$ was an **unsigned**, it would be $235_{10}$ instead of $-21_{10}$. If we want to extend it to 12 bits:
- Number is unsigned: $000011101011_{2}$
- Number is signed: $111111101011_{2}$

If we ask assembly to move a value from a smaller [[2_Registers#Calling Convention|register]] like `%ax` to a larger one like `%rax`, it **does not know** if it should pad $0$s or $1$s.
- `movsx` means *move with sign extension*, will pad $0$s if positive, and $1$s if negative.
- `movzx` means *move with zero-extend*, will pad $0$s.

### Signed addition
In two's complement addition, we use the [[#Unsigned addition|same algorithm]] as unsigned. If there is a **last carry** (the leftmost carry making the result longer), we will **discard that carry**.

![[chart14.png|500]]

In this case, $110_{2}+011_{2}=001_{2}$ since we discard the leading $1$ at the end. In base 10, this is $-2+3=1$.

Since all additions are the same for both unsigned and signed, there is only **one instruction** `add` to add integers.

> [!tip] Subtraction
> Subtraction is done using addition, since $A-B=A+(-B)$. We just need to negate $B$. Subtraction is also done through **one instruction** `sub`.

### Signed overflow
For a 4-digit signed integer, we can represent values from $-8$ to $7$. If we try doing $7+1$, we get:

![[chart15.png|200]]

$0111_{2}+0001_{2}=1000_{2}=-8_{10}$, which is not right. $7+1$ is not $-8$.

There was a **signed overflow**. We've exceeded the range of values representable with the number of digits. 

To detect this overflow:
- If the two inputs have the **same sign**, but the result is a **different sign**, then there is an overflow.
- If the two inputs have **different signs**, there can never be an overflow.

The [[4_Conditions#Status flags|status flag]] `OF` is set when there is a signed overflow. We can use `jo` and `jno` to detect this flag.


---
## Hexadecimal
Apart from base 2, using **base 16** is also useful in computing. There can be 16 possible values in one position:
```
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

This is convenient since we can represent **4 bits** with **1 letter**:

| Base 2 | Base 10 | Base 16    |
| ------ | ------- | ---------- |
| $0000$ | $0$     | $0$        |
| $1001$ | $9$     | $9$        |
| $1100$ | $12$    | $\text{C}$ |
| $1111$ | $15$    | $\text{F}$ |

$16$ is a multiple of $2$, so hexadecimals are still nicely related to binary, and easier to look at.
$$
\begin{align}
12345678_{10} & = 1011\,1100\,0110\,0001\,0100\,1110_{2} \\
 & =\text{B C 6 1 4 E}_{16}
\end{align}
$$

In code, we can give values in base 10, or hexadecimals with `0x` prefix, or binary with `0b` prefix:
```python
a = 28
b = 0x1c
c = 0b11100
```

```nasm
mov $28, %rax
mov $0x1c, %rbx
mov $0b11100, %rcx
```


---
## Multiplication and Division

### Multiplication
For unsigned integers, the `mul` instruction:
- takes a **register operand** (`mul a`)
- multiplies that by `%rax`
- puts the result in `%rdx:%rax` (128-bit result)

For signed integers, the `imul` instruction can do the same with a single operand, or:
- if given **two operands** (`imul a, b`)
- multiplies and puts result in the second operand `b *= a`

Both `mul` and `imul` set [[4_Conditions#Status flags|status flags]] `OF` and `CF` if there is an overflow (doesn't fit in one register).

### Division
For unsigned integers, use the `div` instruction. For signed integers, use the `idiv` instruction. They do the same thing:
- takes a **register operand** (`div a`, `idiv a`)
- divides `%rdx:%rax` by the operand (`%rdx:%rax / a`)
- puts the result in `%rax`
- puts the remainder in `%rdx`


---
## Application

### RGB Colours
We can represent colours using **RGB**, the brightness values of red, green, blue. An 8-bit integer is used for each value (can be up to $2^{8}-1=255$), resulting in a colour taking up 24 bits.

Since each value is 8-bit, we can use **2 hexadecimals** to represent it as well:
$$
255_{10}=1111\,1111_{2}=\text{FF}_{16}
$$

We can form a **hex code** string of **6 hexadecimals**, 2 for each value:
```
[2 digits of red][2 digits of green][2 digits of blue]
```

For example, the colour **plain white** is max brightness ($255$) for all 3 values in RGB, therefore, plain white is $\#\text{FFFFFF}$ in hex code.

### Time
We can use the **Unix epoch** standard to represent time **with a single integer**. The value is the **number of seconds** after *January 1, 1970 at 00:00:00 UTC*.

For example, *June 15, 2026 at 16:30:00 PDT* is `1781566200` in Unix epoch.