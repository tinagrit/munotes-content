Chapter 1.3


## Vector lengths
- the **length** or **magnitude** or **norm** of a vector 
- denoted $\lVert \vec{v} \rVert$ for "*length of vector* $\vec{v}$"
- is a positive [[1_Vectors#Scalars|scalar]] quantity
	- $\lVert \vec{v} \rVert\geq 0$
- $\lVert c\vec{v} \rVert=|c|\times \lVert \vec{v} \rVert$ where $c \in \mathbb{R}$ 
- $\lVert \vec{v} \rVert=0 \iff   \vec{v}=\mathbf{0}$ 
	- a vector can only be 0 in length if and only if the vector is a $\mathbf{0}$ vector

Also see [[#Distance]]

### In R2
The length of the vector $\vec{v}=\begin{bmatrix}v_{1}\\v_{2}\end{bmatrix}$ can be calculated using the Pythagorean Theorem
![[IMG_70421A2C3A39-1.jpeg|300]]
$$\underset{ \text{in }\mathbb{R}^{2} }{ \lVert { \vec{v} } \rVert }=\sqrt{ v_{1}^{2}+v_{2}^{2} }$$
- For example, $\lVert \begin{bmatrix}3\\4\end{bmatrix} \rVert = \sqrt{ 3^{2}+4^{2} }=\sqrt{ 25 } =5$

### In R3
The length of the vector $\vec{v}=\begin{bmatrix}v_{1}\\v_{2}\\v_{3}\end{bmatrix}$ can be calculated with the following formula (derived from the Pythagorean Theorem, similar to $\mathbb{R}^{2}$)
$$
\underset{ \text{in } \mathbb{R}^{3} }{ \lVert \vec{v} \rVert } = \sqrt{ v_{1}^{2}+v_{2}^{2}+v_{3}^{2} }
$$

$\lVert \vec{v} \rVert$ is also equal to $\sqrt{ \vec{v} \cdot \vec{v} }$ ([[#Dot product Examples|see below]])


### Triangle Inequality
The direct path is shorter than the total lengths of all other sides
$\lVert \vec{u}+  \vec{v} \rVert=\lVert \vec{u} \rVert+\lVert \vec{v} \rVert$

![[IMG_EC077BB8E5E8-1.jpeg|300]]


---
## Distance
- a [[#Vector lengths|length]] is calculated from the origin to the vector endpoint
- a **distance** is calculated from a point to another point
	- denoted by $d(\vec{u},\vec{v})$
		- for "*distance between the endpoints of* $\vec{u}$ *and* $\vec{v}$"
		- is the **length of** $\vec{v}-\vec{u}$
	- is a positive [[1_Vectors#Scalars|scalar]] quantity
		- since the result has square root over everything
		- $d(\vec{u},\vec{v})\geq 0$
	- $d(\vec{u},\vec{v})=0 \iff  \vec{u}=\vec{v}$
		- if $\vec{u}$ and $\vec{v}$ are exactly the same, then there is no distance between each other
	- $d(\vec{u},\vec{v})=d(\vec{v},\vec{u})$ (commutative)

The distance can be calculated by also using the Pythagorean Theorem:
$$
\underset{ \text{in } \mathbb{R}^{2} }{ d(\vec{u}-\vec{v}) }=\lVert \vec{v}-\vec{u} \rVert =\sqrt{ (v_{1}-u_{1})^{2}+(v_{2}-u_{2})^{2} }
$$
$$
\underset{ \text{in } \mathbb{R}^{3} }{ d(\vec{u}-\vec{v}) }=\lVert \vec{v}-\vec{u} \rVert =\sqrt{ (v_{1}-u_{1})^{2}+(v_{2}-u_{2})^{2}+(v_{3}-u_{3})^{2} }
$$

### Distance examples

> Calculate the distance between $\vec{u}=\begin{bmatrix}1\\5\end{bmatrix}$ and $\vec{v}=\begin{bmatrix}-1\\4\end{bmatrix}$
> ![[IMG_B7C86D7A6063-1.jpeg|200]]
> (Diagram not to scale)

$d(\vec{u},\vec{v})$
- $=\lVert \vec{v}-\vec{u} \rVert$
- $=\sqrt{ (-1-1)^{2}-(4-5)^{2} }$
- $=\sqrt{ 4+1 }$
- $=\sqrt{ 5 }$


---
## Angles
- the **angle** needed to **rotate** one vector to another vector
- between two **non-zero** vectors
- smallest non-negative quantity

For example, the angle $\theta$ rotates from $\vec{v}$ to $\vec{u}$
![[IMG_029E4230481C-1.jpeg|300]]

In $\mathbb{R}^{2}$, the angle can be calculated with the following formula:
$$
\cos\theta=\dfrac{u_{1}v_{1}+u_{2}v_{2}}{\lVert \vec{u} \rVert \times \lVert \vec{v} \rVert }
$$

### Angle examples

> Find the angle between $\vec{a}=\begin{bmatrix}1\\2\end{bmatrix}$ and $\vec{b}=\begin{bmatrix}-1\\5\end{bmatrix}$

$\cos\theta=\dfrac{a_{1}b_{1}+a_{2}b_{2}}{\lVert a \rVert \times \lVert b \rVert}$
$\cos\theta=\dfrac{{(1)(-1)+(2)(5)}}{(\sqrt{ 1^{2}+2^{2} })(\sqrt{ (-1)^{2}+5^{2} })}$
$\cos\theta=\dfrac{-1+10}{(\sqrt{ 5 })(\sqrt{ 26 })}$
$\cos\theta=\dfrac{9}{\sqrt{ 5 }\sqrt{ 26 }}$
$\theta=\arccos \dfrac{9}{\sqrt{ 5 }\sqrt{ 26 }}$


> Derive the angle formula using $\vec{u}=\begin{bmatrix}u_{1}\\0\end{bmatrix}$ and $v_{1}=\begin{bmatrix}v_{1}\\v_{2}\end{bmatrix}$ 
> where $u_{1}=v_{1}$ and $a,b \neq 0$

![[IMG_40E868B7AD5D-1.jpeg|250]]

$\cos\theta$
- $=\dfrac{\text{adjacent}}{\text{hypotenuse}}$
- $=\dfrac{\lVert \vec{u} \rVert}{\lVert \vec{v} \rVert}$
- $=\dfrac{\sqrt{ u_{1}^{2}+u_{2}^{2} }}{\sqrt{ v_{1}^{2}+v_{2}^{2} }}$
- $=\dfrac{\sqrt{ u_{1}^{2}+\cancelto{ 0 }{ u_{2}^{2} } }}{\sqrt{ v_{1}^{2}+v_{2}^{2} }}$
- $=\dfrac{u_{1}}{\sqrt{ v_{1}^{2}+v_{2}^{2} }}$
- $=\dfrac{u_{1}}{\sqrt{ v_{1}^{2}+v_{2}^{2} }}\times \dfrac{u_{1}}{u_{1}}$
- $=\dfrac{u_{1}^{2}}{u_{1}\sqrt{ v_{1}^{2}+v_{2}^{2} }}$  
- $=\dfrac{u_{1}^{2}}{\sqrt{ u_{1}^{2} } \sqrt{ v_{1}^{2}+v_{2}^{2} }}$
- $=\dfrac{u_{1}^{2}}{\sqrt{ u_{1}^{2} +0 } \sqrt{ v_{1}^{2}+v_{2}^{2} }}$
- $=\dfrac{u_{1}^{2}}{\sqrt{ u_{1}^{2} +u_{2}^{2} } \sqrt{ v_{1}^{2}+v_{2}^{2} }}$
- $=\dfrac{u_{1}^{2}}{\lVert u \rVert\times \lVert v \rVert}$
- $=\dfrac{u_{1}\cdot u_{1}}{\lVert u \rVert\times \lVert v \rVert}$
- $=\dfrac{u_{1}v_{1}}{\lVert u \rVert\times \lVert v \rVert}$
- $=\dfrac{u_{1}v_{1}+0}{\lVert u \rVert\times \lVert v \rVert}$
- $=\dfrac{u_{1}v_{1}+0\cdot(v_{2})}{\lVert u \rVert\times \lVert v \rVert}$
- $=\dfrac{u_{1}v_{1}+u_{1}v_{2}}{\lVert u \rVert\times \lVert v \rVert}$

> [!warning]
> This is not a proof, but rather a justification to show that the formula works for this specific constraint.


---
## Dot products
- a **dot product** of vectors is a [[1_Vectors#Scalars|scalar]]
- multiply the quantity in each dimension of all vectors

In $\mathbb{R}^{2}$
- $\vec{u}\cdot     \vec{v}=u_{1}v_{1}+u_{2}v_{2}$

In $\mathbb{R}^{3}$
- $\vec{u}\cdot   \vec{v}=u_{1}v_{1}+u_{2}v_{2}+u_{3}v_{3}$

In $\mathbb{R}^{n}$
- $\vec{u}\cdot   \vec{v}=u_{1}v_{1}+u_{2}v_{2}+\dots+u_{n}v_{n}$

### Cauchy-Schwartz Inequality
- The dot product is less than the multiplication of the vector lengths
- $|\vec{u}\cdot  \vec{v}|\leq \lVert \vec{u} \rVert\times  \lVert \vec{v} \rVert$

### Orthogonality
- two vectors are **orthogonal**
	- if a dot product of the two vectors **is 0**
- $\vec{u}\perp  \vec{v} \implies  \vec{u}\cdot   \vec{v}=0$
- the [[#Angles|angle]] between the two vectors is therefore $90^{\circ}$ and $\cos\theta=0$

#### The Normal Vector
- is a vector that is **orthogonal to a segment** in plane
- there is a **unique** normal vector for each point on plane
- the normal vector can only **touch the plane once**
![[Screenshot 2025-01-14 at 8.23.22 PM.png|250]]


### Properties
1. Commutative
	1. $\vec{u}\cdot  \vec{v}=\vec{v}  \cdot  \vec{u}$
2. Distribution
	1. $\vec{u} \cdot  (\vec{v}+\vec{w})=\vec{u}\cdot  \vec{v}+\vec{u}\cdot  \vec{w}$
	2. $\vec{u} \cdot  (\vec{v}-\vec{w})=\vec{u}\cdot  \vec{v}-\vec{u}\cdot  \vec{w}$
	3. $(\vec{u}+\vec{v})\cdot  \vec{w}=\vec{u}\cdot  \vec{w}+\vec{v}\cdot  \vec{w}$
3. Associative
	1. $k(\vec{u}\cdot  \vec{v})=(k\vec{u})\cdot  \vec{v}$
	2. $k(\vec{u}\cdot  \vec{v})=(k\vec{v})\cdot  \vec{u}$
4. Zero
	1. $\mathbf{0}\cdot  \vec{v}=0$

### Dot product examples

> Find the dot product of $\vec{u}=\begin{bmatrix}1\\2\end{bmatrix}$ and $\vec{v}=\begin{bmatrix}-1\\5\end{bmatrix}$

$\vec{u}\cdot   \vec{v}=(1)(-1)+(2)(5)=9$


> Find the dot product $\vec{u}\cdot  \vec{u}$ in $\mathbb{R}^{2}$

$\vec{u}\cdot  \vec{u}=u_{1}u_{1}+u_{2}u_{2}=u_{1}^{2}+u_{2}^{2}$

Notice that $\lVert \vec{u} \rVert=\sqrt{ u_{1}^{2}+u_{2}^{2} }$

$\therefore \vec{u} \cdot  \vec{u}=\lVert \vec{u} \rVert^{2}$


> Are $\vec{u}$ and $\vec{v}$ orthogonal to each other given:
> $\vec{u}=\begin{bmatrix}3\\0\end{bmatrix}$,  $\vec{v}=\begin{bmatrix}0\\3\end{bmatrix}$

$\vec{u}\cdot  \vec{v}=(3)(0)+(0)(3)=0$

Since the dot product is 0, $\vec{u}$ and $\vec{v}$ are orthogonal.


> Find the plane through $P(1,1,2)$ with normal $\vec{n}=\begin{bmatrix}-1\\2\\1\end{bmatrix}$

![[IMG_601F8F82DC39-1.jpeg|300]]

- Connect the point on plane $P(1,1,2)$ to a generic point on plane $Q(x,y,z)$ by a new vector $\vec{v}$
- $\vec{v}=Q(x,y,z)-P(1,1,2)=\begin{bmatrix}x-1\\y-1\\z-2\end{bmatrix}$ (see [[#Distance]])
- Since $\vec{v}$ is along the plane, it must be [[#Orthogonality|orthogonal]] to the vector $\vec{n}$
- Therefore, $\vec{v}\cdot  \vec{n}=0$
- $\implies \begin{bmatrix}x-1\\y-1\\z-2\end{bmatrix} \cdot \begin{bmatrix}-1\\2\\1\end{bmatrix}=0$
- $\implies (x-1)(-1)+(y-1)(2)+(z-1)(1)=0$
- $\implies -x+2y+z=3$

$\therefore$ The plane equation is $-x+2y+z = 3$

> [!important] Notice that the coefficients of the plane equation (-1, 2, 1) are the normal vector

