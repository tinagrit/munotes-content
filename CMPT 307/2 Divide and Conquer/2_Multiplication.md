Lecture 7

## Recursion in Multiplication
- **Problem**: Multiplying $x$ and $y$
- **Constraint**: $x$ and $y$ are $n$-bit numbers. For convenience, assume that $n$ is a power of 2.

To partition the problem, we can **split** each $x$ and $y$ into 2 halves. For example, if $x=10110110_{2}$, then we can split $x$ into $x_{L}$ (left) and $x_{R}$ (right):
$$
\begin{align}
x_{L}=1011 &  & x_{R}=0110
\end{align}
$$

These are equivalent to:
$$
x=\boxed{ x_{L} }\boxed{ x_{R} }=x_{L}\cdot 2^{n/2}+x_{R} 
$$
since $x_{L}$ can be **left-shifted** by $n/2$ bits (in the example $n=8$ then shift left 4 bits).

Using this representation, then:
$$
\begin{align}
xy &= \left( x_{L}\cdot 2^{n/2}+x_{R} \right)\left( y_{L}\cdot 2^{n/2}+y_{R} \right)   \\
 & =x_{L}y_{L}\cdot2^{n}+\left( x_{L}y_{R}+x_{R}y_{L} \right)\cdot 2^{n/2}+x_{R}y_{R} 
\end{align}
$$

> [!tip] Multiplication in linear time
> In this equation, multiplying a number by a power of 2, such as $2^{n}$, can be done in linear time, since it is left shifting a number by $n$ bits.

Using this partition, from 1 multiplication $xy$, we have 4 subproblems ($x_{L}y_{L}$, $x_{L}y_{R}$, $x_{R}y_{L}$, $x_{R}y_{R}$), each with half the digit length.

This leads to the recurrence relation:
$$
T(n)=4T\left(\frac{n}{2}\right)+O(n) \implies \boxed{ T(n)=O(n^{2}) }
$$

This is however, **not better** than the naive multiplication algorithm, which is also $O(n^{2})$.

### Using Gauss
*Carl Friedrich Gauss* found that only 3 multiplications are needed instead of 4 in each recurrence.

In the equation we derived earlier:
$$
\begin{align}
xy &= x_{L}y_{L}\cdot2^{n}+\boxed{ \left( x_{L}y_{R}+x_{R}y_{L} \right) }\cdot 2^{n/2}+x_{R}y_{R} 
\end{align}
$$

This term is equal to:
$$
x_{L}y_{R}+x_{R}y_{L}=(x_{L}+x_{R})(y_{L}+y_{R})-x_{L}y_{L}-x_{R}y_{R}
$$

Notice that we already have $x_{L}y_{L}$ and $x_{R}y_{R}$ from the other terms in the equation.

Therefore, from 4 multiplications, we only need these 3:
$$
\begin{align}
x_{L}y_{L} &  & (x_{L}+x_{R})(y_{L}+y_{R}) &  & x_{R}y_{R}
\end{align}
$$

This leads to the [[3_Master Theorem#Master Theorem for Recurrence Relations|recurrence relation]]:
$$
T(n)=3T\left( \dfrac{n}{2} \right)+O(n) \implies \boxed{ T(n)=O(n^{\log_{2}3}) }
$$

