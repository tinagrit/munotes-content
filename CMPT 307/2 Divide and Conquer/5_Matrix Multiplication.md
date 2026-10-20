Lectures 9-10

## Matrix Multiplication
**Problem**: Multiplying matrices $X$ and $Y$ of size $n \times n$. For $Z=X\times Y$:
$$
Z_{ij}=\sum_{k=1}^{n}X_{ik}\cdot Y_{kj} 
$$
where $X_{ij}$ is the $i$th row and $j$th column in matrix $X$.

$Z_{ij}$ is the **dot product** of the $i$th row of $X$ and the $j$th column of $Y$.

> [!tip] Matrix multiplication is **not** commutative, that is, $A\times B \neq B\times A$

The general approach to matrix multiplication has the time complexity $\boxed{ O(n^{3}) }$ since there are $n^{2}$ entires and requires $O(n)$ per entry.

For a long time, this was believed to be optimal.

### Using Recursion
German mathematician Volker Strassen introduced a more efficient algorithm using divide and conquer.

We can break matrix multiplication into subproblems by **splitting the matrices** into smaller blocks:
$$
\begin{align}
X=\begin{bmatrix}
A & B \\
C & D
\end{bmatrix} &  & Y=\begin{bmatrix}
E & F \\
G & H
\end{bmatrix}
\end{align}
$$
where $A,B,C,D,E,F,G,H$ are blocks with size $\frac{n}{2}$.

Using this representation, $X\times Y$ can be written as:
$$
X\times Y=\begin{bmatrix}
A & B \\
C & D
\end{bmatrix}\begin{bmatrix}
E & F \\
G & H
\end{bmatrix}=\begin{bmatrix}
AE+BG & AF+BH \\
CE+DG & CF+DH
\end{bmatrix}
$$
(by definition of matrix multiplication).

We broke one multiplication into **8 subproblems** ($AE$, $BG$, $AF$, $\dots$), each with size $\frac{n}{2}$. Addition of matrices requires runtime $O(n^{2})$. This algorithm has the running time, using the [[3_Master Theorem#Master Theorem for Recurrence Relations|Master Theorem]]:
$$
T(n)=8T\left(\frac{n}{2}\right)+O(n^{2}) \implies \boxed{ T(n)=O(n^{3}) }
$$
This is no better than the general approach algorithm.

### Strassen's improvement
German mathematician Volker Strassen found that only **7 subproblems** of multiplication are needed instead of 8.

$$
X\times Y = \begin{bmatrix}
P_{5}+P_{4}-P_{2}+P_{6} & P_{1}+P_{2} \\
P_{3}+P_{4} & P_{1}+P_{5}-P_{3}-P_{7}
\end{bmatrix}
$$
where
$$
\begin{align}
P_{1} & =A(F-H) \\
P_{2} & =(A+B)H \\
P_{3} & =(C+D)E \\
P_{4} & =D(G-E) \\
P_{5} & =(A+D)(E+H) \\
P_{6} & =(B-D)(G+H) \\
P_{7} & =(A-C)(E+F)
\end{align}
$$

The submatrices $A$-$H$ are from the same split as described above.

The running time of this improved algorithm is:
$$
T(n)=7T\left( \dfrac{n}{2} \right)+O(n^{2})\implies T(n)=O(n^{\log_{2}7})\approx\boxed{ O(n^{2.81}) }
$$
