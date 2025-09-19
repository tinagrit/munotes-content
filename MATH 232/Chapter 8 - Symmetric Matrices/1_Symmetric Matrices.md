Chapter 8.1


## Symmetric matrices
- a [[1_Matrix|matrix]] is **symmetric** if $A^{T}=A$
	- the transpose is equal to the original

If a matrix $A$ is symmetric, it has the following properties:
- $A$ is a [[1_Matrix#Square matrices|square matrix]]
- All of $A$'s [[1_Eigenvectors#Eigenvalues|eigenvalues]] are real
- All [[1_Eigenvectors|eigenvectors]] of $A$ are [[1_Orthonormal bases#Orthonormal basis|orthogonal]] and [[3_Reduced REF#Linear Independence|linearly independent]]
- $A$ is orthogonally [[2_Diagonalization|diagonalizable]]
	- there exists an [[1_Orthonormal bases#Orthogonal matrices|orthogonal]] matrix $P$ containing $A$'s eigenvalues such that $P^{-1}AP=D$

> [!important] 
> For any arbitrary rectangular matrix $M$, 
> $M^{T}M$ is symmetric


### Orthogonally diagonalize
This process is very similar to regular [[2_Diagonalization|Diagonalization]].

The only difference is that the $P$ (transition) matrix has to be an [[1_Orthonormal bases#Orthogonal matrices|orthogonal]] matrix. If a matrix $A$ can be orthogonally diagonalize, then $A$ is symmetric, and vice versa.

For example:
> Find the orthogonal matrix $P$ that diagonalizes the symmetric matrix $A$, given:
> $A=\begin{bmatrix}5&2\\2&2\end{bmatrix}$

Performing the [[1_Eigenvectors#Eigenvalues|eigenvalue]] calculation, we get:
$$
\begin{align}
\lambda_{1}=1 &  & \lambda_{2}=6
\end{align}
$$

Using the eigenvalues, the [[1_Eigenvectors#Eigenvectors|eigenvectors]] corresponding to each value are:
$$
\begin{align}
\vec{v_{1}}=t\begin{bmatrix}
-\frac{1}{2}\\1
\end{bmatrix}=t\begin{bmatrix}
-1\\2
\end{bmatrix} &  & \vec{v_{2}}=t\begin{bmatrix}
2\\1
\end{bmatrix}
\end{align}
$$

Therefore, the transition matrix $P$ that diagonalizes the matrix is:
$$
P=\begin{bmatrix}
-1&2\\2&1
\end{bmatrix}
$$

To make this transition matrix an **orthogonal** matrix, we need to **normalize** it by diving each column by its own length.
$$
\begin{align}
\lVert \vec{v_{1}} \rVert &  =\sqrt{ \left(-1\right)^{2}+(2)^{2} }=\sqrt{ 5 } \\
\lVert \vec{v_{2}} \rVert &  =\sqrt{ \left(2\right)^{2}+(1)^{2} }=\sqrt{ 5 }
\end{align}
$$

$\therefore$ The orthogonal matrix $P$ that diagonalizes $A$ is:
$$
P=\begin{bmatrix}
-\frac{1}{\sqrt{ 5 }}&\frac{2}{\sqrt{ 5 }}\\\frac{2}{\sqrt{ 5 }}&\frac{1}{\sqrt{ 5 }}
\end{bmatrix}
$$

We can show that $P$ actually diagonalizes $A$ by substituting into the formula:
$$
D=P^{-1}AP
$$
Since $P$ is orthogonal, $P^{-1}=P^{T}=P$
$$
D=\begin{bmatrix}
-\frac{1}{\sqrt{ 5 }}&\frac{2}{\sqrt{ 5 }}\\\frac{2}{\sqrt{ 5 }}&\frac{1}{\sqrt{ 5 }}
\end{bmatrix}\begin{bmatrix}5&2\\2&2\end{bmatrix}\begin{bmatrix}
-\frac{1}{\sqrt{ 5 }}&\frac{2}{\sqrt{ 5 }}\\\frac{2}{\sqrt{ 5 }}&\frac{1}{\sqrt{ 5 }}
\end{bmatrix}
$$
$$
D=\begin{bmatrix}
1&0\\0&6
\end{bmatrix}
$$

$D$ is diagonal and $P$ is the orthogonal matrix that diagonalizes $A$.