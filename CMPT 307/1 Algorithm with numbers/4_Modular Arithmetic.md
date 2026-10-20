Lectures 3-5

## Modular Arithmetic
Modular Arithmetic is a system for dealing with **restricted range** of integers. It has the notation:
$$
X \bmod{N}
$$
which means the **remainder** when $X$ is divided by $N$.

For example,
$$
17\bmod 4 = 1
$$
since $\frac{17}{4}=4$  with remainder $1$.

$$
21\bmod 4 = 1
$$
since $\frac{21}{4}=5$  with remainder $1$.

Since $17$ and $21$ have **the same remainder** after being divided by $4$, we can say they are **congruent** modulo 4.
$$
17 \equiv 21 \bmod 4
$$

### Laws for Modular Arithmetic
- **Substitution rule**: if $x \equiv x' \pmod{N}$ and $y \equiv y' \pmod{N}$, then:
$$
\begin{align}
x+y\equiv x'+y'  \pmod{N} &&\text{and} &  &  xy\equiv x'y' \pmod{N}
\end{align}
$$
- **Associativity**: $x+(y+z)\equiv (x+y)+z  \pmod{N}$
- **Commutativity**: $xy \equiv yx  \pmod{N}$
- **Distributivity**: $x(y+z)\equiv xy+yz \pmod{N}$

### Reduction
During a calculation, we can simplify large powers. For example, if we have:
$$
2^{345}\bmod 31
$$
We can do:
$$
2^{345}\equiv (2^{5})^{69}\equiv 32^{69}\pmod{31}
$$
Notice that $32$ and $1$ both have the same remainder after being divided by $31$. That is,
$$
32\equiv 1 \pmod{31}
$$
We can use this to reduce the power above:
$$
32^{69}\equiv 1^{69}\equiv 1 \pmod{31}
$$

### Addition
Calculating
$$
(x+y)\bmod N = (x\bmod N+y\bmod N)\bmod N
$$

Since both $x$ and $y$ are between $[0,N-1]$, their sum must be between $[0,2(N-1)]$.

If the sum exceeds $N-1$, subtract $N$ from the sum.

This algorithm has the running time $O(n)$ where $n=\lceil \log N \rceil$ (the size of $N$)

### Multiplication
Calculating:
$$
(x \times y)\bmod N = (x\bmod N)(y\bmod N)\bmod N
$$
There are two approaches. For example, if we want to calculate $(13 \times 9)\bmod 5$:

**Approach #1**: Multiply $x \times y$ first, then mod $N$
$$
(13\times 9)\bmod 5 = 117 \bmod 5 = \boxed{ 2 }
$$

**Approach #2**: Mod $N$ in $x$ and $y$, multiply, then mod $N$ again
$$
(13 \bmod 5)(9 \bmod 5)\bmod 5=(3\times 4)\bmod 5=12\bmod 5 =\boxed{ 2 }
$$

This algorithm relies on regular multiplication, and has the running time $O(n^{2})$.

### Division
Modular division is more complicated. When we do fractional arithmetic dividing, diving $a$ by $b\neq 0$ is the same as multiplying $a$ by $\frac{1}{b}$. This works because $\frac{1}{b}$ is the **multiplicative inverse** of $b$. 

For modular arithmetic, dividing $a$ by $b$ requires the **multiplicative inverse** of $b$.

$b^{-1}$ is the multiplicative inverse of $b$ modulo $N$ if:
$$
\boxed{ bb^{-1} \equiv 1\bmod N }
$$
There can be at most one such $b^{-1} \bmod N$. The inverse **does not always exist**. The inverse exists *if and only if*:
$$
\text{gcd}(b,N)=1
$$
If $\text{gcd}(b,N)>1$, no such inverse exists. This is called the **Modular Division Theorem**.

