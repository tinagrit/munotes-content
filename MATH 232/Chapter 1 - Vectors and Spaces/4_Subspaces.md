Chapter 1.4 and 1.5


## Closure
A non-empty set $S \subset \mathbb{R}^{n}$ is can be **closed** under an operation if
- the vector remains in the set after the operation

### Closure under addition
A set  $S \subset \mathbb{R}^{n}$ is closed under addition if:
- for all $\vec{u},\vec{v}$ in $S$
- $\vec{u}+\vec{v}$ is also in $S$

Basically: add up any two vectors in the set, if the **sum is also in the set**, then that set is closed under addition.


> Is $S$ closed under addition, given:
> $S=\left\{ \begin{bmatrix}1\\0\\0\end{bmatrix},\begin{bmatrix}0\\1\\0\end{bmatrix} \right\}$

Since there are only two elements, add them up.

$\begin{bmatrix}1\\0\\0\end{bmatrix}+\begin{bmatrix}0\\1\\0\end{bmatrix}=\begin{bmatrix}1\\1\\0\end{bmatrix}$

However, $\begin{bmatrix}1\\1\\0\end{bmatrix} \not\in S$
$\therefore S$ is not closed under addition


> Is $S$ closed under addition, given:
> $S=\left\{ \begin{bmatrix}a\\b\\0\end{bmatrix}\mid a,b \in \mathbb{Z} \right\}$

Since all integers can be produced as a sum of two other integers, $S$ is closed under addition.

> [!note] Integers are closed under addition.


### Closure under scalar multiplication
A set $S \subset \mathbb{R}^{n}$ is closed under scalar multiplication if:
- for all $\vec{u}$ in $S$
- $c\vec{u}$ where $c \in \mathbb{R}$ is also in $S$

Basically: take any vector in the set and multiply it with any real number, if the **product is also in the set**, then that set is closed under scalar multiplication.


> Is $S$ closed under scalar multiplication, given:
> $S=\left\{ \begin{bmatrix}a\\b\\0\end{bmatrix}\mid a,b \in \mathbb{Z} \right\}$

Let $c$ be $1.5$
Pick a random vector from the set, $\begin{bmatrix}2\\5\\0\end{bmatrix}$
Multiply the vector with $c$:

$1.5\times \begin{bmatrix}3\\5\\0\end{bmatrix}=\begin{bmatrix}4.5\\7.5\\0\end{bmatrix}$

Since $S$ only includes integers, this product is not in $S$
$\therefore S$ is not closed under scalar multiplication.


