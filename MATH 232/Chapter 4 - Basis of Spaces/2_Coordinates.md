Chapter 4.4, 4.5 and 4.6


## Coordinates
Also see [[1_Orthonormal bases#Projection onto a subspace|Projection onto a subspace]] where this is further generalized.

- [[1_Vectors#Vectors|Vectors]] can be written as a **linear combination** of [[2_Vector Spans and Basis#Basis|basis]] vectors.
- For example, writing the vector $\vec{v}=\begin{bmatrix}1\\2\end{bmatrix}$ in terms of the [[3_Functions and Mappings#Standard Basis Vectors|Standard Basis Vectors]] for $\mathbb{R}^{2}$, we get:
$$
\begin{bmatrix}
1\\2
\end{bmatrix}=1\begin{bmatrix}
1\\0 
\end{bmatrix}+2\begin{bmatrix}
0\\1
\end{bmatrix}
$$
- In this case, we require 1 of $e_{1}$ and 2 of $e_{2}$, the quantities 1 and 2 are **the coordinates**
- Coordinates *with respect to a basis* refers to **how much of each basis** vector is needed to create the final vector
- Denoted $[\vec{v}]_{B}=\begin{bmatrix}c_{1}\\c_{2}\\\vdots\\c_{n}\end{bmatrix}$ where
	- $B$ is the basis
		- If the subscript does not exist (not defined), assume that the basis is the [[3_Functions and Mappings#Standard Basis Vectors|Standard Basis]]. Most vectors are written this way.
	- $\begin{bmatrix}c_{1}\\c_{2}\\\vdots\\c_{n}\end{bmatrix}$ is the **coordinate vector/matrix** with respect to $B$. Each row is the quantity (coefficients) of each basis vector. The number of rows is the number of basis vectors.


### Finding coordinates example

 > Find the coordinates of $\vec{v}=\begin{bmatrix}0\\3\end{bmatrix}$ with respect to basis $B$ where:
 > $B=\left\{ \vec{v_{1}},\vec{v_{2}} \right\}$, $\vec{v_{1}}=\begin{bmatrix}2\\1\end{bmatrix}$, $\vec{v_{2}}=\begin{bmatrix}-1\\1\end{bmatrix}$
 
 We want to represent vector $\vec{v}$ as a linear combination of the two basis vectors, therefore:
$$
\vec{v}=s\vec{v_{1}}+t\vec{v_{2}}
$$
where $s$ and $t$ are the coordinates.

Plugging in the vectors, we get:
$$
\begin{bmatrix}
0\\3
\end{bmatrix}=s\begin{bmatrix}
2\\1
\end{bmatrix}+t\begin{bmatrix}
-1\\1
\end{bmatrix}
$$
Create a system of linear equations:
$$
\begin{align}
2s-t & =0 \\
s+t & =3
\end{align}
$$
Solving the system, we get:
$$
\begin{align}
s=1 &  & t=2
\end{align}
$$

Therefore, the coordinates of $\vec{v}$ is:
$$
[\vec{v}]_{B}=\begin{bmatrix}
1\\2
\end{bmatrix}
$$


---

## Change of Basis
- if a vector $\vec{v}$ in $\mathbb{R}^{n}$ is defined with respect to a basis $B$
- we can **change the basis** to a new basis $B'$ (in the same $\mathbb{R}^{n}$) using the **transition matrix** $P_{B\to B'}$
$$
[\vec{v}]_{B'}=P_{B\to B'}[\vec{v}]_{B}
$$
- the transition matrix $P_{B\to B'}$ acts like a [[3_Functions and Mappings#Matrix as a function|function]] to **convert** the basis the vector is defined with respect to
- the transition matrix is defined as:
$$
P_{B\to B'}=\begin{bmatrix}
[\vec{v_{1}}]_{B'} & [\vec{v_{2}}]_{B'} & \dots & [\vec{v_{n}}]_{B'}
\end{bmatrix}
$$
- where $\vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{n}}$ refer to each basis vectors in the original basis $B$
- **basically**: write each original basis vector with respect to the new basis, each one making up a matrix column

> [!important] Transition matrices are invertible
> $P_{B\to B'}$ and $P_{B'\to B}$ are [[7_Inverses#Matrix Inverse|invertible and inverses]] of one another.
> 
> $\begin{align} (P_{B\to B'})^{-1}=(P_{B'\to B})&&(P_{B'\to B})^{-1}=(P_{B\to B'}) \end{align}$


### Computation
- While we can **solve** for each original basis vector with respect to the new basis, there is a faster way to get to the **transition matrix**
- To compute $P_{B\to B'}$ :
	- form a matrix $[B'|B]$, each column being a basis vector 
	- reduce the matrix to [[3_Reduced REF#Reduced Row Echelon Form|RREF]]
	- the resulting matrix will be the [[1_Matrix#Identity matrices|Identity matrix]] on the left and the transition matrix on the right $[I|P_{B\to B'}]$


> Find the transition matrix from $B\to B'$ where:
> - $B=\left\{ \begin{bmatrix}1\\0\end{bmatrix},\begin{bmatrix}0\\1\end{bmatrix} \right\}$
> - $B'=\left\{ \begin{bmatrix}2\\1\end{bmatrix},\begin{bmatrix}-1\\1\end{bmatrix} \right\}$
> 
> Then write the vector $[\vec{v}]_{B}=\begin{bmatrix}1\\1\end{bmatrix}$ with respect to $B'$

Forming a matrix $[B'|B]$, we get:
$$
\left[  \begin{array}{cc|cc}
2 & -1 & 1 & 0 \\
1 & 1 & 0 & 1
\end{array} \right]\sim\left[  \begin{array}{cc|cc}
1 & 0 & \frac{1}{3} & \frac{1}{3} \\
0 & 1 & -\frac{1}{3} & \frac{2}{3}
\end{array} \right]
$$
Therefore, the transition matrix $P_{B\to B'}$ is:
$$
P_{B\to B'}=\begin{bmatrix}
\frac{1}{3} & \frac{1}{3} \\
-\frac{1}{3} & \frac{2}{3}
\end{bmatrix}
$$
Finally, to write $\vec{v}$ with respect to $B'$ multiply the transition matrix with $[\vec{v}]_{B}$
$$
[\vec{v}]_{B'}=P_{B\to B'}[\vec{v}]_{B}=\begin{bmatrix}
\frac{1}{3} & \frac{1}{3} \\
-\frac{1}{3} & \frac{2}{3}
\end{bmatrix}\begin{bmatrix}
1\\1
\end{bmatrix}=\begin{bmatrix}
\frac{2}{3} \\ \frac{1}{3}
\end{bmatrix}
$$
$$
\therefore [\vec{v}]_{B'}=\begin{bmatrix}
\frac{2}{3} \\ \frac{1}{3}
\end{bmatrix}
$$


---

## Matrix mapping with basis
Also see [[3_Functions and Mappings#Matrix as a function|Matrix Mapping]], [[2_Coordinates#Coordinates|Coordinates]]

**Recall**: the [[3_Functions and Mappings#Standard matrix|standard matrix]] for a mapping is defined to be [[1_Matrix#Row and Column Vectors|column vectors]] of the transformation of each [[3_Functions and Mappings#Standard Basis Vectors|standard basis vectors]].
$$
[L]=\begin{bmatrix}
L(e_{1}) & L(e_{2}) & \dots & L(e_{n})
\end{bmatrix}
$$
While this is done through the standard basis vectors, we can also write a matrix mapping using a [[2_Coordinates#Change of Basis|different basis]].

The matrix mapping with respect to a basis $B$ is denoted:
$$
[L]_{B}=\begin{bmatrix}
[L(\vec{v_{1}})]_{B} & [L(\vec{v_{2}})]_{B} & \dots & [L(\vec{v_{n}})]_{B}
\end{bmatrix}
$$
where $\vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{n}}$ are the basis vectors in $B$


### Formula
- to convert the matrix mapping from basis $S\to B$
- use the [[2_Coordinates#Change of Basis|transition matrix]] $P$ ($P_{B\to S}$)
$$
[L]_{B}=P^{-1}\times[L]_{S}\times P
$$
- since $P^{-1}=P_{S\to B}$, this can also be written as:
$$
[L]_{B}=P_{S\to B}\times [L]_{S}\times P_{B\to S}
$$
