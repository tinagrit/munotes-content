Chapter 3.4


## Range
- all **possible outputs** from all inputs
- defined as
$$
\text{Range}(L)=\left\{ L(\vec{x})\in \mathbb{R}^{m}\mid \vec{x}\in \mathbb{R}^{n} \right\}
$$
- where
	- $L$ is a [[3_Functions and Mappings#Linear mappings|linear mapping]] (function)
	- $\vec{x}$ is the input
	- $\mathbb{R}^{m}$ is the [[3_Functions and Mappings#Domain and Codomain|codomain]]
	- $\mathbb{R}^{n}$ is the [[3_Functions and Mappings#Domain and Codomain|domain]]

> [!note] Range is a subset of [[3_Functions and Mappings#Domain and Codomain|codomain]].

- Since $L$ is linear, 
	- $L(c\vec{x})=cL(\vec{x})$
	- $L(\vec{x}+\vec{y})=L(\vec{x})+L(\vec{y})$
- $L$ is closed under addition and scalar multiplication
- Therefore, the range is a [[4_Subspaces#Subspaces|subspace]] 

### Range examples

> State the domain, codomain, and range of the linear transformation:
> $L(x_{1},x_{2},x_{3})=(2x_{1},-x_{2}+2x_{3})$

Since:
- the mapping receives 3 inputs, the domain is $\mathbb{R}^{3}$
- the mapping returns 2 outputs, the codomain is $\mathbb{R}^{2}$

Rewriting the mapping we get:
$$
L(\vec{x})=\begin{bmatrix}
2x_{1} \\
-x_{2}+2x_{3}
\end{bmatrix}=x_{1}\begin{bmatrix}
2 \\
0
\end{bmatrix}+x_{2}\begin{bmatrix}
0 \\
-1
\end{bmatrix}+x_{3}\begin{bmatrix}
0 \\
2
\end{bmatrix}
$$
Therefore, the mapping can output linear combinations of any $x_{1},x_{2},x_{3}$. The range is the [[2_Vector Spans and Basis#Span|span]] of these 3 vectors.
$$
\text{Range}(L)=\text{span}\left\{ \begin{bmatrix}
2\\0
\end{bmatrix},\begin{bmatrix}
0\\-1
\end{bmatrix},\begin{bmatrix}
0\\2
\end{bmatrix} \right\} 
$$
Since there are 2 [[3_Reduced REF#Spans and Dimensions|linearly independent]] vectors in the span:
$$
\text{Range}(L)=\mathbb{R}^{2}
$$