---
## Subspaces
Also see [[1_ Vector Spaces#Vector space|Vector Spaces]]

A non-empty set $S \subset \mathbb{R}^{n}$ is a **subspace** of $\mathbb{R}^{n}$ if it is:
- closed under addition, **and**
- closed under scalar multiplication

> [!note] A [[2_Vector Spans and Basis#Span|span]] of any set of vectors is a valid subspace.

### Subspace examples

> Is $S$ a subspace of $\mathbb{R}^{2}$, given:
>$S=\left\{ \begin{bmatrix}x\\y\end{bmatrix}\mid x>0,y>0 \right\}$

While $S$ is closed under addition, it is not closed under scalar multiplication.

Letting $c$ be a real number $\leq 0$, the negative numbers aren't in the set.

$\therefore S$ is not a subspace of $\mathbb{R}^{2}$


> Is $S$ a subspace of $\mathbb{R}^{2}$, given:
> $S$ is a line through origin

A line through origin can be given by $S=\left\{ t\vec{v} \mid t \in \mathbb{R} \right\}$

- Check for closure under addition
	- Add up two generic vectors
	- $t_{1}\vec{v}+t_{2}\vec{v}$
	- $=(t_{1}+t_{2})\vec{v}$
	- Since $t_{1},t_{2}\in \mathbb{R}$, then $(t_{1}+t_{2})\in \mathbb{R}$
	- $\therefore (t_{1}+t_{2})\vec{v} \in S$ and $S$ is closed under addition
- Check for closure under scalar multiplication
	- Multiply a genetic $c \in \mathbb{R}$ to a generic vector $t\vec{v}$
	- $c\times(t\vec{v})$
	- $=(ct)\vec{v}$
	- Since $c,t\in \mathbb{R}$, then $ct\in \mathbb{R}$
	- $\therefore ct\vec{v} \in S$ and $S$ is closed under scalar multiplication

$\therefore S$ is a subspace of $\mathbb{R}^{2}$


> Is $S$ a subspace of $\mathbb{R}^{3}$, given:
> $S$ is a line passing through $P(1,0,0)$ parallel with $\vec{v}=\begin{bmatrix}0\\1\\1\end{bmatrix}$

$S=\left\{ \begin{bmatrix}1\\0\\0\end{bmatrix}+t\begin{bmatrix}0\\1\\1\end{bmatrix} \mid t\in \mathbb{R} \right\}$
(See [[1_Vectors#Vector equation of lines|line equations]])

$\implies S=\left\{ \begin{bmatrix}1\\0\\0\end{bmatrix}+\begin{bmatrix}0\\t\\t\end{bmatrix}\mid t\in \mathbb{R} \right\}$
$\implies S=\left\{ \begin{bmatrix}1\\t\\t\end{bmatrix} \mid t\in \mathbb{R} \right\}$

Check for closure scalar multiplication
- When $c=0$
- $c\times \begin{bmatrix}1\\t\\t\end{bmatrix}=0\times \begin{bmatrix}1\\t\\t\end{bmatrix}=\begin{bmatrix}0\\0\\0\end{bmatrix}$

However, $\begin{bmatrix}0\\0\\0\end{bmatrix}$ is not in $S$ since the first component will always be $1$.
$\therefore S$ is not a subspace of $\mathbb{R}^{3}$


> Is $S$ a subspace of $\mathbb{R}^{n}$, given:
> $S$ is a plane through origin

$S=\left\{ a\vec{v}+b\vec{u} \mid a,b \in \mathbb{R} \right\}$
(See [[1_Vectors#Vector equation of planes|plane equations]])

- Check for closure under addition
	- Add up two generic linear combination
	- $(a_{1}\vec{v}+b_{1}\vec{u})+(a_{2}\vec{v}+b_{2}\vec{u})$
	- $=(a_{1}\vec{v}+a_{2}\vec{v})+(b_{1}\vec{u}+b_{2}\vec{u})$
	- $=(a_{1}+a_{2})\vec{v}+(b_{1}+b_{2})\vec{u}$
	- Since $a_{1},a_{2} \in \mathbb{R}$ and $b_{1},b_{2} \in \mathbb{R}$ 
	- $(a_{1}\vec{v}+b_{1}\vec{u})+(a_{2}\vec{v}+b_{2}\vec{u}) \in S$ and $S$ is closed under addition
- Check for closure under scalar multiplication
	- Multiply a genetic $c \in \mathbb{R}$ to a generic combination $a\vec{v}+b\vec{u}$
	- $c\times(a\vec{v}+b\vec{u})$
	- $(ca)\vec{v}+(cb)\vec{u}$
	- Since $a,b,c \in \mathbb{R}$, then $ca,cb \in \mathbb{R}$
	- $c(a\vec{v}+b\vec{u}) \in S$ and $S$ is closed under scalar multiplication

$\therefore S$ is a subspace of $\mathbb{R}^{n}$


> Is $S$ a subspace of $\mathbb{R}^{n}$, given:
> $S=\left\{ \mathbf{0} \right\}$

- Check for closure under addition
	- $\mathbf{0}+\mathbf{0}$
	- $=\mathbf{0}$
	- $\mathbf{0} \in S$ and $S$ is closed under addition
- Check for closure under scalar multiplication
	- Multiply a genetic $c \in \mathbb{R}$ to the only element $\mathbf{0}$
	- $c\times\mathbf{0}$
	- $=\mathbf{0}$
	- $\mathbf{0} \in S$ and $S$ is closed under scalar multiplication

$\therefore S$ is a subspace of $\mathbb{R}^{n}$

> [!important] The $\{\mathbf{0}\}$ is a subspace of any vector space. This is called a trivial subspace.


> Is $S$ a subspace of $\mathbb{R}^{n}$, given:
> $S=\mathbb{R}^{n}$

- Check for closure under addition
	- Let $a,b \in S$ be generic elements
	- $a+b$ is also $\in S$
	- $a+b \in S$ and $S$ is closed under addition
- Check for closure under scalar multiplication
	- Multiply a genetic $c \in \mathbb{R}$ to a generic element $a\in S$
	- $c\times a$ is also $\in S$
	- $ca\in S$ and $S$ is closed under scalar multiplication

$\therefore S$ is a subspace of $\mathbb{R}^{n}$


### Possible subspaces

- In $\mathbb{R}^{2}$ the possible subspaces include:
	- the trivial subspaces
	- lines through the origin
	- $\mathbb{R}^{2}$ itself
- In $\mathbb{R}^{3}$ the possible subspaces include:
	- the trivial subspaces
	- lines through the origin
	- planes through the origin
	- $\mathbb{R}^{3}$ itself


### Basis of subspaces
*see* [[2_Vector Spans and Basis#Basis|Basis]]

A non-empty set of vectors is a **basis for a subspace** if:
- it [[2_Vector Spans and Basis#Span|spans]] the subspace
- it is [[2_Vector Spans and Basis#Linear independence|linearly independent]]


### Hyperplanes
see [[1_Vectors#Vector equation of planes|plane equations]]

A **hyperplane** of $\mathbb{R}^{n}$ is:
- a subspace of points orthogonal to a vector
- a flat surface that separates a space into two parts

A hyperplane of $\mathbb{R}^{2}$ is a **line**
A hyperplane of $\mathbb{R}^{3}$ is a **plane**


