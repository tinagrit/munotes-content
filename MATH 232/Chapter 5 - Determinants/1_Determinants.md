Chapter 5.1 and 5.2


## The Determinant
- is a **real number**
- a **function** derived from a [[1_Matrix#Square matrices|square matrix]]
- $M_{n\times n} \to \mathbb{R}$
- denoted $\det(A)$ or $|A|$ (NOT absolute value)

### 1x1 matrix
- for any $M_{1\times 1}$ with
$$
A=[a]
$$
- the $\det(A)=a$ (the only value in the matrix)


### 2x2 matrix
- for any $M_{2\times 2}$ with
$$
A=\begin{bmatrix}
a&b\\c&d
\end{bmatrix}
$$
- the $\det(A)$ is:
$$
\det(A)=
\begin{vmatrix}
a&b\\c&d
\end{vmatrix}=ad-bc
$$

Notice that it is a subtraction of each cross multiplication
![[det1 1.png|300]]

### 3x3 matrix
- defined **recursively** in terms of 2x2 matrices
- for any $M_{3\times 3}$ with
$$
A=\begin{bmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}
$$
- the $\det(A)$ is:
$$
\det(A)=a\begin{vmatrix}
e & f \\
h & i
\end{vmatrix}-b\begin{vmatrix}
d & f \\
g & i
\end{vmatrix}+c\begin{vmatrix}
d & e \\
g & h
\end{vmatrix}
$$

This is done by:
- **choosing** each element from the top row,
- **ignore** the same row and column of such element
- multiply that element by the determinant **of the rest**

![[det2.png|600]]

This idea is generalized as minors and cofactors below.


---

## Minors and Cofactors

### Minor
- a **minor** is the determinant of the sub-matrix
	- after **removing** the row and column an element in on
- denoted $M_{ij}$ where 
	- $i$ is the row 
	- $j$ is the column

For example, in a 3x3 matrix, to find $M_{11}$:
- locate the element in row 1 and column 1
![[det4.png|200]]
- remove the first row and first column
![[det3.png|200]]
- the determinant of the rest of the matrix is the **minor**
	- in this case, $M_{11}=\begin{vmatrix}e&f\\g&h\end{vmatrix}=eh-fg$


### Cofactor
- is either the positive or negative of minor
	- $C_{ij}=\pm M_{ij}$
- if the **sum** of row and column:
	- is even, the cofactor is equal to minor
	- is odd, the cofactor is $(-1)\times$ minor
$$
C_{ij}=(-1)^{i+j}M_{ij}
$$


---

## Cofactor Expansion
- the **determinant** of a matrix can be found by each cofactor along **a row** or **a column**

Choosing any $j$-th column, the determinant is:
$$
\det(A)=a_{1j}C_{1j}+a_{2j}C_{2j}+\dots+a_{nj}C_{nj}
$$

Choosing any $i$-th row, the determinant is:
$$
\det(A)=a_{i1}C_{i 1}+a_{i 2}C_{i 2}+\dots+a_{in}C_{in}
$$

These two ways give **the same answer**.

> [!important] Try to choose a row or column that has a 0 entry, if possible, to minimize computation.

---

## Properties of the Determinant

### Matrix Inverse
- these three statements are **equivalent**
	1. The matrix is [[7_Inverses#Matrix Inverse|invertible]]
	2. The [[2_Row Echelon#Ranks|rank]] is $n$
	3. The determinant is ***not zero***

> [!important] The inverse does not exist if the determinant is 0. See why in [[7_Inverses#General 2x2 Inverse|general 2x2 inverse]].

### Transpose
- Since the determinant can be found **along** any **rows or columns**, the [[1_Matrix#Transpose|transpose]] of matrix has the same determinant
$$
\det(A)=\det(A^{T})
$$


### Triangular matrices
For any [[1_Matrix#Triangular matrices|Triangular matrices]], the determinant is the **product** of the **diagonal entries**.
For example:
$$\begin{align}
A=\begin{bmatrix}
1 & 2 & 3 & 4 \\
0 & 5 & 6 & 7 \\
0 & 0 & 8 & 9 \\
0 & 0 & 0 & 1
\end{bmatrix} &  & \det(A)=(1)(5)(8)(1)
\end{align}

$$

> [!important] Try to row reduce matrices into an upper triangular matrix for an easier computation. 
> Be careful of changes in the determinant from performing [[#Elementary Row Operation]]


### Product of the determinants
- In general, the determinant of the **product of two matrices** is equal to the **product of the determinants** of each matrix
$$
\det(AB)=\det(A)\det(B)
$$


### When det = 0
- If there is a row or column that is **entirely 0**, then the $\det(A)=0$. For example:
$$\begin{align}
A=\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
0 & 0 & 0
\end{bmatrix} &  & \det(A)=0
\end{align}
$$


### Elementary Row Operation
- [[#Adding a multiple of a row to another]] ***preserves*** the determinant
- [[#Scalar multiplication]] to a row ***changes*** the determinant
- [[#Swapping rows]] ***changes*** the determinant

#### Adding a multiple of a row to another
- This ***preserves*** the determinant
- This means that:
	- if there is a row that is a [[1_Vectors#Linear combinations|linear combination]] of other rows, that row can be made into a 0 row and $\det(A)=0$
	- if there is a column that is a [[1_Vectors#Linear combinations|linear combination]] of other columns, that column can be made into a 0 column and $\det(A)=0$
$$\begin{align}
A=\begin{bmatrix}
1 & 2 & 3 \\
2 & 4 & 6 \\
3 & 6 & 9
\end{bmatrix}\sim \begin{bmatrix}
1 & 2 & 3 \\
0 & 0 & 0 \\
0 & 0 & 0
\end{bmatrix} &  & \det(A)=0
\end{align}
$$

#### Scalar multiplication
- As mentioned above, multiplying a row by a scalar quantity **changes** the determinant.
- The determinant changes **by the same rate**

For example, let the determinant of the following matrix be $\det(A)=d$
$$
A=\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{bmatrix}
$$
If we multiply the first row by 2: $R_{1}\mapsto 2R_{1}$
$$
A'= \begin{bmatrix}
2 & 4 & 6 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{bmatrix}
$$
The determinant now becomes $\det (A')=2d$

Note that the change in the determinant is accounted for all changes in any row/column.

If the entire matrix is multiplied by 2, for example, $2A$:
$$
2A=\begin{bmatrix}
2 & 4 & 6 \\
8 & 10 & 12 \\
14 & 16 & 18
\end{bmatrix}
$$
These changes include:
- $R_{1}\mapsto 2R_{1}$
- $R_{2}\mapsto 2R_{2}$
- $R_{3}\mapsto 2R_{3}$

Therefore, the determinant becomes $\det(2A)=(2\times 2\times 2)d$

**In general**:
$$
\det(rA)=r^{n}\det(A)
$$
where
- $A$ is a matrix
- $r$ is a scalar quantity
- $n$ is the number of rows/columns (recall: $A$ is a square matrix)

#### Swapping rows
- if we swap two rows/columns, the determinant is **negated**

For example, let the determinant of the following matrix be $\det(A)=d$
$$A=\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{bmatrix}$$
If we swap two rows: $R_{1} \leftrightarrow R_{2}$
$$
A'=\begin{bmatrix}
4 & 5 & 6 \\
1 & 2 & 3 \\
7 & 8 & 9
\end{bmatrix}
$$
The determinant now becomes $\det(A')=-d$

**In general,** by swapping two rows,
$$
\det(B)=-\det(A)
$$
