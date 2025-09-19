Chapter 3.4


The four fundamental subspaces include
- [[#Column Spaces]]
- [[#Row Spaces]]
- [[#Nullspace]]
- [[#The Left Nullspace]]


## Column Spaces
- the [[2_Vector Spans and Basis#Span|span]], all **linear combinations of the columns** of a matrix
- denoted $\text{Col}(A)$
$$
\text{Col}(A)=\text{Span}\left\{ \vec{c_{1}},\vec{c_{2}},\dots,\vec{c_{n}} \right\} 
$$
For example, finding the column space $\text{Col}(A)$ where
$A=\begin{bmatrix}1&2&8\\1&1&5\\1&0&-2\end{bmatrix}$
$$
\text{Col}(A)=\text{Span}\left\{ \begin{bmatrix}
1\\1\\1
\end{bmatrix},\begin{bmatrix}
2\\1\\0
\end{bmatrix},\begin{bmatrix}
8\\5\\-2
\end{bmatrix} \right\} 
$$

### Column Space Dimension
- the number of **leading** variables after [[3_Reduced REF#Reduced Row Echelon Form|row-reduction]]
- denoted $\text{dim Col}(A)$

For example, reducing $A$:
$$
\begin{bmatrix}1&2&8\\1&1&5\\1&0&-2\end{bmatrix}\sim \begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
This means that all column vectors are [[3_Reduced REF#Linear Independence|linearly independent]], and $\text{dim Col}(A)=3$


---
## Row Spaces
- the [[2_Vector Spans and Basis#Span|span]], all **linear combinations of the rows** of a matrix
- denoted $\text{Row}(A)$
$$
\text{Row}(A)=\text{Span}\left\{ \vec{r_{1}},\vec{r_{2}},\dots,\vec{r_{n}} \right\} 
$$
For example, finding the row space $\text{Row}(A)$ using the $A$ from above:
$$
\text{Row}(A)=\text{Span}\left\{ \begin{bmatrix}
1\\2\\8
\end{bmatrix},\begin{bmatrix}
1\\1\\5
\end{bmatrix},\begin{bmatrix}
1\\0\\-2
\end{bmatrix} \right\} 
$$

### Row Space Dimension
- the number of **leading** variables after [[3_Reduced REF#Reduced Row Echelon Form|row-reduction]] of the [[1_Matrix#Transpose|transpose]]
- denoted $\text{dim Row}(A)$

For example, reducing $A^{T}$:
$$
\begin{bmatrix}1&1&1\\2&1&0\\8&5&-2\end{bmatrix}\sim \begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
This means that all row vectors are [[3_Reduced REF#Linear Independence|linearly independent]], and $\text{dim Row}(A)=3$



---
## Nullspace
- or **Kernel**
- the set of all input vectors that **make the output** $\mathbf{0}$ (a zero vector)
- denoted $\text{Null}(L)$
$$
\text{Null}(L)=\left\{ \vec{x}\in \mathbb{R}^{n}\mid L(\vec{x})=\mathbf{0} \right\} 
$$
- the nullspace is a [[4_Subspaces#Subspaces|subspace]]
	- $\vec{x_{1}}\in \text{Null}(L)$
		- $L(\vec{x_{1}})=\mathbf{0}$
		- $L(c\vec{x_{1}})=cL(\vec{x_{1}})=\mathbf{0}$
		- $L$ is closed under scalar multiplication
	- $\vec{x_{2}}\in \text{Null}(L)$
		- $L(\vec{x_{2}})=\mathbf{0}$
		- $L(\vec{x_{1}}+\vec{x_{2}})=L(\vec{x_{1}})+L(\vec{x_{2}})=\mathbf{0}$
		- $L$ is closed under addition


### Nullspace Dimension
- the number of **free variables**
	- total number of variables (number of columns) $-$ number of leading variables (rank)
- this is **DIFFERENT** from the [[3_Reduced REF#Spans and Dimensions|dimension of a matrix]] or the [[#Column Space Dimension|dimension of column and row spaces]] (the number of leading variables)
- denoted $\text{dim Null}(L)$
$$
\text{dim Null}(M)=\text{columns of }M-\text{rank}(M)
$$

Moving $\text{rank}(M)$ to the other side, we get:
$$
\text{columns of }M=\text{dim Null}(M)+\text{rank}(M)
$$
This is called the **Rank-Nullity Theorem**.

If $M$ is a [[3_Functions and Mappings#Linear mappings|linear mapping]] from [[1_ Vector Spaces#Vector space|space]] $A\to B$, then the $\text{columns of }M$ is equivalent to $\text{dim}(A)$. The Rank-Nullity Theorem is also stated as:
$$
\text{dim}(A)=\text{dim Null}(M)+\text{rank}(M)
$$


### The Left Nullspace
- the nullspace of a [[1_Matrix#Transpose|Transpose]] of a matrix
- denoted $\text{Null}(A^{T})$
$$
\text{Null}(A^{T})=\left\{ \vec{x}\in \mathbb{R}^{m}\mid A^{T}\vec{x}=\mathbf{0} \right\} 
$$


### Nullspace Examples

> Find $\text{Null}(L)$ and $\text{dim Null}(L)$ given:
> $L(x_{1},x_{2},x_{3})=(2x_{1},-x_{2}+2x_{3})$

Since we want the output to be $\mathbf{0}$, set:
$$
\begin{bmatrix}
2x_{1} \\
-x_{2}+2x_{3}
\end{bmatrix}=\begin{bmatrix}
0 \\
0
\end{bmatrix}
$$
Use this equation to set up an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]]:
$$
\begin{bmatrix}
2 & 0 & 0 & 0 \\
0 & -1 & 2 & 0
\end{bmatrix}
$$
Reducing this to [[3_Reduced REF#Reduced Row Echelon Form|RREF]], we get:
$$
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & -2 & 0
\end{bmatrix}
$$
Therefore:
$$
\vec{x}=\text{Null}(L)=t\begin{bmatrix}
0 \\
2 \\
1
\end{bmatrix},t\in \mathbb{R}
$$
The dimension of the nullspace is $\text{dim Null}(L)=1$


> Find $\text{Null}(A)$ and $\text{dim Null}(A)$ given:
> $A=\begin{bmatrix}2&1&3\\2&-2&6\\4&3&5\end{bmatrix}$
> 
> Note: $A$ is a [[4_Transformations#Geometrical Transformations|transformation]] matrix and a linear mapping

Set $A$ to $\mathbf{0}$ and solve for $x_{1},x_{2},x_{3}$:
$$
\begin{bmatrix}
2 & 1 & 3 & 0 \\
2 & -2 & 6 & 0 \\
4 & 3 & 5 & 0
\end{bmatrix}\sim \begin{bmatrix}
1 & 0 & 2 & 0 \\
0 & 1 & -1 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$
Therefore:
$$
\text{Null}(A)=t\begin{bmatrix}
-2 \\
1 \\
1
\end{bmatrix},t\in \mathbb{R}
$$
The dimension of the nullspace is $\text{dim Null}(A)=1$

