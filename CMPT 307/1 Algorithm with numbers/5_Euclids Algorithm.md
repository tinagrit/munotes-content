Lectures 4-5

## Greatest Common Divisor
The **GCD** (*Greatest Common Divisor*) of $a$ and $b$, denoted $\text{gcd}(a,b)$, is the **largest integer** that divides both $a$ and $b$.

### Factoring
The GCD can be solved via factoring. The common factors between $a$ and $b$ are multiplied to get the GCD.

For example, finding $\text{gcd}(759,1035)$:
$$
\begin{align}
759 & =23\cdot 11\cdot 3 \\
1035 & =23\cdot 5\cdot 3\cdot 3
\end{align}
$$
Here, the common factors are $23$ and $3$. Therefore:
$$\text{gcd}(759,1035)=23\times 3=\boxed{ 69 }$$

The problem with this approach is that **factoring is hard**, and there is no efficient algorithm to factoring.

### Euclid's Algorithm
Mathematician Euclid of Ancient Greece uses [[4_Modular Arithmetic#Modular Arithmetic|modular arithmetic]] in the rule:

If $a$ and $b$ are positive integers with $a\geq b$, then:
$$
\text{gcd}(a,b)=\text{gcd}(b,a\bmod b)
$$

> [!tip] Simple proof
> Showing that:
> $$\text{gcd}(a,b)=\text{gcd}(a-b,b)$$
> 
> This proof is enough because $a\bmod b$ is essentially subtracting $b$ repeatedly from $a$ until we get the remainder.
> 
> Any integer that divides both $a$ and $b$ must also divide $a-b$, therefore $\text{gcd}(a,b)\leq \text{gcd}(a-b,b)$.
> Any integer that divides both $a-b$ and $b$ must also divide $a$, therefore $\text{gcd}(a,b)\geq \text{gcd}(a-b,b)$.
> 
> Therefore, $\text{gcd}(a,b)=\text{gcd}(a-b,b)$

The Euclid algorithm for finding the GCD can be written as:
```
function Euclid(a,b):
	if (b=0): return a
	return Euclid(b, a mod b)
```
where $a$, $b$ are positive integers with $a\geq b \geq 0$.

To perform this algorithm practically, for example, computing $\text{gcd}(25,11)$:
First we arrange
$$
\underline{a}=(\text{quotient})\underline{b}+\text{remainder}
$$
Divide 25 by 11:
$$
\underline{25}=(2)\underline{11}+3
$$

Now, from `Euclid(a,b)`, we do `Euclid(b, a mod b)`. In this case $b=11$ and $a\bmod b$ (the remainder) $=3$. We divide 11 by 3:
$$
\underline{11}=(3)\underline{3}+2
$$
Repeat:
$$
\underline{3}=(1)\underline{2}+1
$$
$$
\underline{2}=(2)\underline{1}+0
$$
When we get to $0$ on the remainder, we stop. The last remainder before it became $0$, in this case $\boxed{ 1 }$ is the $\text{gcd}(25,11)$.

For the running time of this recursive algorithm, for $n$ bit integers, the base case will be reached within $2n$ calls, each call using an $O(n^{2})$ division algorithm. The total running time is $\boxed{ O(n^{3}) }$.

### Extension to Euclid's Algorithm
The $\text{gcd}(a,b)$ is the **smallest positive integer** that can be written as a linear combination of $a$ and $b$. That is:
$$
d=ax+by
$$
for some integers $x$ and $y$. $d=\text{gcd}(a,b)$ is **minimal**.

We can extend the Euclid's algorithm to find the coefficients $x$ and $y$ of the linear combination.

For example, using the example above, $d=\text{gcd}(25,11)$. We want to find $x$ and $y$ such that:
$$
1=25x+11y
$$

Going back to the iterations that we computed:
$$
\begin{align}
\underline{25} & =(2)\underline{11}+3 & &  (1) \\
\underline{11} & =(3)\underline{3}+2 &  & (2) \\
\underline{3} & =(1)\underline{2}+1  &  & (3) \\
\underline{2} & =(2)\underline{1}+0 &  & (4)
\end{align}
$$

Starting from $(3)$ where we got the GCD from, arrange the GCD on the left:
$$
\begin{align}
(3) &  & 1=3-2
\end{align}
$$
Going up to $(2)$, arrange the remainder on the left:
$$
\begin{align}
(2) &  & 2=11-3(3)
\end{align}
$$
Back substitute this into $(3)$, we will refer to this as $(5)$:
$$
\begin{align}
(2)\to (3) &  & 1 & =3-(11-3\cdot3) \\
 &  & 1 & =4\cdot 3-11 &  (5)
\end{align}
$$
Going up to $(1)$, arrange the remainder on the left:
$$
\begin{align}
(1) &  & 3=25-2(11)
\end{align}
$$
Back substitute this into $(5)$:
$$
\begin{align}
(1)\to (5) &  & 1 & =4 \cdot (25-2\cdot 11)-11 \\
 &  & 1 & = 4\cdot 25-8\cdot 11-11 \\
 &  & 1 & =4\cdot 25 - 9\cdot 11
\end{align}
$$

Since we are looking for
$$
1=25x+11y
$$
The result shows that $x=4$ and $y=-9$.

