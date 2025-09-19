Chapter 3.2


## Matrix as a function
- think of [[1_Matrix#Matrices|matrices]] as a **function** that **operates on a** [[1_Vectors#Vectors|vector]]

Recall the equation from [[2_Matrix multiplication#Single matrix equation|Single matrix equation]]:
$$
A\vec{x}=\vec{b}
$$
$$
\begin{bmatrix}
3 & -7 & 1 \\
5 & 1 & 2
\end{bmatrix}\vec{x}=\begin{bmatrix}
4 \\
2
\end{bmatrix}
$$
Solving for $\vec{x}$ (*solving process not relevant here; see* [[2_Row Echelon#Solving REF Matrix Examples|Solving REF]] *for how to solve*), we get:
$$
\vec{x}=\begin{bmatrix}
6 \\
0 \\
-14
\end{bmatrix}+t\begin{bmatrix}
15 \\
1 \\
-38
\end{bmatrix},t\in \mathbb{R}
$$
Since there are infinitely as many solutions, picking $t=1$, we get:
$$
\vec{x}\mid\\ _{t=1}= \begin{bmatrix}
21 \\
1 \\
-52
\end{bmatrix}
$$
Then, substituting this back into the equation, this statement is true:
$$
A\vec{x}=\vec{b}
$$
$$
\begin{bmatrix}
3 & -7 & 1 \\
5 & 1 & 2
\end{bmatrix}\begin{bmatrix}
21 \\
1 \\
-52
\end{bmatrix}=\begin{bmatrix}
4 \\
2
\end{bmatrix}
$$
In this form, we can think of matrix $A$ as a **function** that **transforms** $\vec{x}$ into $\vec{b}$:
$$
f_{A}(\vec{x})=\vec{b}
$$
Through function $f_{A}$, the vector $\begin{bmatrix}21\\1\\-52\end{bmatrix}\mapsto \begin{bmatrix}4\\2\end{bmatrix}$

> [!important] A function mapping that is done by multiplying with a matrix is called a **matrix mapping**.

### Domain and Codomain
- In the example above, notice that $\vec{x}$ is a vector in $\mathbb{R}^{3}$, but $\vec{b}$ is a vector in $\mathbb{R}^{2}$
- This means that the function $f_{A}$ maps $\mathbb{R}^{3}\mapsto \mathbb{R}^{2}$
	- Notation: $f:\mathbb{R}^{3}\mapsto \mathbb{R}^{2}$
- This can be determined using the **size of the matrix**
	- The number of **columns** is the **domain**
	- The number of **rows** is the **codomain**
![[diag8.png|400]]

> [!note] [[5_Mapping Range#Range|Range]] is a subset of codomain.

### Function Example

> Determine $f_{A}(2,-5)$ given:
> $A=\begin{bmatrix}-2&3\\3&0\\1&5\\4&-6\end{bmatrix}$

$f_{A}=\begin{bmatrix}-2&3\\3&0\\1&5\\4&-6\end{bmatrix}\begin{bmatrix}2\\-5\end{bmatrix}$

Using [[2_Matrix multiplication#Product of Ax|Single matrix multiplication]], we get:
$f_{A}=\begin{bmatrix}-19\\6\\-23\\32\end{bmatrix}$


### Standard Basis Vectors
- vector in $\mathbb{R}^{n}$ [[#Domain and Codomain|domain]] of the matrix mapping
- all 0s except for a **single 1** in the row specified
- denoted $e_{n}$ where $n$ is the row with 1
- for example:
	- If the domain is $\mathbb{R}^{3}$,
	- $e_{1}=\begin{bmatrix}1\\0\\0\end{bmatrix}$, $e_{2}=\begin{bmatrix}0\\1\\0\end{bmatrix}$, $e_{3}=\begin{bmatrix}0\\0\\1\end{bmatrix}$

This can be used to **extract** [[1_Matrix#Row and Column Vectors|column vectors]] out of a matrix.
- $e_{n}$ will return column $n$ of the matrix

For example, let:
$A=\begin{bmatrix}-2&3\\3&0\\1&5\\4&-6\end{bmatrix}$
- $f_{A}(e_{1})=A\begin{bmatrix}1\\0\end{bmatrix}=\begin{bmatrix}-2\\3\\1\\4\end{bmatrix}$ (first column)
- $f_{A}(e_{2})=A\begin{bmatrix}0\\1\end{bmatrix}=\begin{bmatrix}3\\0\\5\\6\end{bmatrix}$ (second column)


### Standard Basis Matrices
- matrix $M_{m\times n}(\mathbb{R})$ 
- all 0s except for a **single 1** in the matrix
- denoted $A_{ij}$ where $i$ is the row and $j$ is the column

For example, the standard basis matrices for a $2\times 2$ matrix includes:
$B=\left\{ A_{11},A_{12},A_{21},A_{22} \right\}$

$B=\left\{ \begin{bmatrix}1&0\\0&0\end{bmatrix},\begin{bmatrix}0&1\\0&0\end{bmatrix},\begin{bmatrix}0&0\\1&0\end{bmatrix},\begin{bmatrix}0&0\\0&1\end{bmatrix} \right\}$

To represent $M=\begin{bmatrix}1&-2\\3&4\end{bmatrix}$, we can say:
$M=A_{11}-2A_{12}+3A_{21}+4A_{22}$

---
## Linear mappings

- any mapping is **linear** is it satisfies
	1. $f(k\vec{x})=kf(\vec{x})$
		- *Homogeneity property*
		- any [[1_Vectors#Scalars|scalar]] constant can be multiplied **before or after** the function
	2. $f(\vec{x}+\vec{y})=f(\vec{x})+f(\vec{y})$
		- *Additivity property*
		- functions should have the **distributive property**

Show that a function **satisfies** these two properties to **show that it is linear**.

> [!important] Important
> All linear mappings are matrix mappings, and all matrix mappings are linear mappings.
> 
> **A mapping is linear if and only if it is a matrix mapping**.

### Linear mapping Example

> Is $g$ a linear mapping, given:
> $g(x_{1},x_{2},x_{3})=\begin{bmatrix}1\\1\\1\end{bmatrix}$

- Prove additivity
	- Create two sets of arbitrary values
	- $g(a_{1},a_{2},a_{3})$ and $g(b_{1},b_{2},b_{3})$
	- Since both are equal to $\begin{bmatrix}1\\1\\1\end{bmatrix}$, we get:
	- $g(\vec{a})+g(\vec{b})=\begin{bmatrix}1\\1\\1\end{bmatrix}+\begin{bmatrix}1\\1\\1\end{bmatrix}=\begin{bmatrix}2\\2\\2\end{bmatrix}$
	- However, $g(\vec{a}+\vec{b})=\begin{bmatrix}1\\1\\1\end{bmatrix}$ (anything plugged into $g$ will return this value)
- Additivity fails, therefore, $g$ is **not a linear mapping**

### Standard matrix
- describes a **function**
- can be found using [[#Standard Basis Vectors]]

> [!info] Every linear mapping has a standard matrix.

For example, we will determine the standard matrix for function $L$ where:
$L(x_{1},x_{2},x_{3})=\begin{bmatrix}2x_{1}\\x_{1}-x_{2}+3x_{3}\end{bmatrix}$

Notice that:
- the **pre-image** (input) has 3 components 
	- $\implies$ Domain is in $\mathbb{R}^{3}$
	- $\implies$ Standard matrix has 3 columns
- the **image** (output) has 2 components
	- $\implies$ Codomain is in $\mathbb{R}^{2}$
	- $\implies$ Standard matrix has 2 rows

To find the standard matrix,
- Plug in $e_{1}$ into $L$, place the result in the **first column**
	- $L(e_{1})=L(1,0,0)=\begin{bmatrix}2(1)\\1-0+0\end{bmatrix}=\begin{bmatrix}2\\1\end{bmatrix}$
	- The standard matrix is now: $\begin{bmatrix}2&\times &\times\\1&\times&\times\end{bmatrix}$
- Plug in $e_{2}$ into $L$, place the result in the **second column**
	- $L(e_{2})=L(0,1,0)=\begin{bmatrix}2(0)\\0-1+0\end{bmatrix}=\begin{bmatrix}0\\-1\end{bmatrix}$
	- The standard matrix is now: $\begin{bmatrix}2&0 &\times\\1&-1&\times\end{bmatrix}$
- Plug in $e_{3}$ into $L$, place the result in the **third column**
	- $L(e_{3})=L(0,0,1)=\begin{bmatrix}2(0)\\0-0+3(1)\end{bmatrix}=\begin{bmatrix}0\\3\end{bmatrix}$
	- The standard matrix is now: $\begin{bmatrix}2&0 &0\\1&-1&3\end{bmatrix}$

$\therefore$ The standard matrix of $L$ is 
$$\begin{bmatrix}2&0 &0\\1&-1&3\end{bmatrix}$$

### Standard Matrix Example

> Given $\vec{v}=\begin{bmatrix}-2\\1\end{bmatrix}$
> Determine the standard matrix for $[\text{proj}_{\vec{v}}]$
> See [[5_Projections|Vector Projections]]

Since $\text{proj}$ does not change the input vector's dimensions,
- both the pre-image and image are in $\mathbb{R}^{2}$
- $\implies$ the standard matrix will be $2\times 2$

The [[5_Projections|Projection formula]]:
$$
\text{proj}_{\vec{v}}\vec{a}=\dfrac{\vec{a}\cdot   \vec{v}}{\lVert \vec{v} \rVert ^{2}}\vec{v}
$$

To find the standard matrix,
- Plug in $e_{1}$ into $\text{proj}_{\vec{v}}$, place the result in the first column
	- $\text{proj}_{\vec{v}}e_{1}=\dfrac{e_{1}\cdot   \vec{v}}{\lVert \vec{v} \rVert ^{2}}\vec{v}$
		- $=\dfrac{\begin{bmatrix}1\\0\end{bmatrix}\cdot\begin{bmatrix}-2\\1\end{bmatrix}}{5}\begin{bmatrix}-2\\1\end{bmatrix}$
		- $=-\dfrac{2}{5}\begin{bmatrix}-2\\1\end{bmatrix}$
		- $=\begin{bmatrix} \frac{4}{5}\\-\frac{2}{5} \end{bmatrix}$
	- The standard matrix is now: $\begin{bmatrix} \frac{4}{5}&\times\\ -\frac{2}{5} &\times\end{bmatrix}$
- Plug in $e_{2}$ into $\text{proj}_{\vec{v}}$, place the result in the first column
	- $\text{proj}_{\vec{v}}e_{2}=\dfrac{e_{2}\cdot   \vec{v}}{\lVert \vec{v} \rVert ^{2}}\vec{v}$
		- $=\dfrac{\begin{bmatrix}0\\1\end{bmatrix}\cdot\begin{bmatrix}-2\\1\end{bmatrix}}{5}\begin{bmatrix}-2\\1\end{bmatrix}$
		- $=\dfrac{1}{5}\begin{bmatrix}-2\\1\end{bmatrix}$
		- $=\begin{bmatrix} -\frac{2}{5}\\ \frac{1}{5} \end{bmatrix}$
	- The standard matrix is now: $\begin{bmatrix} \frac{4}{5}& -\frac{2}{5} \\ -\frac{2}{5} & \frac{1}{5} \end{bmatrix}$

$\therefore$ The standard matrix of $[\text{proj}_{\vec{v}}]$ is
$$
\begin{bmatrix} \frac{4}{5}& -\frac{2}{5} \\ -\frac{2}{5} & \frac{1}{5} \end{bmatrix}
$$


### Function Composition

- **inputting a function** into another function
- $f(g(x))\iff (f\circ g)(x)$
	- pronounced "$f$ compose $g$"
- if $f$ and $g$ are both linear mappings, $f \circ g$ is also a linear mapping

Think of functions $f$ and $g$ as matrix mappings:
- $f_{F}(f_{G}(\vec{x}))$
- $=f_{F}(G\vec{x})$
- $=FG\vec{x}$
Composing $f$ and $g$ results in the **multiplication** of their standard matrices.

> [!important] Important
> Writing $f \circ g$ where $f$ and $g$ are standard matrices $F$ and $G$,
> The resulting standard matrix is simply $F \times G$
