Chapter 3.1

<div class="PWW">
<div data-callout-metadata="" data-callout-fold="" data-callout="warning" class="callout"><div class="callout-title" dir="auto"><div class="callout-icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-alert-triangle"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3"></path><path d="M12 9v4"></path><path d="M12 17h.01"></path></svg></div><div class="callout-title-inner">Narrow Screen</div></div><div class="callout-content">
<p dir="auto">This page includes wide mathematical graphics which may not fit well on your screen. Viewing this on a wider screen is highly recommended.</p>
</div></div>
</div>
<div class="hideOnDark">
<div data-callout-metadata="" data-callout-fold="" data-callout="warning" class="callout"><div class="callout-title" dir="auto"><div class="callout-icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-alert-triangle"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3"></path><path d="M12 9v4"></path><path d="M12 17h.01"></path></svg></div><div class="callout-title-inner">This page looks better in dark mode.</div></div><div class="callout-content">
<p dir="auto">Some of the images are made to match dark mode. You can switch using the sidebar on the left.</p>
</div></div>
</div>

## Single matrix equation

When writing a system of equations, for example:
$$
\begin{align}
3x_{1}-7x_{2}+x_{3} & =4 \\
5x_{1}+x_{2}+2x_{3} & =2
\end{align}
$$
We can rewrite this as an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]]:
$$
\begin{align}
\begin{array}{@{}cccc@{}}
x_{1} & x_{2} & x_{3} & = \\
\downarrow & \downarrow & \downarrow & \downarrow\\ 
\end{array} \\
\left[   \begin{array}{@{}ccc|c@{}}
3 & -7 & 1 & 4 \\
5 & 1 & 2 & 2
\end{array}\right]
\end{align}

$$
Notice:
- **First** column of the matrix is multiplied by $x_{1}$
- **Second** column of the matrix is multiplied by $x_{2}$
- **Third** column of the matrix is multiplied by $x_{3}$