For example, finding $11^{-1}\bmod 25$, the inverse of $11\bmod 25$:
Use the [[5_Euclids Algorithm#Extension to Euclid's Algorithm|extended Euclid's algorithm]] to write the linear combination:
$$
1 =25(4) + 11(-9)
$$
[[#Reduction|Reducing]] both sides modulo $25$:
$$
\begin{align}
1\bmod 25 & =(25(4)+11(-9))\bmod 25 \\
1\bmod 25 & =11(-9)\bmod 25 \\
1\bmod 25 & =11(16)\bmod 25
\end{align}
$$
By congruency,
$$
11(16) \equiv 1\bmod 25
$$
and therefore $\boxed{ 16 }$ is the inverse of $11\bmod 25$.

Division can be done in running time $O(n^{3})$ by using the [[5_Euclids Algorithm#Extension to Euclid's Algorithm|extended Euclid's algorithm]].

### Exponentiation
We are trying to calculate
$$
x^{y}\bmod{N}
$$
For example,
$$
3^{4}\bmod 5 = 81\bmod 5 = \boxed{ 1 }
$$

We want an algorithm to calculate $x^{y}\bmod{N}$ where $x$, $y$, and $N$ can all be very large numbers.

To make sure that the numbers we deal with never grow too large, we need to keep reducing in the intermediate steps.

**Approach #1**: Repeatedly multiply by $x\bmod N$ then modulo $N$.
If we multiply $x\bmod N$ by itself, then $\bmod N$, we get $x^{2} \bmod N$. We can keep doing this $y$ times.
$$
x\bmod N \to x^{2}\bmod N \to x^{3}\bmod N\to \dots  \to x^{y}\bmod N
$$

Using the $3^{4}\bmod 5$ example above:
- Start with $3^{1}\bmod 5=3$
- Then $3^{2}\bmod 5=(3^{1}\bmod 5)(3\bmod 5)\bmod 5=(3)(3)\bmod 5=4$
- Then $3^{3}\bmod 5=(3^{2}\bmod 5)(3 \bmod 5)\bmod 5=(4)(3)\bmod 5=2$
- Then $3^{4}\bmod 5=(3^{3}\bmod 5)(3\bmod 5)\bmod 5=(2)(3)\bmod 5=\boxed{ 1 }$

The problem is that each step takes $O(\log^{2}N)$ time. For a 500-bit long $y$, this can take about $2^{500}$ multiplications.

**Approach #2**: Square repeatedly modulo $N$.
$$
x\bmod N \to x^{2}\bmod N \to x^{4}\bmod N\to \dots  \to x^{2^{\lfloor \log y \rfloor }}\bmod N
$$

Using the $3^{4}\bmod 5$ example above:
- Start with $3^{1}\bmod 5 = 3$
- Square the previous result $3^{2}\bmod 5=(3)^{2}\bmod 5=9\bmod 5=4$
- Square the previous result $3^{4}\bmod 5=(4)^{2}\bmod 5=16\bmod 5=\boxed{ 1 }$

While each step still takes $O(\log^{2}N)$ time, there are only $\log y$ multiplications.

To calculate $y$ that is not a perfect square, for example, $3^{25}\bmod 17$, by representing $25$ in binary we get:
$$
25=16+8+1
$$
This means that:
$$
3^{25}=3^{16}\cdot 3^{8}\cdot 3^{1}
$$
Now that these are perfect squares, we can use the fact that:
$$
3^{25}\bmod 17=(3^{16}\bmod 17)(3^{8}\bmod 17)(3^{1}\bmod 17)\bmod 17
$$
The three terms are easy to find using this approach.

The squaring can be done recursively as well. To get to $x^{y}$, we can do
$$
x^{y}=\begin{cases}
(x^{\lfloor y/2 \rfloor })^{2} & \text{if }y\text{ is even} \\
x \cdot (x^{\lfloor y/2 \rfloor })^{2} & \text{if }y\text{ is odd}
\end{cases}
$$
modulo $N$.

This algorithm has the running time $O(n^{3})$, since there are approximately $O(n)$ recursive calls, each call does an $O(n^2)$ multiplication.


