Lecture 10

## Matrix multiplication

Given two $n\times n$ matrices, $A_{n\times n}$ and $B_{n \times n}$, and $C= AB$.

Computing each entry in $C$ takes $O(n)$ time, and with $n^{2}$ entries (matrices size $n\times n$), computing takes $O(n\times n^{2})=\boxed{ O(n^{3}) }$.

There are some **algorithms** that **optimize** multiplying, such as $O(n^{2.373})$ by Alman-Williams, 2020. We believe that multiplication can be done in $\boxed{ O(n^{2+\epsilon}) }$ times where $\epsilon > 0$.

### Freivalds' Algorithm
This algorithm is used to **verify multiplication**.

If we are given $A,B,C$ and we need to verify if $C=AB$, multiplying $A\times B$ manually will take $O(n^{2+\epsilon})$ time to compute.

A [[2_Axioms#Probability Function|probabilistic]] algorithm like Freivalds' can verify in $O(n^{2})$ time.

1. Generate a random $n$-bit vector $x$, by making each bit either a 0 or 1 with $\frac{1}{2}$ probability, independently.
2. Compute $t=Bx$, then $y=At$, then $z=Cx$
3. Output ***YES*** if $y=z$, otherwise output ***NO***

### Example
$$\begin{align}
A=\begin{bmatrix}
0 & 1 \\ 1  & 0
\end{bmatrix}\text{ } & B=\begin{bmatrix}
1 & 0 \\ 1 & 1
\end{bmatrix} &  & C=\begin{bmatrix}
1 & 1 \\  1 & 0
\end{bmatrix}
\end{align}
$$

Generating a random 2-bit vector $x$, in this case $x=\begin{bmatrix}1\\0\end{bmatrix}$.

Computing $t$:
$$
t=Bx=\begin{bmatrix}
1 & 0\\1 & 1
\end{bmatrix}\begin{bmatrix}
1\\ 0
\end{bmatrix}=\begin{bmatrix}
1\\1
\end{bmatrix}
$$
Computing $y$:
$$y=At=
\begin{bmatrix}
0 & 1\\1 & 0
\end{bmatrix}\begin{bmatrix}
1\\1
\end{bmatrix}=\begin{bmatrix}
1\\1
\end{bmatrix}
$$
Computing $z$:
$$
z=Cx=\begin{bmatrix}
1 & 1 \\ 1 & 0
\end{bmatrix}\begin{bmatrix}
1 \\ 0
\end{bmatrix}=\begin{bmatrix}
1 \\ 1
\end{bmatrix}
$$

Since $y=z$, this algorithm outputs ***YES***.

### Probability Analysis
- If $C=AB$, the output ***YES*** is always accurate from the algorithm, since $C=AB \implies Cx=ABx$ for any vector $x$
- If $C \neq AB$, the output ***NO*** is **not always** accurate, but has the probability of outputting ***NO*** $\geq \frac{1}{2}$

| Probability | ***YES***        | ***NO***            |
| ----------- | ---------------- | ------------------- |
| $C=AB$      | $1$              | $0$                 |
| $C \neq AB$ | $< \dfrac{1}{2}$ | $\geq \dfrac{1}{2}$ |

Therefore, we can make Freivalds' algorithm more accurate by **running it repeatedly**, to reduce the chance of the false negative.

If we run the algorithm $m$ times, we get:

| Probability | ***YES***            | ***NO***                   |
| ----------- | -------------------- | -------------------------- |
| $C=AB$      | $1$                  | $0$                        |
| $C \neq AB$ | $< \dfrac{1}{2^{m}}$ | $\geq 1- \dfrac{1}{2^{m}}$ |

If $m=20$, the chance that Freivalds' produces a false negative is $\approx 10^{-6}$, which is very low.