Chapter 8.5


## Matrix Decomposition

For any [[1_Matrix#Matrices|matrix]] $A$, we can **decompose** $A$ into **3** matrices [[2_Matrix multiplication#Matrix multiplication|multiplied]] together.
$$
A=BCD
$$
If $A$ has the size $m \times n$, the sizes of $B,C,D$ will be respective to $A$:
$$
A_{m\times n}=B_{m\times m}C_{m\times n}D_{n\times n}
$$
In this theorem of Singular Value Decomposition, the $B,C,D$ are $U,\Sigma,V^{T}$
$$
A=U\Sigma V^{T}
$$
where $U$ and $V$ are [[1_Orthonormal bases#Orthogonal matrices|orthogonal matrices]].

> [!important] $\Sigma$ (Uppercase sigma) is a matrix and does not denote a sum.


### Finding Σ (Singular Values)
Recall that for any arbitrary matrix $A$, $A^{T}A$ is [[1_Symmetric Matrices#Symmetric matrices|symmetric]].
Since $A^{T}A$ is symmetric, real [[1_Eigenvectors#Eigenvalues|eigenvalues]] exist.

We need to **find all eigenvalues** of $A^{T}A$.
Once we have the eigenvalues $\left\{ \lambda_{1},\lambda_{2},\dots,\lambda_{k} \right\}$, sort them in **descending order**.
We can now use them to find the **singular values**, denoted $\sigma$ (lowercase sigma)

> [!success] The singular values of $A$ is the square roots of the eigenvalues of $A^{T}A$
> $\sigma_{i}=\sqrt{ \lambda_{i} }$

We have $\left\{ \sqrt{ \lambda_{1} },\sqrt{ \lambda_{2} },\dots,\sqrt{ \lambda_{k} } \right\}$ to be $\left\{ \sigma_{1},\sigma_{2},\dots,\sigma_{k} \right\}$

We can use the singular values to construct the $\Sigma$ matrix.
$\Sigma$ is a [[1_Matrix#Diagonal matrices|diagonal]] matrix made of the **singular values**.
**Do not** change the order. (Remember that we sorted the eigenvalues earlier).

Note that $\Sigma$ **does not** have to be a [[1_Matrix#Square matrices|square]] matrix.
If matrix $A$ has the size $m\times n$, then $\Sigma$ must also have the size $m\times n$

For example, if we have 3 singular values:
- with $A_{3\times 3}:\Sigma=\begin{bmatrix}\sigma_{1}&0&0\\0&\sigma_{2}&0\\0&0&\sigma_{3}\end{bmatrix}$
- with $A_{4\times 3}:\Sigma=\begin{bmatrix}\sigma_{1}&0&0\\0&\sigma_{2}&0\\0&0&\sigma_{3}\\0&0&0\end{bmatrix}$
- with $A_{3\times 4}:\Sigma=\begin{bmatrix}\sigma_{1}&0&0&0\\0&\sigma_{2}&0&0\\0&0&\sigma_{3}&0\end{bmatrix}$


### Finding V (Eigenvectors)
Using the **sorted** eigenvalues of $A^{T}A$ that we have computed earlier: $\left\{ \lambda_{1},\lambda_{2},\dots,\lambda_{k} \right\}$
Find the **basis** of the [[1_Eigenvectors#Eigenvectors|eigenvector]] associated with each eigenvalue.

Using the same process as [[1_Eigenvectors#Finding eigenvalues and eigenvectors|the characteristic equation]], solve for each eigenvector of $A^{T}T$ using:
$$
(\lambda_{}I-A^{T}T)\vec{v_{}}=\vec{0}
$$

Once we have the bases for all eigenvectors, **normalize** them by diving each vector by its own length.

**Construct a matrix** $V$ where each column is a normalized basis vector. Do not change the order.

If done correctly, $V$ should have the size $n\times n$ for $A_{n\times n}$, and $V$ should be an [[1_Orthonormal bases#Orthogonal matrices|orthogonal matrix]].


### Finding U
For each column $\vec{v_{i}}$ of the matrix $V$ that we computed above, apply the formula:
$$
\vec{u_{i}}=\dfrac{1}{\sigma _{i}}A\vec{v_{i}}
$$
Note that the $A$ in this formula denotes the original matrix $A$, and not $A^{T}A$.

**Construct a matrix** $U$ where each column is the vector $\vec{u_{i}}$. Do not change the order.

If done correctly, $U$ should also be an [[1_Orthonormal bases#Orthogonal matrices|orthogonal matrix]].


### Extending Basis for U
From above, we know that $U$ should have the size $m\times m$ for $A_{m\times n}$. However, if $A$ is not a square matrix, $U$ may be missing a column to make $m\times m$.

If $U$ already has the size $m\times m$, **skip this step**.

To fill in the missing columns for $U$,
we need to find the **basis** of the [[6_Fundamental Subspaces#Nullspace|nullspace]] of $A^{T}$.
(This is a part of the **Fundamental Theorem of Linear Algebra**)

Set up $\left[\begin{array}{@{}c|c@{}}A^{T}&\vec{0}\end{array}\right]$, [[3_Reduced REF#Reduced Row Echelon Form|RREF]], then solve for a **normalized** basis vector.

Fill in the missing column of $U$ with the basis of $\text{Null}(A^{T})$


### Substituting back
After computing $\Sigma,V,U$, we can put them all back together with the formula:
$$
A=U\Sigma V^{T}
$$
Do not forget to transpose $V$ when putting this back.

If done correctly, multiplying $U\Sigma V^{T}$ should output $A$. Make sure that:
- $U$ and $V$ are orthogonal matrices
- $\Sigma$ is a diagonal matrix


---

## Decomposition Example

> Find the singular value decomposition of $A$, given:
> $A=\begin{bmatrix}2&2\\-1&2\end{bmatrix}$

1. Find eigenvalues of $A^{T}A$
   $A^{T}A=\begin{bmatrix}2&2\\-1&2\end{bmatrix}\begin{bmatrix}2&2\\-1&2\end{bmatrix}=\begin{bmatrix}5&2\\2&8\end{bmatrix}$
	- $\lambda_{1}=9$, $\lambda_{2}=4$
	- $\sigma_{1}=3$, $\sigma_{2}=2$
	- $\implies\Sigma=\begin{bmatrix}3&0\\0&2\end{bmatrix}$

2. Find normalized eigenvectors
	- Using $\lambda_{1}$: $\vec{v_{1}}=t\begin{bmatrix} \frac{1}{\sqrt{ 5 }} \\ \frac{2}{\sqrt{ 5 }} \end{bmatrix}$
	- Using $\lambda_{2}$: $\vec{v_{2}}=t\begin{bmatrix}-\frac{2}{\sqrt{ 5 }} \\ \frac{1}{\sqrt{ 5 }}\end{bmatrix}$
	- $\implies V=\begin{bmatrix}\frac{1}{\sqrt{ 5 }}&-\frac{2}{\sqrt{ 5 }}\\\frac{2}{\sqrt{ 5 }}&\frac{1}{\sqrt{ 5 }}\end{bmatrix}$

3. Solve for $\vec{u_{i}}=\dfrac{1}{\sigma _{i}}A\vec{v_{i}}$
	- $\vec{u_{1}}=\dfrac{1}{3}\begin{bmatrix}2&2\\-1&2\end{bmatrix}\begin{bmatrix} \frac{1}{\sqrt{ 5 }} \\ \frac{2}{\sqrt{ 5 }} \end{bmatrix}=\begin{bmatrix} \frac{2}{\sqrt{ 5 }} \\ \frac{1}{\sqrt{ 5 }} \end{bmatrix}$
	- $\vec{u_{2}}=\dfrac{1}{2}\begin{bmatrix}2&2\\-1&2\end{bmatrix}\begin{bmatrix} -\frac{2}{\sqrt{ 5 }} \\ \frac{1}{\sqrt{ 5 }} \end{bmatrix}=\begin{bmatrix} -\frac{1}{\sqrt{ 5 }} \\ \frac{2}{\sqrt{ 5 }} \end{bmatrix}$
	- $\implies U=\begin{bmatrix}\frac{2}{\sqrt{ 5 }}&-\frac{1}{\sqrt{ 5 }}\\\frac{1}{\sqrt{ 5 }}&\frac{2}{\sqrt{ 5 }}\end{bmatrix}$

4. Substitute into $A=U\Sigma V^{T}$
	- $A=\begin{bmatrix}\frac{2}{\sqrt{ 5 }}&-\frac{1}{\sqrt{ 5 }}\\\frac{1}{\sqrt{ 5 }}&\frac{2}{\sqrt{ 5 }}\end{bmatrix}\begin{bmatrix}3&0\\0&2\end{bmatrix}\begin{bmatrix}\frac{1}{\sqrt{ 5 }}&\frac{2}{\sqrt{ 5 }}\\-\frac{2}{\sqrt{ 5 }}&\frac{1}{\sqrt{ 5 }}\end{bmatrix}$


---

## The Pseudo-Inverse

Recall: any matrix with the [[1_Determinants#The Determinant|determinant]] of 0 is **not** [[7_Inverses#Matrix Inverse|invertible]]

This means that the inverse does not exist, but we can still find a **pseudo-inverse** of the matrix such that:
$$
AA^{+}A=A
$$
where $A^{+}$ is the pseudo-inverse.

Notice that for invertible matrices, $(AA^{-1})A=IA=A$. The pseudo-inverse acts **almost** like an inverse.

Using the [[#Matrix Decomposition|SVD]], the pseudo-inverse is found through the formula:

> [!success] Formula for finding the pseudo-inverse
> $A^{+}=V\Sigma ^{+}U^{T}$
> 
> where $\Sigma^{+}$ is the matrix of the reciprocals of all non-zero entries of $\Sigma$.


### Pseudo-Inverse and Least Squares
Recall that the [[3_Least Squares|Method of Least Squares]] uses the formula:
$$
\vec{x}=(A^{T}A)^{-1}A^{T}\vec{b}
$$
We can use the **pseudo-inverse** of $A$ to derive another formula for the method of least squares.
$$
\vec{x}=A^{+}\vec{b}
$$

