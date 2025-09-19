Chapter 1.1


## Scalars and Vectors

- $\mathbb{R}^{2}$ is the set of **all pairs of real numbers**, a 2D space
	- is a [cross product](https://munotes.tinagrit.com/MACM101/unit-5-functions-and-relations/week-11-functions/1_relations.html#Cartesian_product) of $\mathbb{R}\times \mathbb{R}$
	- for example, some pairs of integers include:
		- $\{ (1,1),(1,2),\dots,(2,1),(2,2),\dots \}$
- $\mathbb{R}^{3}$ is the set of **all triples of real numbers**, a 3D space
	- is a *cross product* of $\mathbb{R}\times \mathbb{R}\times \mathbb{R}$
	- for example, some triples of integers include:
		- $\{ (1,1,1),(1,1,2),\dots,(1,2,1),(1,2,2),\dots\}$
- $\mathbb{R}^{n}$ is the set of all $n$-sized tuples of real numbers

### N-tuple
- ordered list of $n$ numbers in brackets
	- $(1,2,3,4)$ is an n-tuple of length $4$

### Scalars
- described entirely **by a number**
- notated with lowercase italicized letters
	- $a,b,c,d$

### Vectors
- described by **a length** (non-negative $\mathbb{R}$; *magnitude*) and **a direction**.
- can also be written as an [[#N-tuple|n-tuple]]
- two vectors are ***equal*** if they have identical *length and direction*
	- $\vec{u}=\vec{v} \iff u_{i}=v_{i}$ where $i=1,2,\dots,n$
- a ***zero vector*** is denoted by $\mathbf{0}$.
- notated with bolded letters or with an arrow on top
	- $\vec{a},\vec{b},\vec{c},\vec{d}$

### Graphical representation

| Point in plane               | Vector in $\mathbb{R}^{2}$                    | Vector in $\mathbb{R}^{3}$                    |
| ---------------------------- | --------------------------------------------- | --------------------------------------------- |
| ![[IMG_31581D2EBCD0-1.jpeg]] | ![[Screenshot 2025-01-08 at 1.05.04 PM.jpeg]] | ![[Screenshot 2025-01-08 at 1.05.56 PM.jpeg]] |
- Vectors' lengths are described in *square brackets*, each line representing a **dimension**
	- a 2-dimensional vector looks like: $\begin{bmatrix}x\\y\end{bmatrix}$
		- $x$ represents the length in the x-axis
	- a 3-dimensional vector looks like: $\begin{bmatrix}x\\y\\z\end{bmatrix}$ or $\begin{bmatrix}x_{1}\\x_{2}\\x_{3}\end{bmatrix}$
	- an $n$-dimensional vector looks like: $\begin{bmatrix}x_{1}\\x_{2}\\\dots\\x_{n}\end{bmatrix}$

## Vector addition
- Two vectors are added by **connecting heads to tails**
- Add all lengths in each dimension
	- $\vec{u}+\vec{v}=\begin{bmatrix}u_{1}+v_{1}\\u_{2}+v_{2}\\\dots\\u_{n}+v_{n}\end{bmatrix}$
- $\vec{u}+\vec{v}=\vec{v}+\vec{u}$

> Add $\vec{u}$ and $\vec{v}$ given:
> $\vec{u}=\begin{bmatrix}1\\3\end{bmatrix}$, $\vec{v}=\begin{bmatrix}2\\1\end{bmatrix}$

| Algebraically                                                                                       | Geometrically                                      |
| --------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| $\vec{u}+\vec{v}$<br>$=\begin{bmatrix}1+2\\3+1\end{bmatrix}$<br>$=\begin{bmatrix}3\\4\end{bmatrix}$ | ![[Screenshot 2025-01-08 at 1.29.50 PM.jpeg\|300]] |

### Negation
- negate all lengths in each dimension

> Negate $\vec{u}$ given:
> $\vec{u}=\begin{bmatrix}2\\1\end{bmatrix}$

| Algebraically                                                                               | Geometrically                                      |
| ------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| $\vec{u}=\begin{bmatrix}2\\1\end{bmatrix}$<br>$-\vec{u}=\begin{bmatrix}-2\\-1\end{bmatrix}$ | ![[Screenshot 2025-01-08 at 1.38.48 PM.jpeg\|300]] |

### Vector subtraction
- **Negate the second** vector and add them
	- $\vec{u}-\vec{v}=\vec{u}+(-\vec{v})$
- Subtract lengths in each dimensions

> Subtract $\vec{u}$ and $\vec{v}$ given:
> $\vec{u}=\begin{bmatrix}1\\2\end{bmatrix}$, $\vec{v}=\begin{bmatrix}2\\1\end{bmatrix}$

| Algebraically                                                                                                                 | Geometrically                     |
| ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| $\vec{u}-\vec{v}$<br>$=\vec{u}+(-\vec{v})$<br>$=\begin{bmatrix}1-2\\2-1\end{bmatrix}$<br>$=\begin{bmatrix}-1\\1\end{bmatrix}$ | ![[IMG_8CD46929CA0D-1.jpeg\|300]] |

## Scalar multiplication
- Multiply the scalar quantity to the length of each dimension
	- $2\vec{v}$ is exactly twice as long as $\vec{v}$

> Multiply $\vec{v}$ by $2$ given:
> $\vec{v}=\begin{bmatrix}1\\2\end{bmatrix}$

| Algebraically                                                                                                                            | Geometrically                     |
| ---------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| $2\times \begin{bmatrix}1\\2\end{bmatrix}$<br>$=\begin{bmatrix}2\times 1\\2\times 2\end{bmatrix}$<br>$=\begin{bmatrix}2\\4\end{bmatrix}$ | ![[IMG_FF69C7D3A1A4-1.jpeg\|300]] |

---
## Vector properties
Also see [[3_Length and Angles#Properties|dot product properties]]

1. $\vec{u}+\vec{v}=\vec{v}+\vec{u}$
2. $(\vec{u}+\vec{v})+\vec{w}=\vec{u}+(\vec{v}+\vec{w})$
3. $\vec{u}+\mathbf{0}=\vec{u}$
4. $(k+l)\times\vec{u}=k\vec{u}+l\vec{u}$
5. $k(\vec{u}+\vec{v})=k\vec{u}+k\vec{v}$
6. $(kl)\vec{u}=k(l\vec{u})$
7. $1\vec{u}=\vec{u}$
8. $(-1)\vec{u}=-\vec{u}$
9. $0\vec{u}=\mathbf{0}$
10. $k\mathbf{0}=\mathbf{0}$

>[!note]
>Practice by showing each property algebraically then geometrically

---
## Linear combinations
*see more:* [MACM 101 → Integer division](https://munotes.tinagrit.com/MACM101/unit-4-properties-of-the-integers/week-10-division/1_integer-division.html?mark=linear%20combination)

A vector $\vec{w}$ in $\mathbb{R}^{2}$ ([[#Scalars and Vectors|pairs of real numbers]]) is a **linear combination** of vectors $\vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{k}}$ in $\mathbb{R}^{2}$ if it can be expressed as:
$$
\vec{w}=c_{1}\vec{v_{1}}+c_{2}\vec{v_{2}}+\dots+c_{k}\vec{v_{k}}
$$
for some scalar quantities $c_{1},c_{2},\dots,c_{k}\in \mathbb{R}$.

> [!warning] Linear combinations cannot include exponents greater than 1 (no squares)

### Examples

> Give an example of a linear combination of $\vec{v_{1}}$ and $\vec{v_{2}}$ given:
> $\vec{v_{1}}=\begin{bmatrix}1\\4\end{bmatrix}$, $\vec{v_{2}}=\begin{bmatrix}3\\4\end{bmatrix}$

$\vec{w}=3\vec{v_{1}}+2\vec{v_{2}}$
$=3\begin{bmatrix}1\\4\end{bmatrix}+2\begin{bmatrix}3\\4\end{bmatrix}$
$=\begin{bmatrix}3\\12\end{bmatrix}+\begin{bmatrix}6\\8\end{bmatrix}$
$=\begin{bmatrix}9\\20\end{bmatrix}$

$\vec{w}$ is a linear combination of $\vec{v_{1}}$ and $\vec{v_{2}}$


> Give a general linear combination of $\vec{v_{1}}$ and $\vec{v_{2}}$ given:
>  $\vec{v_{1}}=\begin{bmatrix}1\\4\end{bmatrix}$, $\vec{v_{2}}=\begin{bmatrix}2\\8\end{bmatrix}$

$\vec{w}=c_{1}\vec{v_{1}}+c_{2}\vec{v_{2}}$
$=c_{1}\begin{bmatrix}1\\4\end{bmatrix}+c_{2}\begin{bmatrix}2\\8\end{bmatrix}$
$=\begin{bmatrix}c_{1}\cdot 1+c_{2}\cdot 2\\c_{1}\cdot 4+c_{2}\cdot 8\end{bmatrix}$
$=\begin{bmatrix}c_{1}+2c_{2}\\4c_{1}+8c_{2}\end{bmatrix}$
$=(c_{1}+2c_{2})\begin{bmatrix}1\\4\end{bmatrix}$

$\vec{w}$ where $c_{1},c_{2}\in \mathbb{R}$ is a linear combination of $\vec{v_{1}},\vec{v_{2}}$

---
## Vector equation of lines
*see more:* [MACM 101 → Sets and Subsets](https://munotes.tinagrit.com/MACM101/unit-3-set-theory/week-6-sets-and-subsets/sets-and-subsets.html)

- a **line** through the origin in $\mathbb{R}^{2}$ is a set of vectors
	- $\{ t\vec{d} \mid t \in \mathbb{R} \}$
		- $t\times\vec{d}$  where $t$ is an element of all real numbers 
		- represent **all scalings** of $\vec{d}$

For example, the line $y=x$ ($45^{\circ}$ line)
- represents all scalings of the vector $\vec{v}=\begin{bmatrix}1\\1\end{bmatrix}$
- $\left\{ t\begin{bmatrix}1\\1\end{bmatrix} \mid t\in \mathbb{R} \right\}$
![[IMG_0690.jpg|300]]

### Off-origin line
- To translate the line off the origin, **add in a translating vector** into the set.

For example, the line $y=x+1$ (line above moved up by $1$)
- is the vector $\vec{v}=\begin{bmatrix}1\\1\end{bmatrix}$ on top of vector $\vec{t}=\begin{bmatrix}0\\1\end{bmatrix}$
- $\left\{ \begin{bmatrix}0\\1\end{bmatrix}+t\begin{bmatrix}1\\1\end{bmatrix} \mid t \in R \right\}$

![[IMG_3BFBA1F7978E-1.jpeg|300]]


### Parametric equations
Since each line of a vector represents a quantity in each dimension/axis, they can be **extracted** and represented **parametrically**.

For example, 
- The line $\left\{ \begin{bmatrix}0\\1\end{bmatrix}+t\begin{bmatrix}1\\2\end{bmatrix} \mid t \in R \right\}$
- Simplifying, we get $\left\{ \begin{bmatrix}0+1t\\1+2t\end{bmatrix} \mid t \in \mathbb{R} \right\}$
- $\implies \left\{ \begin{bmatrix}t\\2t+1\end{bmatrix} \mid t \in \mathbb{R} \right\}$
- This line can therefore be represented parametrically as
	- $x=t$
	- $y=2t+1$


### Examples

> Find a line parallel to $\vec{x}=t\begin{bmatrix}1\\2\\3\end{bmatrix}$

A translated line is **always parallel** to the original.
$\vec{y}=\begin{bmatrix}-1\\-1\\2\end{bmatrix}+t\begin{bmatrix}1\\2\\3\end{bmatrix}$ is therefore parallel to $\vec{x}$


> Find a line through the points $\begin{bmatrix}1\\4\\0\end{bmatrix}$ and $\begin{bmatrix}0\\0\\2\end{bmatrix}$

Set up the following template for the line:
$$
\begin{bmatrix}
1\\4\\0
\end{bmatrix}+t\begin{bmatrix}
a\\b\\c
\end{bmatrix}
$$
When $t=0$, $\begin{bmatrix}1\\4\\0\end{bmatrix}$ is already on the line.
- We need  $a$, $b$, $c$  values so that this line goes through $\begin{bmatrix}0\\0\\2\end{bmatrix}$
- Since $t\in \mathbb{R}$, achieving the result for one $t$ value will make the $a$, $b$, $c$ values valid for all $t$ values.
- Let $a$, $b$, $c$ be quantities such that when $t=1$, the vector ends up at $\begin{bmatrix}0\\0\\2\end{bmatrix}$

Set $t=1$ and solve for $a$, $b$, $c$:
$$
\begin{bmatrix}
1\\4\\0
\end{bmatrix}+1\times\begin{bmatrix}
a\\b\\c
\end{bmatrix}=\begin{bmatrix}
0\\0\\2
\end{bmatrix}
$$
- $1+a=0\implies a=-1$
- $4+b=0 \implies b=-4$
- $0+c=2 \implies c=2$

Therefore, the line
$$
L=\left\{ \begin{bmatrix}
1\\4\\0
\end{bmatrix} +t\begin{bmatrix}
-1\\-4\\2
\end{bmatrix} \mid t \in \mathbb{R} \right\} 
$$
is on both points.


---

## Vector equation of planes

- a **plane** through the origin in $\mathbb{R}^{3}$ is a set of a [[#Linear combinations|linear combination]].
	- $\{ t\vec{u}+s\vec{v} \mid t,s \in \mathbb{R} \}$
	- where $\vec{u}$ and $\vec{v}$ are vectors through the origin
	- Two lines crossing at the origin

> [!warning]
> To make a plane, $\vec{u}$ and $\vec{v}$ cannot be [[#Scalar multiplication|scalar multiples]] of each other. Otherwise, they are the exact same line.

### Plane example

> Give a plane $P$ with vectors $\vec{u}$ and $\vec{v}$ given:
> $\vec{u}=\begin{bmatrix}1\\3\\2\end{bmatrix}$,  $\vec{v}=\begin{bmatrix}-1\\4\\2\end{bmatrix}$

$P=\left\{ a\vec{u}+b\vec{v} \mid a,b \in \mathbb{R} \right\}$

$P=\left\{ a\begin{bmatrix}1\\3\\2\end{bmatrix} +b\begin{bmatrix}-1\\4\\2\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$

Plane $P$ has **2 degrees** of freedom. ($a$ and $b$ $\in \mathbb{R}$)

Plane $P$ can also be parametrically represented as:
- $x=a-b$
- $y=3a+4b$
- $z=2a+2b$


> Find a plane $Q$ parallel to $P$ through point $\begin{bmatrix}1\\1\\1\end{bmatrix}$

Since plane $P$ is through the origin, to get a plane through the point $\begin{bmatrix}1\\1\\1\end{bmatrix}$, shift the whole plane with the vector to that point.

$Q=\left\{ \begin{bmatrix}1\\1\\1\end{bmatrix}+ a\begin{bmatrix}1\\3\\2\end{bmatrix} +b\begin{bmatrix}-1\\4\\2\end{bmatrix} \mid a,b \in \mathbb{R} \right\}$
