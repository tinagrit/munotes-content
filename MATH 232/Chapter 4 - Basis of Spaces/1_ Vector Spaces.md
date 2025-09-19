Chapter 4.2 and 4.3


## Vector space
Also see [[4_Subspaces#Subspaces|Subspaces]]

- **collection** of things
- [[1_Vectors#Vectors|vector]] is an **item** inside a vector space
- items are [[4_Subspaces#Closure|closed]] under addition and scalar multiplication

If:
- $S$ is a **subset** of a **vector space** $V$, and
- $S$ is also a **vector space**
Then:
- $S$ is a [[4_Subspaces#Subspaces|subspace]] of $V$

### Vector space rules
For any $\vec{x},\vec{y},\vec{z}\in V$ (a vector space), and for any $s,t\in \mathbb{R}$:
1. $\vec{x}+\vec{y} \in V$
   [[4_Subspaces#Closure under addition|Closure under addition]]
2. $\vec{x}+\vec{y}=\vec{y}+\vec{x}$
   Commutative under addition
3. $(\vec{x}+\vec{y})+\vec{z}=\vec{x}+(\vec{y}+\vec{z})$
   Associative under addition
4. $\exists \text{ } \mathbf{ 0}\in V$
   The zero vector exists
5. $\forall  \vec{x}\in V, \exists -\vec{x}\in V \mid \vec{x}+(-\vec{x})=\mathbf{0}$
   For any vector, there exists the opposite vector
6. $s\vec{x}\in V$
   [[4_Subspaces#Closure under scalar multiplication|Closure under scalar multiplication]]
7. $s(t\vec{x})=(st)\vec{x}$
   Associative under scalar multiplication
8. $(s+t)\vec{x}=s\vec{x}+t\vec{x}$
   Distributive property of vectors
9. $s(\vec{x}+\vec{y})=s\vec{x}+s\vec{y}$
   Distributive property of scalar quantities
10. $1\vec{x}=\vec{x}$
    Same vector is returned if multiplied by 1


---
## Unique Representation Theorem

Let a vector space $V=\text{span }B$,
all vectors in $V$ can be represented **uniquely** as a linear combination of the vectors in $B$
- *if and only if* $B$ is [[2_Vector Spans and Basis#Linear independence|linearly independent]]

Revisit:
- [[3_Functions and Mappings#Standard Basis Vectors|Standard Basis Vectors]]
- [[3_Functions and Mappings#Standard Basis Matrices|Standard Basis Matrices]]

### Basis
- are [[2_Vector Spans and Basis#Linear independence|linearly independent]]
- can uniquely span any vectors in the same space


> Express $\vec{v}$ using the given basis vectors
> $\vec{v}=\begin{bmatrix}1\\2\\3\end{bmatrix}$, using $b_{1}=\begin{bmatrix}1\\1\\0\end{bmatrix},b_{2}=\begin{bmatrix}1\\0\\1\end{bmatrix},b_{3}=\begin{bmatrix}0\\1\\1\end{bmatrix}$

Since $b_{1},b_{2},b_{3}$ are linearly independent, the vector $\vec{v}$ can be represented using the basis vectors.

Set up an augmented matrix by having the basis vectors on the left, and $\vec{v}$ on the right:
$$
\begin{bmatrix}
1 & 1 & 0 & 1 \\
1 & 0 & 1 & 2 \\
0 & 1 & 1 & 3
\end{bmatrix}\sim \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 1 \\
0 & 0 & 1 & 2
\end{bmatrix}
$$
Therefore, $\vec{v}=b_{2}+2b_{3}$


> Find the basis matrices for the subspace:
> $S=\left\{ \begin{bmatrix}a&b\\c&d\end{bmatrix} \mid a+b=d \right\}\subset M_{2\times 2}$

Since $c$ does not depend on any other variables, it is free to be any value. From that, we know that $\begin{bmatrix}0&0\\1&0\end{bmatrix}$ is a basis.

For $a$ and $b$ however, we set up matrices where $a=1,b=0$ and $a=0,b=1$:
- $a=1,b=0$
	- $\begin{bmatrix}1&0\\0&d\end{bmatrix}$
	- Since $a+b=d$, $1+0=d$, $d=1$
	- $\begin{bmatrix}1&0\\0&1\end{bmatrix}$ is a basis
- $a=0,b=1$
	- $\begin{bmatrix}0&1\\0&d\end{bmatrix}$
	- Since $a+b=d$, $0+1=d$, $d=1$
	- $\begin{bmatrix}0&1\\0&1\end{bmatrix}$ is a basis

The basis of $S$ is $\left\{ \begin{bmatrix}0&0\\1&0\end{bmatrix},\begin{bmatrix}1&0\\0&1\end{bmatrix},\begin{bmatrix}0&1\\0&1\end{bmatrix} \right\}$


### Space Dimensions
- Revisit: [[3_Reduced REF#Spans and Dimensions|Spans and Dimensions]]
- Number of [[2_Vector Spans and Basis#Linear independence|linearly independent]] basis in the set that spans a space


> Determine the dimension of a subspace $W=\text{span }S$ spanned by:
> $S=\left\{ \begin{bmatrix}1&1\\-1&1\end{bmatrix},\begin{bmatrix}0&1\\3&-1\end{bmatrix},\begin{bmatrix}1&-1\\2&-3\end{bmatrix},\begin{bmatrix}2&1\\4&-3\end{bmatrix} \right\}$

Determine the number of linearly independent matrices in $S$:
$$
t_{1}\begin{bmatrix}1&1\\-1&1\end{bmatrix}+t_{2}\begin{bmatrix}0&1\\3&-1\end{bmatrix}+t_{3}\begin{bmatrix}1&-1\\2&-3\end{bmatrix}+t_{4}\begin{bmatrix}2&1\\4&-3\end{bmatrix}=\begin{bmatrix}
0 & 0\\0 & 0
\end{bmatrix}
$$
If there is only one solution (trivial), then $S$ is linearly independent.
$$
\begin{bmatrix}
t_{1}+t_{3}+2t_{4} & t_{1}+t_{2}-t_{3}+t_{4} \\
-t_{1}+3t_{2}+2t_{3}+4t_{4} & t_{1}-t_{2}-3t_{3}-3t_{4}
\end{bmatrix}=\begin{bmatrix}
0 & 0\\0 & 0
\end{bmatrix}
$$
Using each component in the matrix, set up a system of linear equations:
$$
\begin{align}
t_{1}+t_{3}+2t_{4} & =0 \\
t_{1}+t_{2}-t_{3}+t_{4} & =0 \\
-t_{1}+3t_{2}+2t_{3}+4t_{4} & =0 \\
t_{1}-t_{2}-3t_{3}-3t_{4} & =0
\end{align}
$$
Set up an augmented matrix and reduce it to [[3_Reduced REF#Reduced Row Echelon Form|RREF]]:
$$
\begin{bmatrix}
1 & 0 & 1 & 2 & 0 \\
1 & 1 & -1 & 1 & 0 \\
-1 & 3 & 2 & 4 & 0 \\
1 & -1 & -3 & -3 & 0
\end{bmatrix}\sim \begin{bmatrix}
1 & 0 & 0 & 1 & 0 \\
0 & 1 & 0 & 1 & 0 \\
0 & 0 & 1 & 1 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
Since the fourth matrix is free, it can be written as $M_{4}=M_{1}+M_{2}+M_{3}$

From $W=\text{span }S$, the basis for this subspace is $\left\{ M_{1},M_{2},M_{3} \right\}$
Therefore, $\text{dim }W=3$


---
## Basis Reduction Theorem
- subspace defined by $V=\text{span }S$
	- where $S=\left\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{n}} \right\}$
	- the **basis** of the subspace is the **independent vectors** in $S$
	- (in other words) Basis of $V$ is a **subset** of $S$
- if we **remove all dependent** vectors from $S$, then $S$ is the **minimum spanning set**


---
## Basis Extension Theorem
- an $a$-dimensional vector space **needs** $a$ basis vectors
- if:
	- a vector space $V$ has $n$ dimensions, and
	- $B=\left\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{k}} \right\}$ is linearly independent with $k<n$ (not enough vectors to be basis)
- then:
	- there exists $\vec{w}_{k+1},\vec{w}_{k+2},\dots,\vec{w}_{n}$
	- such that $B$ extended with the $\vec{w}$ vectors be extended to be basis for $V$


> Determine a basis for the plane $x_{1}-2x_{2}+x_{3}=0$, then extend that basis to a basis for $\mathbb{R}^{3}$

Notice that a [[3_Reduced REF#Spans and Dimensions|plane's dimension]] is 2, therefore, we need to add $3-2=1$ more basis vector to make up $\mathbb{R}^{3}$

Assuming that $\vec{v_{1}},\vec{v_{2}}$ span the plane, the basis for $\mathbb{R}^{3}$ is:
$\left\{ \vec{v_{1}},\vec{v_{2}},n \right\}$
where $n$ is not in the span of $\vec{v_{1}},\vec{v_{2}}$

Picking $\vec{v_{1}},\vec{v_{2}}$, they can be **any 2 independent** vectors in the plane:
$$
\vec{v_{1}}=\begin{bmatrix}
1\\1\\1
\end{bmatrix},\vec{v_{2}}=\begin{bmatrix}
2\\1\\0
\end{bmatrix}
$$
Now, $n$ can be any vector that is not on the plane. The **normal** vector is definitely not on the plane.
$$
n=\begin{bmatrix}
1\\-2\\1
\end{bmatrix}
$$
Therefore, the following basis set spans $\mathbb{R}^{3}$:
$$
\left\{ \begin{bmatrix}
1\\1\\1
\end{bmatrix},\begin{bmatrix}
2\\1\\0
\end{bmatrix},\begin{bmatrix}
1\\-2\\1
\end{bmatrix} \right\} 
$$
