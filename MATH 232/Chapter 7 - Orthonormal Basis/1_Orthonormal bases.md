Chapter 7.1 and 7.2


## Orthonormality
- two vectors are **orthonormal** if:
	- they are [[3_Length and Angles#Orthogonality|orthogonal]], right angle to each other ($\vec{p}\cdot   \vec{q}=0$)
	- they both have [[3_Length and Angles#Vector lengths|magnitudes]] of 1 (**normal**ized)
	- the dot product of $\vec{v}_{i}$ and $\vec{v}_{j}$ is:
		- $0$, if $i\neq j$
		- $1$, if $i=j$

### Orthonormal basis
The basis is **orthonormal** if all basis vectors are orthonormal to each other.
 
For example
- the standard basis is orthonormal
- the basis $B=\left\{ \begin{bmatrix} \frac{1}{\sqrt{ 2 }}\\ \frac{1}{\sqrt{ 2 }} \end{bmatrix},\begin{bmatrix}-\frac{1}{\sqrt{ 2 }}\\ \frac{1}{\sqrt{ 2 }} \end{bmatrix} \right\}$ is orthonormal

To determine whether basis vectors are orthonormal, either:
- Perform dot products and find the length of each vector, or
- [[#Determining orthonormal basis|Construct a matrix and multiply]]

### Properties
If a basis is orthonormal, it satisfies the following:
- all non-zero basis vectors are [[2_Vector Spans and Basis#Linear independence|linearly independent]]
- If $\left\{ v_{1},v_{2},\dots v_{k} \right\}$ is the basis for a subspace, then
	- $\lVert v_{1}+v_{2}+\dots v_{k} \rVert^{2}=\lVert v_{1} \rVert^{2}+\lVert v_{2} \rVert^{2}+\dots+\lVert v_{k} \rVert^{2}$


### Orthogonal matrices
- a [[1_Matrix#Square matrices|square matrix]] $A$ is **orthogonal**
- if $A^{T}A^{}=I$, or $A^{T}=A^{-1}$

If a matrix $A$ is orthogonal, then:
- $A^{T}$ is orthogonal
- $A^{-1}$ is orthogonal
- $\det(A)=\pm 1$ 
- $\lambda = \pm 1$
- $\lVert Ax \rVert=\lVert x \rVert$
- $Ax \cdot Ay=x\cdot y$
- its [[6_Fundamental Subspaces#Row Spaces|row space]] forms an orthonormal basis
- its [[6_Fundamental Subspaces#Column Spaces|column space]] forms an orthonormal basis

If $A$ and $B$ are orthogonal, then the product $AB$ is orthogonal.


### Determining orthonormal basis
Using the theorem above, we conclude that:
- if a matrix is orthogonal,
- then its column space forms an orthonormal basis

This means that we can:
- **create a matrix**, each column being a basis vector
- **perform** $A^{T}A$
	- if the result $=I$, the basis is ortho**normal**
	- if the result is a diagonal matrix but $\neq I$, the basis is ortho**gonal**
	- otherwise, the basis is neither


---

## Projection onto a subspace

[[5_Projections|Projecting]] a vector onto a [[4_Subspaces|subspace]] (instead of onto another vector) is the **same as** rewriting the vector using a [[2_Coordinates|different basis]].

If we have a subspace $W$ that spans $\left\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{n}} \right\}$, we can **project** a vector $\vec{x}$ onto the subspace by finding each constant $c$ such that:
$$
\text{proj}_{W}\vec{x}=c_{1}\vec{v_{1}}+c_{2}\vec{v_{2}}+\dots c_{n}\vec{v_{n}}
$$
Note that this is still the **exact same process** as [[2_Coordinates#Finding coordinates example|finding coordinates]].

It turns out that each $c$ is a result of the projection of $\vec{x}$ onto each basis vector of $W$. We can rewrite the equation using the [[5_Projections#Orthogonal Projections|projection formula]].

> [!success] General formula to project onto an ortho**gonal** subspace
> $\text{proj}_{W}\vec{x}=\dfrac{x\cdot\vec{v_{1}}}{\lVert \vec{v_{1}} \rVert^{2} }\vec{v_{1}}+\dfrac{x\cdot\vec{v_{2}}}{\lVert \vec{v_{2}} \rVert^{2} }\vec{v_{2}}+\dots+\dfrac{x\cdot\vec{v_{n}}}{\lVert \vec{v_{n}} \rVert^{2} }\vec{v_{n}}$

If the basis of our subspace is **orthonormal**, we know that each basis vector has the length of 1. This cancels out all of the denominator.

$$
\text{proj}_{W}\vec{x}={(x\cdot\vec{v_{1}})}\vec{v_{1}}+{(x\cdot\vec{v_{2}})}\vec{v_{2}}+\dots+{(x\cdot\vec{v_{n}})}\vec{v_{n}}
$$

The dot product calculation for each basis vector can be **simplified** to:

> [!success] General formula to project onto an ortho**normal** subspace
> $\text{proj}_{W}\vec{x}=MM^{T}\vec{x}$
> 
> where $M$ is a matrix constructed by having each column being a basis vector of $W$.


This formula can be much easier to use than the general formula for any subspace above. However, it **only works** when a subspace is ortho**normal**.

This means that for an ortho**gonal** subspace, we can **normalize** the basis vectors by **diving each vector** by its **length**. This will make them ortho**normal** and we can use the formula.