Chapter 7.2


## Orthogonalization
- the **Gram-Schmidt** procedure turns **any basis** into an [[1_Orthonormal bases|orthonormal]] basis

Idea: for any [[4_Subspaces|subspace]] spanned by the basis $\left\{ \vec{w_{1}},\vec{w_{2}},\dots,\vec{w_{n}} \right\}$,
we can find another basis $\left\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{n}} \right\}$ that is **orthonormal** and spans the **same space**.


### Deriving the orthonormal basis
This derivation will be shown in $\mathbb{R}^{2}$, and the [[#The Gram-Schmidt Procedure|procedure]] that comes after will generalize this idea to $\mathbb{R}^{n}$.

Here, we have a subspace spanned by the vectors $\vec{w_{1}}$ and $\vec{w_{2}}$. We want to find an orthonormal basis that spans the **same space**.

![[IMG_FC128F2B5BA0-1.jpeg|400]]

$\vec{w_{1}}$ and $\vec{w_{2}}$ are [[2_Vector Spans and Basis#Linear independence|linearly independent]]. We can **choose** $\vec{w_{1}}$ to be one of the basis vectors, in this case $\vec{v_{1}}$.

Using $\vec{v_{1}}$, we can draw a **line** (space) spanned by all **orthogonal vectors** of $\vec{v_{1}}$. This entire line is orthogonal to $\vec{v_{1}}$, and is called $\vec{v_{1}}^{\perp}$.

![[IMG_C022ADA3D722-1.jpeg|400]]

Now, we can [[1_Orthonormal bases#Projection onto a subspace|project]] $\vec{w_{2}}$ onto the subspace $\vec{v_{1}}^{\perp}$, resulting in $\vec{v_{2}}$. 
![[IMG_CAEE26704563-1.jpeg|400]]

The new basis vectors $\vec{v_{1}}$ and $\vec{v_{2}}$ are **orthogonal** to each other, and span the same space as $\vec{w_{1}}$ and $\vec{w_{2}}$.

Notice that: $\vec{v_{2}}=\text{proj}_{\text{span}\left\{ \vec{v_{1}} \right\}^{\perp}}\vec{w_{2}}$

To make them orthonormal, simply normalize each vector by diving each component by its length.


### The Gram-Schmidt Procedure
- general way to find **orthonormal basis** that span the same space as a non-orthonormal basis
- the goal is to turn the subspace spanned by $\left\{ \vec{w_{1}},\vec{w_{2}},\dots,\vec{w_{n}} \right\}$ into the orthonormal span $\left\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v_{n}} \right\}$ without changing the space

Procedure:
1. **Base Step**: $\vec{v_{1}}=\vec{w_{1}}$
	- this is what we did earlier in $\mathbb{R}^{2}$ where we define the first orthogonal vector as the first basis vector

2. **Inductive Step**: for each basis vector that comes after, perform the following recursively:
$$
\vec{v}_{i}=\vec{w}_{i}-\text{proj}_{\text{span}\left\{ \vec{v_{1}},\vec{v_{2}},\dots,\vec{v}_{i-1} \right\} }\vec{w}_{i}
$$
	- project the non-orthogonal basis vector onto a space spanned by all the $\vec{v}$ vectors leading up to the current one
	- see how to [[1_Orthonormal bases#Projection onto a subspace|project onto a subspace]]
	- regularly *check* that all $\vec{v_{i}}$ vectors are orthogonal, by verifying that the **dot products are 0**

3. **Normalization Step**: normalize each basis vector by diving it by its length
$$
\vec{v_{i}}^{\text{Normalized}}=\dfrac{\vec{v_{i}}}{\lVert \vec{v_{i}} \rVert }
$$
