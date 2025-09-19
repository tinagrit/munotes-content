Chapter 1.2


## Span
Also see [[1_Matrix#Matrix Spans and Basis|Matrix Spans and Basis]]

- a **span** is a set of *every possible* [[1_Vectors#Linear combinations|linear combinations]] of vectors
- for example, a span of $\vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{n}}$ is:
	- $\{ x \mid x=t_{1}\vec{v}_{1}+t_{2}\vec{v}_{2}+\dots+t_{n}\vec{v_{n}}$  , $t_{1},t_{2},\dots,t_{n} \in \mathbb{R}$ $\}$
	- multiply a **constant** to each vector
	- also denoted by $\text{span}\left\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{n}} \right\}$

### Span examples

> What is the set $W=\text{span}\left\{ \begin{bmatrix}-1\\4\end{bmatrix} \right\}$

$W = \left\{ t\begin{bmatrix}-1\\4\end{bmatrix} \mid t \in \mathbb{R} \right\}$

Recall that a [[1_Vectors#Vector equation of lines|line equation]] is a set of a *vector multiplied by a constant*.
With only **one vector** in the linear combination, **this is a line**.

$\therefore W$ is a line through $\begin{bmatrix}-1\\4\end{bmatrix}$ and origin.

> What is the set $W=\text{span}\left\{ \begin{bmatrix}1\\0\\5\end{bmatrix},\begin{bmatrix}0\\1\\5\end{bmatrix} \right\}$

$W=\left\{ t_{1}\begin{bmatrix}1\\0\\5\end{bmatrix}+t_{2}\begin{bmatrix}0\\1\\5\end{bmatrix} \mid t_{1},t_{2} \in \mathbb{R} \right\}$

Recall that a [[1_Vectors#Vector equation of planes|plane]] through the origin is a set of linear combinations of **two vectors** in $\mathbb{R}^{3}$.

$\therefore W$ is a plane through the origin.

Note: $W$ is ***not a line*** since one vector is not a scalar multiplication of another.
- $\begin{bmatrix}1\\0\\5\end{bmatrix} \not\in \left\{ t\begin{bmatrix}0\\1\\5\end{bmatrix} \mid t \in \mathbb{R} \right\}$
- $\begin{bmatrix}0\\1\\5\end{bmatrix} \not\in \left\{ t\begin{bmatrix}1\\0\\5\end{bmatrix} \mid t \in \mathbb{R} \right\}$

### Entire cross products
To create a span as a set with all of 
- $\mathbb{R}^{2}$ points:
	- Create a span with $\vec{v_{1}}=\begin{bmatrix}1\\0\end{bmatrix}$ and $\vec{v_{2}}=\begin{bmatrix}0\\1\end{bmatrix}$
	- The linear combination of these vectors:
		- $\left\{ a\begin{bmatrix}1\\0\end{bmatrix} +b\begin{bmatrix}0\\1\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
		- $=\left\{ \begin{bmatrix}1a+0b\\0a+1b\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
		- $=\left\{ \begin{bmatrix}a\\b\end{bmatrix} | a,b \in R \right\}$
	- This includes **all points** in $\mathbb{R}^{2}$
- $\mathbb{R}^{3}$ points:
	- Create a span with $\vec{v_{1}}=\begin{bmatrix}1\\0\\0\end{bmatrix}$, $\vec{v_{2}}=\begin{bmatrix}0\\1\\0\end{bmatrix}$ and $\vec{v_{3}}=\begin{bmatrix}0\\0\\1\end{bmatrix}$
	- The linear combination of these vectors:
		- $\left\{ a\begin{bmatrix}1\\0\\0\end{bmatrix} + b\begin{bmatrix}0\\1\\0\end{bmatrix} + c\begin{bmatrix}0\\0\\1\end{bmatrix} \mid a,b,c \in \mathbb{R} \right\}$
		- $=\left\{ \begin{bmatrix}1a+0b+0c\\0a+1b+0c\\0a+0b+1c\end{bmatrix} \mid a,b,c \in \mathbb{R} \right\}$
		- $=\left\{ \begin{bmatrix}a\\b\\c\end{bmatrix} \mid a,b,c \in \mathbb{R} \right\}$
	- This includes **all points** in $\mathbb{R}^{3}$
- x-y plane in $\mathbb{R}^{3}$
	- Create a span with $\vec{v_{1}}=\begin{bmatrix}1\\0\\0\end{bmatrix}$ and $\vec{v_{2}}=\begin{bmatrix}0\\1\\0\end{bmatrix}$
	- The linear combination of these vectors:
		- $\left\{ a\begin{bmatrix}1\\0\\0\end{bmatrix} +b\begin{bmatrix}0\\1\\0\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
		- $=\left\{ \begin{bmatrix}1a+0b\\0a+1b\\0a+0b\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
		- $=\left\{ \begin{bmatrix}a\\b\\0\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
	- This is the **entire x-y plane** in $\mathbb{R}^{3}$

---
## Linear independence

A set of vectors is **linearly independent** if
- its linear combination is $\mathbf{0}$ **if and only if** all of the scalar constants are 0
- if there exists a selection of constants that can produce $=\mathbf{0}$, the vectors are **linearly dependent**

Set $\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{k}} \}$ is linearly independent if:
- $c_{1}\vec{v_{1}}+c_{2}\vec{v_{2}}+\dots+c_{3}\vec{v_{3}}=\mathbf{0}$
- if and only if $\forall c,c_{n}=0$ (all $c$'s are 0)

To determine if a set of vectors is linearly independent:
- create a [[#Span|span]] of all vectors
- set the span equal to $\mathbf{0}$
- determine if the only possible solution is for all constants to be 0

See an easier way to solve this by [[3_Reduced REF#Applying RREF|Applying Row-Echelon Form]]

### Theorem
A set $S$ with 2 or more vectors is ***not* linearly independent** if and only if:
- at least one of the vectors in $S$ is a [[1_Vectors#Linear combinations|linear combination]] of other vectors in $S$ 

#### Corollary
- $S=\left\{ \vec{v_{1}},\vec{v_{2}} \right\}$ is ***not* linearly independent** if and only if:
	- $\vec{v_{1}}$ and $\vec{v_{2}}$ are parallel
- $S=\left\{ \vec{v_{1}},\vec{v_{2}},\vec{v_{3}} \right\}$ is ***not* linearly independent** if and only if:
	- $\vec{v_{1}},\vec{v_{2}},\vec{v_{3}}$ all lie on the same [[1_Vectors#Vector equation of planes|plane]]


### Independence example

> Is the set $S$ linearly independent given:
> $S=\left\{ \begin{bmatrix}1\\0\\0\end{bmatrix},\begin{bmatrix}0\\0\\1\end{bmatrix} \right\}$

A [[#Span|span]] of $S$: $\text{span}\left\{ S \right\}=\left\{ \begin{bmatrix}a\\0\\b\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
Is there a way to produce $\begin{bmatrix}0\\0\\0\end{bmatrix}$ without both $a$ and $b$ being 0?
No, the only way to produce $\mathbf{0}$ is for both $a$ and $b$ to be 0.
$\therefore S$ is linearly independent.

> Is the set $S$ linearly independent given:
> $S=\left\{ \begin{bmatrix}0\\1\\0\end{bmatrix},\begin{bmatrix}0\\3\\0\end{bmatrix} \right\}$

$\text{span}\left\{ S \right\}=\left\{ \begin{bmatrix}0\\a+3b\\0\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
Is there a value for $a$ and $b$ that makes the second dimension 0 without them both being 0?

Yes, if $a=-3$ and $b=1$ $\implies (-3)+3(1)=0$

$\therefore S$ is not linearly independent

> Is the set $S$ linearly independent given:
> $S=\left\{ \vec{u} \right\}$

$\text{span}\left\{ S \right\}$
- $=\left\{ a\vec{u} \mid a\in \mathbb{R} \right\}$
- $=\left\{ \begin{bmatrix}au_{1}\\au_{2}\\\dots\\au_{k}\end{bmatrix} \mid a \in \mathbb{R}  \right\}$

From this, unless $\vec{u}=\mathbf{0}$ (all dimensions are 0), $a$ needs to be 0 for all dimensions to be 0.

$\therefore \vec{u}$ is linearly independent *unless* $\vec{u}=\mathbf{0}$

> [!note] $\{\mathbf{0}\}$ is not linearly independent


> Is the set $S$ linearly independent given:
> $S=\left\{ \vec{u},\vec{v},\mathbf{0} \right\}$

$\text{span}\{S\}=\left\{ a\vec{u}+b\vec{v}+c\mathbf{0} \mid a,b,c \in \mathbb{R} \right\}$

To produce $\mathbf{0}$, $a$ and $b$ need to be 0 but $c$ can be anything (since it is multiplied by $\mathbf{0}$). There is infinitely as many ways to produce $\mathbf{0}$

$\therefore S$ is not linearly independent

> Is the set $S$ linearly independent given:
> $S=\left\{ \begin{bmatrix}1\\0\\1\end{bmatrix},\begin{bmatrix}-1\\0\\1\end{bmatrix},\begin{bmatrix}2\\0\\2\end{bmatrix} \right\}$

Using the [[#Theorem]]:
- $2\times \begin{bmatrix}1\\0\\1\end{bmatrix}=\begin{bmatrix}2\\0\\2\end{bmatrix}$ 
- This means that $\begin{bmatrix}2\\0\\2\end{bmatrix}$ is a **linear combination** of $\begin{bmatrix}1\\0\\1\end{bmatrix}$
- This implies that $S$ is not linearly independent

$\therefore S$ is not linearly independent

---

## Basis
- a set of vectors $S=\left\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{k}} \right\}$ is a **basis** for $\mathbb{R}^{n}$ if:
	- $\text{span}\left\{ S \right\}=\mathbb{R}^{n}$
	- $S$ is linearly [[#Linear independence|independent]]

Also see: [[4_Subspaces#Basis of subspaces|Basis of subspaces]]

See an easier way to solve this by [[3_Reduced REF#Applying RREF|Applying Row-Echelon Form]]

### Basis examples

> Is the set $S$ a basis for $\mathbb{R}^{2}$ given:
> $S=\left\{ \begin{bmatrix}-1\\2\end{bmatrix},\begin{bmatrix}1\\5\end{bmatrix} \right\}$

Show that:
- **Part 1**: $\text{span}\{S\}=\mathbb{R}^{2}$
- **Part 2**: $S$ is linearly independent

#### Part 1
$\text{span}\{S\}$
- $=\left\{ a\begin{bmatrix}-1\\2\end{bmatrix}+b\begin{bmatrix}1\\5\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
- $=\left\{ \begin{bmatrix}-a+b\\2a+5b\end{bmatrix} \mid a,b \in\mathbb{R} \right\}$

This span has 2 degrees of freedom and spans across all points in $\mathbb{R}^{2}$
$\therefore \text{span}\{S\}=\mathbb{R}^{2}$

#### Part 2
Set $\begin{bmatrix}-a+b\\2a+5b\end{bmatrix}=\begin{bmatrix}0\\0\end{bmatrix}$

- $-a+b=0$
	- $\implies a=b$
- $2a+5b=0$
	- $2a+5a=0$ (using $a=b$)
		- $\implies 7a=0 \implies a=0$
	- $2b+5b=0$ (using $a=b$)
		- $\implies 7b=0 \implies b=0$

Since the only solution is $a=0$ and $b=0$,
$\therefore S$ is linearly independent

Since $\text{span}\left\{ S \right\}=\mathbb{R}^{2}$ and $S$ is linearly independent
$\therefore S$ **is a basis** for $\mathbb{R}^{2}$


