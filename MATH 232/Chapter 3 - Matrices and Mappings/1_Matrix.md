Chapter 3.1
<div class="PWW">
<div data-callout-metadata="" data-callout-fold="" data-callout="warning" class="callout"><div class="callout-title" dir="auto"><div class="callout-icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-alert-triangle"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3"></path><path d="M12 9v4"></path><path d="M12 17h.01"></path></svg></div><div class="callout-title-inner">Narrow Screen</div></div><div class="callout-content">
<p dir="auto">This page includes wide mathematical graphics which may not fit well on your screen. Viewing this on a wider screen is highly recommended.</p>
</div></div>
</div>


## Matrices
A **matrix** (doesn't have to be [[1_Augmented Matrix|augmented]]) is a rectangular array of numbers. For example:
$$
A=\begin{bmatrix}
1 & 2 & 3 & 4 \\
5 & 6 & 7 & 8 \\
9 & 10 & 11 & 12
\end{bmatrix}
$$
Matrix $A$ has 3 rows and 4 columns, therefore the **size** of $A$ is $3\times 4$ (row comes first)

To refer to an **element** in the matrix, use the notation: $(A)_{\text{row}\text{column}}$ or $a_{\text{rowcolumn}}$. For example, $(A)_{22}=a_{22}=6$ since the element in the second row and column is 6.
$$
A=\begin{bmatrix}
1 & 2 & 3 & 4 \\
5 & \boxed{ 6 } & 7 & 8 \\
9 & 10 & 11 & 12
\end{bmatrix}
$$

The entire matrix can be represented using a general element with row and column variables $i$ and $j$, inside square brackets. For example, $A=[a_{ij}]$.

The size can also be specified, although not required: $A=[a_{ij}]_{3\times 4}$


### Matrix equality
Two matrices $A$ and $B$ are equal if
- they have **the same size**, and
- **each entries** are equal
$$
A=B \iff  \forall i,j\text{ , } a_{ij}=b_{ij} 
$$

### Square matrices
are matrices with the same number of rows and columns.
$$
S=\begin{bmatrix}
8 & 7 & 6 \\
5 & 4 & 3 \\
2 & 1 & 0
\end{bmatrix}
$$
For example, $S$ is a square matrix since $\text{rows}=\text{columns}=3$

The **main diagonal** or **diagonal entries** refers to elements in the diagonal line drew from top left to bottom right. For example, the boxed numbers are diagonal entries.
$$
S=\begin{bmatrix}
\boxed{ 8 } & 7 & 6 \\
5 & \boxed{ 4 } & 3 \\
2 & 1 & \boxed{ 0 }
\end{bmatrix}
$$

#### Diagonal matrices
are [[#Square matrices|square matrices]] where non-diagonal entires are **all 0s**.
$$
D=\begin{bmatrix}
1 & 0 & 0 \\
0 & 2 & 0 \\
0 & 0 & 3
\end{bmatrix}
$$
For example, $D$ is a diagonal matrix.


#### Triangular matrices
are [[#Square matrices|square matrices]] that partially satisfy being [[#Diagonal matrices|diagonal matrices]].

- A **lower triangular** (LT) matrix: all elements above the diagonal entries are all 0s. (elements below the diagonal entries can be anything)
	- For example, $L=\begin{bmatrix}1&0&0\\2&3&0\\4&5&6\end{bmatrix}$
	- $a_{ij}=0$ for all $i>j$
- An **upper triangular** (UT) matrix: all elements below the diagonal entries are all 0s. (elements above the diagonal entries can be anything)
	- For example, $U=\begin{bmatrix}1&2&3\\0&4&5\\0&0&6\end{bmatrix}$
	- $a_{ij}=0$ for all $i<j$


> [!important] The [[#Diagonal matrices|diagonal matrix]] is both **lower** and **upper** triangular


#### Identity matrices
are [[#Square matrices|square matrices]] and [[#Diagonal matrices|diagonal matrices]] where all **diagonal entries are 1**.
$$
I=\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
For example, $I$ is an identity matrix.


---

## Row and Column Vectors
- matrix can be thought of as a **list** of vectors
- vectors can be in a **row**, or in a **column**

For example, the matrix $E=\begin{bmatrix}2 & 0 \\7 & -5 \\4 & 3\end{bmatrix}$ is consisted of:
- Two column vectors
	- $c_{1}=\begin{bmatrix}2\\7\\4\end{bmatrix}$ and $c_{2}=\begin{bmatrix}0\\-5\\3\end{bmatrix}$
	- $\therefore E=\begin{bmatrix}c_{1}&c_{2}\end{bmatrix}$
- Three row vectors
	- $r_{1}=\begin{bmatrix}2&0\end{bmatrix}$, $r_{2}=\begin{bmatrix}7&-5\end{bmatrix}$, and $r_{3}=\begin{bmatrix}4&3\end{bmatrix}$
	- $\therefore E=\begin{bmatrix}r_{1}\\r_{2}\\r_{3}\end{bmatrix}$


---

## Basic matrix operations
Also see [[1_Augmented Matrix#Elementary Row Operations|Augmented Matrix Operations]]

### Addition and Subtraction
- add or subtract **each element**
- two matrices need to have the same size
	- if they are different sizes, the sum is **undefined**
- For example:

$$
A=\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
,B=\begin{bmatrix}
5 & 6  \\
7 & 8
\end{bmatrix}\implies A+B=\begin{bmatrix}
1+5 & 2+6 \\
3+7 & 4+8
\end{bmatrix}
=\begin{bmatrix}
6 & 8 \\
10 & 12
\end{bmatrix}
$$
$$
C=\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
,D=\begin{bmatrix}
5 & 6 & 7 \\
8 & 9 & 10
\end{bmatrix}
\implies C+D=\text{undefined}
$$

### Scalar multiplication
- multiply the scalar quantity to **every element** in the matrix
- For example:

$$
E=\begin{bmatrix}
2 & 0 \\
7 & -5 \\
4 & 3
\end{bmatrix}
\implies
5E=\begin{bmatrix}
2\times 5 & 0\times 5 \\
7\times 5  & -5\times 5 \\
4\times 5  & 3\times 5
\end{bmatrix}=\begin{bmatrix}
10 & 0 \\
35 & -25 \\
20 & 15
\end{bmatrix}
$$

### Transpose
- **switch** rows/columns
- if the original matrix has the size $i\times j$, the new matrix will have the size $j\times i$
- row $m$ becomes column $m$
- column $n$ becomes row $n$
- denoted with a **superscript** $T$, i.e. $A^{T}$
- For example:

$$
E=\begin{bmatrix}
2 & 0 \\
7 & -5 \\
4 & 3
\end{bmatrix}
\implies
E^{T}=\begin{bmatrix}
2 & 7 & 4 \\
0 & -5 & 3
\end{bmatrix}
$$

> [!important] Two Transpose operators cancel out.
> $(A^{T})^{T}=A$

---

## Matrix Spans and Basis
Also see [[2_Vector Spans and Basis|Vector Spans and Basis]]

- a **span** is a set of every possible [[1_Vectors#Linear combinations|linear combination]]
- same concept with [[2_Vector Spans and Basis|Vector spans]]
- a set of matrices is [[2_Vector Spans and Basis#Linear independence|linearly independent]] if the span is equal to 0 if and only if each constant in the span is 0

### Matrix Spans and Basis Examples

> What is the span of $S$, given:
> $S=\left\{  \begin{bmatrix}1&2\\1&0\end{bmatrix},\begin{bmatrix}0&1\\-1&2\end{bmatrix},\begin{bmatrix}1&1\\3&-1\end{bmatrix}\right\}$

$\text{span}\{S\}$
$=\left\{ a\begin{bmatrix}1&2\\1&0\end{bmatrix}+b\begin{bmatrix}0&1\\-1&2\end{bmatrix} +c\begin{bmatrix}1&1\\3&-1\end{bmatrix} \mid a,b,c \in \mathbb{R} \right\}$


> Is $\begin{bmatrix}2&3\\2&-3\end{bmatrix}$ in $\text{span}\{S\}$?

- set the span **equal to** the matrix
- matrix is in the span if it is **possible to solve** for each constant
	- expand the span equation
	- set up an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]] to solve

Show that there exists $a,b,c$ such that:
$$
a\begin{bmatrix}1&2\\1&0\end{bmatrix}+b\begin{bmatrix}0&1\\-1&2\end{bmatrix} +c\begin{bmatrix}1&1\\3&-1\end{bmatrix}=\begin{bmatrix}
2&3\\2&-3
\end{bmatrix}
$$
Expanding the left hand side, we get:
$$
\begin{bmatrix}
a+c&2a+b+c\\a-b+3c&2b-c
\end{bmatrix}
=\begin{bmatrix}
2&3\\2&-3
\end{bmatrix}
$$
Set up a system of equations from each element of the matrices
$$
\begin{align}
a+c & =2 \\
2a+b+c & =3 \\
a-b+3c & =2 \\
2b-c & =-3
\end{align}
$$
Use this to set up an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]].
$$
\begin{bmatrix}
1 & 0 & 1 & 2 \\
2 & 1 & 1 & 3 \\
1 & -1 & 3 & 2 \\
0 & 2 & -1 & -3
\end{bmatrix}
$$
[[3_Reduced REF|Row reducing]] this augmented matrix, we get:
$$
\begin{bmatrix}
1 & 0 & 0 & 3 \\
0 & 1 & 0 & -2 \\
0 & 0 & 1 & -1 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$
Since we don't have $\begin{bmatrix}0&0&0&1\end{bmatrix}$ at the end, this system of equations is [[2_Row Echelon#Consistency|consistent]], and therefore the **matrix is in the span**.


> Is $S$ linearly independent?

- set the span **equal to the zero matrix** of the same size
- if all the constants must be 0 to produce the zero matrix, it is [[2_Vector Spans and Basis#Linear independence|linearly independent]].
	- set up an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]] to solve

Show that $a,b,c$ must all be 0 for the following to be true:
$$
a\begin{bmatrix}1&2\\1&0\end{bmatrix}+b\begin{bmatrix}0&1\\-1&2\end{bmatrix} +c\begin{bmatrix}1&1\\3&-1\end{bmatrix}=\begin{bmatrix}
0&0\\0&0
\end{bmatrix}
$$
Expanding the left hand side, we get:
$$
\begin{bmatrix}
a+c&2a+b+c\\a-b+3c&2b-c
\end{bmatrix}
=\begin{bmatrix}
0&0\\0&0
\end{bmatrix}
$$
Set up a system of equations from each element of the matrices
$$
\begin{align}
a+c & =0 \\
2a+b+c & =0 \\
a-b+3c & =0 \\
2b-c & =0
\end{align}
$$
Use this to set up an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]].
$$
\begin{bmatrix}
1 & 0 & 1 & 0 \\
2 & 1 & 1 & 0 \\
1 & -1 & 3 & 0 \\
0 & 2 & -1 & 0
\end{bmatrix}
$$
[[3_Reduced REF|Row reducing]] this augmented matrix, we get:
$$
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$
Since the system of equations implies that $a=b=c=0$, it means that $S$ **is linearly independent**.