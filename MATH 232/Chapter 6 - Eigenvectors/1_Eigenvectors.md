Chapter 6.1


## Eigenvectors
- vector that **stays on the span** after a linear transformation
	- most vectors are "knocked off" its span after being transformed
	- eigenvectors stays on its span like a scalar multiplication

For example, stretching the vectors $\vec{v_{1}}$ and $\vec{v_{2}}$ horizontally by 2 times using the [[4_Transformations#Geometrical Transformations|transformation matrix]] $A=\begin{bmatrix}2&0\\0&1\end{bmatrix}$

| Before stretching                 | After stretching                  |
| --------------------------------- | --------------------------------- |
| ![[IMG_4DC0C505B05B-1.jpeg\|300]] | ![[IMG_CEBF052A4E2F-1.jpeg\|400]] |

Notice that the vector $\vec{v_{1}}$ is away from its own span, but $\vec{v_{2}}$ stays on it. This makes $\vec{v_{2}}$ an **eigenvector**.

### Eigenvalues
- the amount that a vector **gets scalar multiplied by** instead of transformed by, denoted $\lambda$ (*pronounced lambda*)
	- can be negative; vector flipped

Using the example above, both $\vec{v_{1}}$ and $\vec{v_{2}}$ were transformed with the matrix $A$. But, notice that the transformation that is done on $\vec{v_{2}}$ is **identical** to simply **scalar multiplying** it by 2.
- This makes 2 the **eigenvalue**.

Multiplying an eigenvector by the eigenvalue should produce **the same result** as transforming it normally.
$$
A \vec{v} = \lambda  \vec{v}
$$
where: 
- $A$ is a transformation matrix
- $\lambda$ is the eigenvector (a scalar quantity)

### Dominant eigenvalue
- if **there exists** multiple eigenvalues, the **dominant** eigenvalue is the one with the highest absolute value
- if there are multiple eigenvalues with the **same absolute values**, such as $\lambda=3,-3$, then there is **no dominant** eigenvalue


---

## Calculations

### Multiplication hack
- multiplying matrices is **tedious**, especially if it has to multiply by itself multiple times. For example $A^{15}\vec{v}$ means to apply the transformation to $\vec{v}$ 15 times.
- however, if $\vec{v}$ is an **eigenvector**, we can use $\lambda^{15}\vec{v}$ instead.
	- power of a real number is **much easier** than power of a matrix

### Triangular matrices
For any [[1_Matrix#Triangular matrices|Triangular matrices]], the eigenvalues are the **entires on the main diagonal**.

For example, finding the eigenvalues of $A$:
$$
A=\begin{bmatrix}
\boxed{ 8 } & 0 & 0 \\
3 & \boxed{ 6 } & 0 \\
2 & 9 & \boxed{ 9 }
\end{bmatrix}
$$
It follows that $\lambda=8,6,9$


---

## Characteristic equation

Deriving the formula using the equation:
$$
A \vec{v} = \lambda  \vec{v}
$$

The right side scales the vector by $\lambda$ (a scalar quantity), in other words:
$$
\lambda   \vec{v}=\begin{bmatrix}
\lambda & 0 \\
0 & \lambda
\end{bmatrix} \vec{v}
$$
Factor out the $\lambda$
$$
\lambda   \vec{v}=\lambda \begin{bmatrix}
1 & 0 \\
0 & 1
 \end{bmatrix}\vec{v}
$$
The matrix on the right is the identity matrix
$$A   \vec{v}=(\lambda I)\vec{v}$$
Move everything to the right and factor out $\vec{v}$
$$
\vec{0}=(\lambda I)\vec{v}-A\vec{v}
$$
$$
\vec{0}=(\lambda I-A)\vec{v}
$$
This is a [[1_Augmented Matrix#Homogeneous Systems|homogeneous system]]. The eigenvalue exists if there is a **non-trivial** ($\vec{v}\neq \vec{0}$) solution. 
- The theorem from homogeneous systems state that if there is a **nontrivial** solution, then there are **infinitely as many** solutions
- Since there are infinitely as many solutions, there **is a free variable** in the matrix $(\lambda I-A)$
- Having a free variable implies that the matrix is **not full rank**, and that the **determinant is 0**

Therefore, if there exists $\lambda$ such that:
$$
\det(\lambda I-A)=0
$$
then $\lambda$ is the eigenvalue of the matrix.

This is called the **characteristic equation** of $A$.

The **characteristic polynomial** $p(\lambda)$ of $A$ is defined as $p(\lambda)=\det(\lambda I-A)$

Therefore, to find any eigenvalues of a matrix, we set:
$$
p(\lambda)=0
$$
and solve for $\lambda$.

> [!important] Symmetric matrices ($A=A^{T}$) always have real eigenvalues.


### Finding eigenvalues and eigenvectors

> Find all eigen**values** of $A=\begin{bmatrix}0&6\\-1&5\end{bmatrix}$

Finding $\lambda I-A$:
$$
\lambda \begin{bmatrix}
1&0\\0&1
\end{bmatrix}-\begin{bmatrix}
0&6\\-1&5
\end{bmatrix}=\begin{bmatrix}
\lambda-0&-6\\1&\lambda-5
\end{bmatrix}
$$
Finding $\det(\lambda I-A)$:
$$
\begin{vmatrix}
\lambda&-6\\1&\lambda-5
\end{vmatrix}=(\lambda)(\lambda-5)-(1)(-6)
$$
$$
=\lambda^{2}-5\lambda+6=(\lambda-3)(\lambda-2)
$$
Setting $\det(\lambda I-A)=0$
$$
(\lambda-3)(\lambda-2)=0\implies\lambda=2,3
$$

$\therefore$ The eigenvalues are 2 and 3


> Find all eigen**vectors** of $A=\begin{bmatrix}0&6\\-1&5\end{bmatrix}$ associated with $\lambda=2$

Using the equation:
$$
\vec{0}=(\lambda I-A)\vec{v}
$$
Substitute $\lambda$ and $A$:
$$
\vec{0}=\left(\begin{bmatrix}
2&0\\0&2
\end{bmatrix}-\begin{bmatrix}
0&6\\-1&5
\end{bmatrix}\right)\vec{v}
$$
$$
\vec{0}=\begin{bmatrix}
2&-6\\1&-3
\end{bmatrix}\vec{v}
$$
Solve the homogeneous system:
$$\left[  
\begin{array}{@{}cc|c@{}}
2&-6&0 \\
1&-3&0
\end{array}\right] \sim \left[ \begin{array}{@{}cc|c@{}}
1&-3&0 \\
0&0&0
\end{array} \right] 
$$
$$\implies    \vec{v}=\begin{bmatrix}3\\1\end{bmatrix}t$$
This tells us that $\begin{bmatrix}3\\1\end{bmatrix}$ is an eigenvector, and any scales of $\begin{bmatrix}3\\1\end{bmatrix}$ are also eigenvectors.

$\therefore$ The eigenvectors of $A$ associated with $\lambda=2$ is $\text{Span}\left\{ \begin{bmatrix}3\\1\end{bmatrix} \right\}$


> Find all eigen**vectors** of $A=\begin{bmatrix}0&6\\-1&5\end{bmatrix}$ associated with $\lambda=3$

Using the equation:
$$
\vec{0}=(\lambda I-A)\vec{v}
$$
Substitute $\lambda$ and $A$:
$$
\vec{0}=\left(\begin{bmatrix}
3&0\\0&3
\end{bmatrix}-\begin{bmatrix}
0&6\\-1&5
\end{bmatrix}\right)\vec{v}
$$
$$
\vec{0}=\begin{bmatrix}
3&-6\\1&-2
\end{bmatrix}\vec{v}
$$
Solve the homogeneous system:
$$
\left[  
\begin{array}{@{}cc|c@{}}
3&-6&0 \\
1&-2&0
\end{array}\right] \sim \left[ \begin{array}{@{}cc|c@{}}
1&-2&0 \\
0&0&0
\end{array} \right] 
$$
$$
\implies    \vec{v}=\begin{bmatrix}2\\1\end{bmatrix}t
$$
$\therefore$ The eigenvectors of $A$ associated with $\lambda=3$ is $\text{Span}\left\{ \begin{bmatrix}2\\1\end{bmatrix} \right\}$


### Eigenspace
- the [[3_Reduced REF#Solution Set|solution space]] for **all eigenvectors** of the transformation

With the examples above, we've concluded that the eigenspace includes:
- $\lambda=2:\text{Span}\left\{ \begin{bmatrix}3\\1\end{bmatrix} \right\}$
- $\lambda=3:\text{Span}\left\{ \begin{bmatrix}2\\1\end{bmatrix} \right\}$


### Complex eigenvalues
See [[1_Complex Numbers#Complex Numbers|Complex Numbers]]
- eigenvalues can be **real** or [[1_Complex Numbers#Complex Numbers|complex]]

For example, while finding the eigenvalues using the [[#Characteristic equation]], if we end up with:
$$
(\lambda-3)(\lambda^{2}+4)=0
$$
Then, the eigenvalues are:
$$
\begin{align}
\lambda-3 & =0 & \lambda^{2}+4 & =0 \\
\lambda & =3 & \lambda^{2} & =-4 \\
 &  & \lambda & =\pm 2i
\end{align}
$$
$$\lambda=3,2i,-2i$$

Note that the [[#Dominant eigenvalue]] is still $\lambda=3$.


---

## Multiplicity

### Algebraic multiplicity
While finding the eigenvalues using the [[#Characteristic equation]], if we end up with:
$$
(\lambda-1)(\lambda-1)=0
$$
There is only 1 unique eigenvalue, which is $1$. But since $1$ is multiplied twice in the equation, it has a **algebraic multiplicity** of **2**.

The algebraic multiplicity describes **how many times** each **distinct** eigenvalue gets multiplied in the characteristic equation.

For example, if we end up with:
$$ (\lambda-1)(\lambda-1)(\lambda-1)(\lambda+2)(\lambda+2)=0 $$
- the algebraic multiplicity of $\lambda=1$ is 3
- the algebraic multiplicity of $\lambda=-2$ is 2

> [!important] An $n\times n$ matrix has $n$ eigenvalues, but we don't know how many **distinct** eigenvalues there are.

### Geometric multiplicity
- the [[1_ Vector Spaces#Space Dimensions|dimensions]] of each eigenspace

For example, when finding all eigenvectors associated with a $\lambda$, if we end up with:
$$\vec{v}=\begin{bmatrix}3\\0\\1\end{bmatrix}t+\begin{bmatrix}2\\2\\5\end{bmatrix}s$$
Since there are 2 linearly independent vectors in the span, then the **geometric multiplicity** of this $\lambda$ is **2**.


---

## The Power Method
- is used to **approximate** the [[#Dominant eigenvalue]]

Formula to use:
$$
\begin{align}
x_{n}=\dfrac{Ax_{n-1}}{\lVert Ax_{n-1} \rVert} &  & \lambda\approx(Ax_{n})\cdot x_{n}
\end{align}
$$

In this example, we will find the dominant eigenvalue of $A=\begin{bmatrix}3&2\\2&3\end{bmatrix}$

1. Choose an arbitrary value for $x_{0}$ (initial vector) that has a length of $1$.
	- Let $x_{0}=\begin{bmatrix}1\\0\end{bmatrix}$

2. For each iteration, apply $x_{n}=\dfrac{Ax_{n-1}}{\lVert Ax_{n-1} \rVert}$. The more iteration, the more precise.
	- Iteration 0: $x_{0}=\begin{bmatrix}1\\0\end{bmatrix}$
	- Iteration 1: $x_{1}=\dfrac{\begin{bmatrix}3&2\\2&3\end{bmatrix}\begin{bmatrix}1\\0\end{bmatrix}}{\lVert \begin{bmatrix}3&2\\2&3\end{bmatrix}\begin{bmatrix}1\\0\end{bmatrix} \rVert}=\dfrac{\begin{bmatrix}3\\2\end{bmatrix}}{\sqrt{ 13 }}\approx \begin{bmatrix}0.83205\\0.55470\end{bmatrix}$
	- Iteration 2: $x_{2}=\dfrac{\begin{bmatrix}3&2\\2&3\end{bmatrix}\begin{bmatrix}0.83205\\0.55470\end{bmatrix}}{\lVert \begin{bmatrix}3&2\\2&3\end{bmatrix}\begin{bmatrix}0.83205\\0.55470\end{bmatrix} \rVert}\approx \begin{bmatrix}0.73480\\0.67828\end{bmatrix}$
	- If we stop at $x_{2}$, calculate $Ax_{2}$ to apply the formula
	  $Ax_{2}=\begin{bmatrix}3&2\\2&3\end{bmatrix}\begin{bmatrix}0.73480\\0.67828\end{bmatrix}\approx \begin{bmatrix}3.56097\\3.50445\end{bmatrix}$

3. Apply formula $\lambda\approx(Ax_{n})\cdot x_{n}$
	- $\lambda \approx (Ax_{2})\cdot x_{2}=\begin{bmatrix}3.56097\\3.50445\end{bmatrix}\cdot\begin{bmatrix}0.73480\\0.67828\end{bmatrix}$
	- Performing dot product, we get:
	- $\lambda \approx 4.99361$

$\therefore$ Estimating the dominant eigenvalue with $n=2$, we get $\lambda \approx 4.99361\approx 5$.

If we find the eigenvalues the normal way, we will get the dominant value $\lambda=5$.

