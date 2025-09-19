Chapter 1.5


## Orthogonal Projections

Let $\vec{a}$ be a non-zero vector in $\mathbb{R}^{n}$
![[IMG_B3477FE14336-1.jpeg|300]]

Any vector on the same plane can be represented **uniquely** as a **projection** of $\vec{a}$. For example, to represent this vector $\vec{x}$:
![[IMG_A3548A715CCE-1.jpeg|300]]

Construct the vector $\vec{x}$ as an addition of $\vec{x_{1}}$ and $\vec{x_{2}}$
![[IMG_48B7A5E167A8-1.jpeg|300]]

where:
- $\vec{x_{1}}$ is in the [[2_Vector Spans and Basis|span]] of $\vec{a}$ (lies directly on top of $\vec{a}$)
	- $\vec{x_{1}}=t\vec{a}$ for some $t$
	- $t=\left(  \dfrac{\vec{x}\cdot  \vec{a}}{\lVert a \rVert^{2}}\right)$
	- $\vec{x_{1}}$ is called the **orthogonal projection** or the **vector component** of $\vec{x}$ onto $\text{span} \left\{ \vec{a} \right\}$
		- denoted by $\text{proj}_{{a}}{x}$
- $\vec{x_{2}}$ is [[3_Length and Angles#Orthogonality|orthogonal]] to $\vec{a}$
	- $\vec{x_{2}}=\vec{x}-\vec{x_{1}}$
	- $\vec{x_{2}}=\vec{x}-\left(  \dfrac{\vec{x}\cdot  \vec{a}}{\lVert a \rVert^{2}}\right)\times\vec{a}$
	- $\vec{x_{2}}$ is perpendicular to the projection
		- denoted by $\text{perp}_{a}x$

$$
\text{proj}_{a}x=\dfrac{x\cdot a}{\lVert a \rVert^{2} }a
$$
$$
\text{perp}_{a}x=x-\text{proj}_{a}x=x-\dfrac{x\cdot a}{\lVert a \rVert^{2} }a
$$

### Projection examples

> Find $\text{proj}_{a}x$ where:
> $\vec{x}=\begin{bmatrix}1\\-2\\-2\end{bmatrix}$ and $\vec{a}=\begin{bmatrix}4\\1\\-3\end{bmatrix}$

- $\text{proj}_{a}x=\left(  \dfrac{\vec{x}\cdot  \vec{a}}{\lVert a \rVert^{2}}\right)\times\vec{a}$
	- $\vec{x}\cdot  \vec{a}=(1\times4)+(-2 \times 1)+(-2 \times  -3)=8$
	- $(\lVert \vec{a} \rVert)^{2}=\left(\sqrt{ 4^{2}+1^{2}+(-3)^{2} }\right)^{2}=26$
- $\text{proj}_{a}x=\dfrac{8}{26}\times  \vec{a}=\dfrac{8}{26}\times \begin{bmatrix}4\\1\\-3\end{bmatrix}$
- $\therefore \text{proj}_{a}x=\begin{bmatrix}16/13\\4/13\\-12/13\end{bmatrix}$

