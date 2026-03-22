Lectures 10 & 11

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

| Probability | ***YES***           | ***NO***            |
| ----------- | ------------------- | ------------------- |
| $C=AB$      | $1$                 | $0$                 |
| $C \neq AB$ | $\leq \dfrac{1}{2}$ | $\geq \dfrac{1}{2}$ |

Therefore, we can make Freivalds' algorithm more accurate by **running it repeatedly**, to reduce the chance of the false negative.

If we run the algorithm $m$ times, we get:

| Probability | ***YES***               | ***NO***                   |
| ----------- | ----------------------- | -------------------------- |
| $C=AB$      | $1$                     | $0$                        |
| $C \neq AB$ | $\leq \dfrac{1}{2^{m}}$ | $\geq 1- \dfrac{1}{2^{m}}$ |

If $m=20$, the chance that Freivalds' produces a false negative is $\approx 10^{-6}$, which is very low.

### Geometric perspective
Verifying a matrix multiplication means verifying:
$$
C=AB
$$
, therefore, this is the same as verifying that the **difference is zero**.
$$
\begin{align}
D=C-AB
\end{align}
$$

The Freivalds' Algorithm verifies the above using a random vector $x$, and thereby verifying that:
$$
Dx=0
$$
Freivalds output ***YES*** when $x$ is in the **nullspace** of $D$. ($x \in \text{null}(D)$)

> [!tip] Nullspace
> The nullspace is a set of all input vectors that **make the output** $0$. In this case, is the list of all $x$'s that make $Dx=0$
> $$\text{null}(D) = \left\{ x \in \mathbb{R}^{n} \mid Dx=0 \right\} $$

When we generate random $x$ with $0$ and $1$, these are essentially coordinates for corners of a **hypercube** (analogue of a square and cube for $n$ dimensions).

For example, with $n=2$ (two dimensions), our $x$ can be one of:
$$
\begin{align}
\begin{bmatrix}
0\\0
\end{bmatrix} &  & \begin{bmatrix}
0\\1
\end{bmatrix}  &  & \begin{bmatrix}
1\\0
\end{bmatrix}  &  &  \begin{bmatrix}
1\\1
\end{bmatrix}
\end{align}
$$

If $C=AB$, then $D$ is a **zero matrix**, and the zero matrix always return $0$ for any input. Therefore, 
$$\text{null}(D)=\mathbb{R}^{n}$$
, and **100%** of matches fall in the null space. The algorithm would always return ***YES*** correctly.


If $C\neq AB$, then $D \neq 0$ and the **dimension** of $D$'s nullspace can be up to $n-1$ (worst case). 
$$
\text{dim}(\text{null}(D)) \leq n-1
$$
If the $x$ falls into the nullspace, then the algorithm would return a **false positive**, a ***YES*** when $C\neq AB$.

For the two dimensional example, when $x$ could be one of the 4 corners, if $C \neq AB$, then the nullspace for $D$ could be a one dimensional space (**a line**). The worst case is that this line goes though two corners, giving $\approx 50\%$ false positive.

### Base Probability Proof
- Let $D=C-AB$ as described above. 
- The nullspace of $D$ is $\text{null}(D) = \left\{ x \in \mathbb{R}^{n} \mid Dx=0 \right\}$.
- Let $x$ be a random $n$-bit vector by making each bit either a 0 or 1 with $\frac{1}{2}$ probability, independently

The algorithm returns ***YES*** if $x \in \text{null}(D)$, and ***NO*** otherwise.

If $C=AB$, then $D=0$ and $\text{null}(D)=\mathbb{R}^{n}$. Any $x$ will satisfy the nullspace, and therefore will **100%** return ***YES*** correctly.

If $C \neq AB$ however, the algorithm falsely returns ***YES*** when $Dx = 0$. Letting $Dx=r$ and $r=0$, all of $r_{i}$ (each entry of the vector) needs to be $0$:
$$
\begin{align}
\text{Pr}[r=0] & = \text{Pr}[(r_{1}=0)\cap (r_{2}=0)\cap \dots\cap (r_{n}=0)] \\
 & =\text{Pr}[r_{i}=0] \cdot \text{Pr}\left[ \bigcap_{k\neq i}(r_{k}=0) \mid r_{i} = 0 \right]  \\
 & \leq \text{Pr}[r_{i} = 0]