Think of $x_{1},x_{2},x_{3}$ as components of the vector $\vec{x}$
- The entire [[1_Augmented Matrix#Coefficient Matrix|coefficient matrix]] is multiplied by $\vec{x}$ to produce the right side

We can rewrite the system as:
$$
\begin{bmatrix}
3 & -7 & 1 \\
5 & 1 & 2
\end{bmatrix}\vec{x}=\begin{bmatrix}
4 \\
2
\end{bmatrix}
$$
This is now in the **single matrix equation** form.
$$
A\vec{x}=\vec{b}
$$
where:
- $A$ is the [[1_Augmented Matrix#Coefficient Matrix|coefficient matrix]]
- $\vec{x}$ is the [[3_Reduced REF#Solution Set|Solution Set]]
- $\vec{b}$ is the resulting vector


### Product of Ax
From the example above, expanding $\vec{x}$ into the vector form, we get:
$$
\begin{bmatrix}
3 & -7 & 1 \\
5 & 1 & 2
\end{bmatrix}\begin{bmatrix}
x_{1} \\
x_{2} \\
x_{3}
\end{bmatrix}=\begin{bmatrix}
4 \\
2
\end{bmatrix}
$$
Using this form, we have shown that:
- the **first column** of $A$ is multiplied by the **first row** of $\vec{x}$
- the **second column** of $A$ is multiplied by the **second row** of $\vec{x}$
- the **third column** of $A$ is multiplied by the **third row** of $\vec{x}$

Notice: the number of **columns in** $A$ must **equal to** the number of **rows in** $\vec{x}$.

Producing the first equation
This is done by adding:
- **first element** in the first row of $A$ ($3$) $\times$ **first element** in the first column of $\vec{x}$ ($x_{1}$)
	- $\begin{bmatrix}\boxed{ 3 } & -7 & 1 \\5 & 1 & 2\end{bmatrix}\begin{bmatrix}\boxed{ x_{1} } \\x_{2} \\x_{3}\end{bmatrix}$
- **second element** in the first row of $A$ ($-7$) $\times$ **second element** in the first column of $\vec{x}$ ($x_{2}$)
	- $\begin{bmatrix}3 & \boxed{ -7 } & 1 \\5 & 1 & 2\end{bmatrix}\begin{bmatrix}x_{1} \\\boxed{ x_{2} } \\x_{3}\end{bmatrix}$
- **third element** in the first row of $A$ ($1$) $\times$ **third element** in the first column of $\vec{x}$ ($x_{3}$)
	- $\begin{bmatrix}3 & -7 & \boxed{ 1 } \\5 & 1 & 2\end{bmatrix}\begin{bmatrix}x_{1} \\x_{2} \\\boxed{ x_{3} }\end{bmatrix}$
Therefore, the first row of the result $b$ is $3x_{1}-7x_{2}+x_{3}$
- $3x_{1}-7x_{2}+x_{3}=4$

Producing the second equation
This is done by adding:
- **first element** in the second row of $A$ ($5$) $\times$ **first element** in the first column of $\vec{x}$ ($x_{1}$)
	- $\begin{bmatrix}3 & -7 & 1 \\\boxed{ 5 } & 1 & 2\end{bmatrix}\begin{bmatrix}\boxed{ x_{1} } \\x_{2} \\x_{3}\end{bmatrix}$
- **second element** in the second row of $A$ ($1$) $\times$ **second element** in the first column of $\vec{x}$ ($x_{2}$)
	- $\begin{bmatrix}3 & -7 & 1 \\5 & \boxed{ 1 } & 2\end{bmatrix}\begin{bmatrix}x_{1} \\\boxed{ x_{2} } \\x_{3}\end{bmatrix}$
- **third element** in the second row of $A$ ($2$) $\times$ **third element** in the first column of $\vec{x}$ ($x_{3}$)
	- $\begin{bmatrix}3 & -7 & 1 \\5 & 1 & \boxed{ 2 }\end{bmatrix}\begin{bmatrix}x_{1} \\x_{2} \\\boxed{ x_{3} }\end{bmatrix}$
Therefore, the second row of the result $b$ is $5x_{1}+x_{2}+2x_{3}$
- $5x_{1}+x_{2}+2x_{3}=2$

To show this generally, let $A$ and $\vec{x}$ be the general matrix and vector:
- $A$ has the size $m\times n$
- $\vec{x}$ has the size $n \times 1$
$$A\vec{x}=
\begin{bmatrix}
a_{11} & a_{12} & \dots & a_{1n} \\
a_{21} & a_{22} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \dots & a_{mn}
\end{bmatrix}\begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix}
$$
The matrix-vector product is:
$$
\begin{bmatrix}
a_{11}x_{1}+a_{12}x_{2}+\dots +a_{1n}x_{n} \\
a_{21}x_{1}+a_{22}x_{2}+\dots+a_{2n}x_{n} \\
\vdots \\
a_{m1}x_{1}+a_{m2}x_{2}+\dots +a_{mn}x_{n}
\end{bmatrix}
$$

> [!note] Note
> Since each [[1_Matrix#Row and Column Vectors|column vector]] of $A$ is **multiplied** by the respective component of the vector $\vec{x}$, the product $A\vec{x}$ can be thought of as a [[1_Vectors#Linear combinations|linear combination]] of the column vectors of $A$ 
> 
> $\begin{bmatrix}3 & -7 & 1 \\5 & 1 & 2\end{bmatrix}\begin{bmatrix}x_{1} \\x_{2} \\x_{3}\end{bmatrix}\implies x_{1}\begin{bmatrix}3\\5\end{bmatrix}+x_{2}\begin{bmatrix}-7\\1\end{bmatrix}+x_{3}\begin{bmatrix}1\\2\end{bmatrix}$


---

## Matrix multiplication
- when **two matrices** multiply
- **different** from [[1_Matrix#Scalar multiplication|Scalar multiplication]]

### Validity
- similar to [[#Product of Ax|Matrix-vector multiplication]], the number of **columns in the first matrix** must **equal** to the number of **rows in the second matrix**
	- otherwise, the multiplication is undefined
- the size of the resulting matrix will be:
	- rows: number of **rows in the first matrix**
	- columns: number of **columns in the second matrix**

For example, to verify if a $3\times 4$ matrix can be multiplied with a $4\times 2$ matrix, see the following diagram.
![[diag.png|400]]

### Operation
- perform [[3_Length and Angles#Dot products|dot products]] on **each row** of the first matrix onto **each column** of the second matrix

For example, multiplying $A$ and $B$ where:
$A=\begin{bmatrix}5&0&2\\-1&4&1\end{bmatrix}$ and $B=\begin{bmatrix}3&5&1\\-2&2&0\\10&0&0\end{bmatrix}$

Notice that:
- this multiplication is **possible** since the number of columns in $A$ (3) matches the number of rows in $B$ (3)
- the **resulting matrix** will have the size $2 \times 3$

Steps:
- **First row** of $A$, dot product with the **first column** of $B$, place the result in the first row and first column
	- ![[diag2.png|500]]
	- Dot product $=(5\times 3)+(0 \times -2)+(2 \times 10)=35$
	- The resulting matrix is now: $A\times B=\begin{bmatrix}35&\times&\times\\\times&\times&\times\end{bmatrix}$
- **First row** of $A$, dot product with the **second column** of $B$, place the result in the first row and second column
	- ![[diag3.png|500]]
	- Dot product $=(5\times 5)+(0\times 2)+(2 \times 0)=25$
	- The resulting matrix is now: $A\times B=\begin{bmatrix}35&25&\times\\\times&\times&\times\end{bmatrix}$
- **First row** of $A$, dot product with the **third column** of $B$, place the result in the first row and third column
	- ![[diag4.png|500]]
	- Dot product $=(5\times 1)+(0 \times 0)+(2 \times 0)=5$
	- The resulting matrix is now: $A\times B=\begin{bmatrix}35&25&5\\\times&\times&\times\end{bmatrix}$
- **Second row** of $A$, dot product with the **first column** of $B$, place the result in the second row and first column
	- ![[diag5.png|500]]
	- Dot product $=(-1\times 3)+(4 \times -2)+(1 \times 10)=-1$
	- The resulting matrix is now: $A\times B=\begin{bmatrix}35&25&5\\-1&\times&\times\end{bmatrix}$
- **Second row** of $A$, dot product with the **second column** of $B$, place the result in the second row and second column
	- ![[diag6.png|500]]
	- Dot product $=(-1 \times 5)+(4\times 2)+(1 \times 0)=3$
	- The resulting matrix is now: $A\times B=\begin{bmatrix}35&25&5\\-1&3&\times\end{bmatrix}$
- **Second row** of $A$, dot product with the **third column** of $B$, place the result in the second row and third column
	- ![[diag7.png|500]]
	- Dot product $=(-1 \times 1)+(4 \times 0)+(1 \times 0)=-1$
	- The resulting matrix is now: $A\times B=\begin{bmatrix}35&25&5\\-1&3&-1\end{bmatrix}$

$\therefore$ The product of $AB$ is:
$$
\begin{bmatrix}
35 & 25 & 5 \\
-1 & 3 & -1
\end{bmatrix}
$$

### Properties
- Matrix multiplication **IS NOT commutative**
	- $AB\neq BA$
	- For example, in the multiplication above, $AB$ is calculated but $BA$ is not possible
- Matrices **CANNOT** be cancelled
	- $AB=AC \centernot\implies \cancel{ A }B=\cancel{ A }C$
- If $AB=0$, it **DOES NOT** imply that either $A$ or $B$ is 0
	- $AB=0 \centernot\implies A=0 \lor B=0$
	- For example, multiplying $\begin{bmatrix}1&0\\0&0\end{bmatrix}\times \begin{bmatrix}0&0\\1&0\end{bmatrix}$, we get $\begin{bmatrix}0&0\\0&0\end{bmatrix}$.