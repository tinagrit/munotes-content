Chapter 3.5


## Matrix Inverse
- A matrix $B$ is **the inverse** of $A$,  if $BA=I$ ([[1_Matrix#Identity matrices|identity]] matrix)
	- See [[2_Matrix multiplication#Matrix multiplication|matrix multiplication]]
- $A$ is **invertible** if an inverse exists
	- **not all** matrices are invertible
- The inverse of a matrix is **unique**
	- NO matrix has 2 different inverses
- Denoted $A^{-1}$

For example, verify that $B$ is an inverse of $A$:
$$
A=\begin{bmatrix}
1 & 2 \\
-1 & 3
\end{bmatrix},B=\begin{bmatrix}
\frac{3}{5} & -\frac{2}{5} \\
\frac{1}{5} & \frac{1}{5}
\end{bmatrix}
$$
$$
AB=\begin{bmatrix}
1 & 2 \\
-1 & 3
\end{bmatrix}\begin{bmatrix}
\frac{3}{5} & -\frac{2}{5} \\
\frac{1}{5} & \frac{1}{5}
\end{bmatrix}=\begin{bmatrix}
\frac{3}{5}+\frac{2}{5} & -\frac{2}{5}+\frac{2}{5} \\
-\frac{3}{5}+\frac{3}{5} & \frac{2}{5}+\frac{3}{5}
\end{bmatrix}=\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$
Since $AB=I$
- $B=A^{-1}$


### Matrix Inverse Properties

1. $(tA)^{-1}=\dfrac{1}{t}A^{-1}$
   
2. $(AB)^{-1}=B^{-1}A^{-1}$ 
   (note that matrix multiplication is **NOT** commutative; do not swap order)
   
3. $(A^{T})^{-1}=(A^{-1})^{T}$


### Finding the Inverse
- finding the inverse of an invertible matrix $A$
- use the "compound matrix" $\begin{bmatrix}A \mid I\end{bmatrix}$
- [[3_Reduced REF#Reduced Row Echelon Form|row reduce]] the compound matrix, if the **left side** becomes the [[1_Matrix#Identity matrices|identity]] matrix, the **right side** is the **inverse**

For example, finding $A^{-1}$ where:
$A=\begin{bmatrix}2&0&0\\0&4&3\\0&1&1\end{bmatrix}$

The compound matrix is:
$$
\left[ \begin{array}{ccc|ccc}
2&0&0&1&0&0 \\
0&4&3&0&1&0 \\
0&1&1&0&0&1
\end{array} \right] 
$$
Reducing this matrix to [[3_Reduced REF#Reduced Row Echelon Form|RREF]], we get:
$$
\left[ \begin{array}{ccc|ccc}
1&0&0&\frac{1}{2}&0&0 \\
0&1&0&0&1&-3 \\
0&0&1&0&-1&4
\end{array} \right] 
$$
Since the left side is now identity, the **right side is the inverse**
$$
A^{-1}=\begin{bmatrix}
\frac{1}{2}&0&0 \\
0&1&-3 \\
0&-1&4
\end{bmatrix}
$$

> [!important] If the left side cannot be made into RREF, the matrix is NOT invertible.


### General 2x2 Inverse

Finding the inverse of a general $2\times 2$: $M=\begin{bmatrix}a&b\\c&d\end{bmatrix}$ matrix.
Reducing the compound matrix, we get:
$$
\left[ \begin{array}{cc|cc}
a&b&1&0 \\
c&d&0&1
\end{array} \right]\sim \left[ \begin{array}{cc|cc}
1&0& \dfrac{d}{ad-bc} & -\dfrac{b}{ad-bc} \\
0&1& -\dfrac{c}{ad-bc} & \dfrac{a}{ad-bc}
\end{array} \right]
$$
Therefore:
$$
M^{-1}=\dfrac{1}{ad-bc}\begin{bmatrix}
d & -b \\
-c & a
\end{bmatrix}
$$

This means that for any $2\times 2$ matrix, if $ad-bc=0$, the matrix is not invertible.

> [!important] The $ad-bc$ is the **determinant** of the matrix. See more at [[1_Determinants#The Determinant|determinants]].