\end{align}
$$

Since $C\neq AB$, then $D$ is not a zero matrix. There exists at least one entry $D_{i,j}\neq 0$, and multiplying $D$ with $x$:
$$
\begin{align}
r_{i} & =\sum_{k=1}^{n} D_{i,k}\cdot x_{k} \\
 & =D_{i,j}\cdot x_{j} + \sum_{k\neq j}D_{i,k}\cdot x_{k} \\
 & =D_{i,j}\cdot x_{j} + w 
\end{align}
$$
where $w$ is the **pertinent residual term**.

Using the [[6_Total Probability#Law of Total Probability|law of total probability]], we can compute $\text{Pr}[r_{i}=0]$
$$
\text{Pr}[r_{i}=0]=\text{Pr}[r_{i}=0\mid w=0]\cdot \text{Pr}[w=0] +\text{Pr}[r_{i}=0 \mid w\neq 0]\cdot \text{Pr}[w\neq 0]
$$

$$
\begin{cases}
w=0  & \text{Case 1}\\
w\neq 0  & \text{Case 2}
\end{cases}
$$
**Case 1**:
- If $w=0$, then $r_{i}=D_{i,j}\cdot x_{j}$
- Since we know that $D_{i,j} \neq 0$, then $x_{j}=0$
$$
\begin{align}
\text{Pr}[r_{i}=0 \mid w=0] & =\text{Pr}[x_{j}=0] \\
 & =\dfrac{1}{2}
\end{align}
$$

**Case 2**:
- If $w \neq 0$, then $r_{i}=0$ implies $D_{i,j}\cdot x_{j}=-w$.
- We know that $D_{i,j} \neq 0$ and $w\neq 0$, therefore $x_{j}=1$
- It follows that $D_{i,j}=-w$
$$
\begin{align}
\text{Pr}[r_{i}=0 \mid w\neq 0] & =\text{Pr}[(x_{j} = 1) \cap (D_{i,j}=-w)] \\
 & = \text{Pr}[x_{j}=1]\cdot\text{Pr}[D_{i,j}=-w \mid x_{j}=1] \\
 & \leq \text{Pr}[x_{j}=1] \\
 & \leq \dfrac{1}{2}
\end{align}
$$

Substituting **Case 1** and **Case 2** back into $\text{Pr}[r_{i}=0]$, we get:
$$
\text{Pr}[r_{i}=0]\leq \dfrac{1}{2}
$$
and therefore
$$
\text{Pr}[\text{false positive}]\leq \dfrac{1}{2}
$$

### Amplifying Probability Proof
Using the table of probability from above,

| Probability | ***YES***               | ***NO***                   |
| ----------- | ----------------------- | -------------------------- |
| $C=AB$      | $1$                     | $0$                        |
| $C \neq AB$ | $\leq \dfrac{1}{2^{m}}$ | $\geq 1- \dfrac{1}{2^{m}}$ |

We can run the algorithm for $m$ independent runs,
- If any of the output says ***NO***, then output ***NO***
- If **all** of the output says ***YES***, then output ***YES***

The case where $C=AB$ has been proven [[#Base Probability Proof|above]].

If $C \neq AB$, then all $m$ runs of the algorithm have failed to detect the error. We have proven that the probability for a single run is $\leq \dfrac{1}{2}$, and the probability that $m$ runs fail is the [[4_Multiplication Rule#Multiplication rule|product]] of each independent run.

Let $E_{k}$ be the event that the $k$-th run produces a false positive. Since $m$ uses **independent** random $x$'s, each $E_{k}$ is independent. The probability is:
$$
\begin{align}
\text{Pr}[\text{all false positive}] & =\text{Pr}[E_{1}\cap E_{2}\cap \dots\cap E_{m}] \\
 & =\prod_{k=1}^{m} \text{Pr}[E_{k}] \\
 & \leq \prod_{k=1}^{m} \dfrac{1}{2} \\
 & \leq \dfrac{1}{2^{m}}
\end{align}
$$

