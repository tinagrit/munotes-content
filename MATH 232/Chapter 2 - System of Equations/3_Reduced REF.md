Chapter 2.2 and 2.3

<div class="PWW">
<div data-callout-metadata="" data-callout-fold="" data-callout="warning" class="callout"><div class="callout-title" dir="auto"><div class="callout-icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-alert-triangle"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3"></path><path d="M12 9v4"></path><path d="M12 17h.01"></path></svg></div><div class="callout-title-inner">Narrow Screen</div></div><div class="callout-content">
<p dir="auto">This page includes wide mathematical graphics which may not fit well on your screen. Viewing this on a wider screen is highly recommended.</p>
</div></div>
</div>

## Reduced Row Echelon Form

- a [[1_Augmented Matrix#Augmented Matrix|matrix]] in [[2_Row Echelon#Row Echelon Form|Row-Echelon Form]] is **reduced** if:
	- any column with leading 1 have 0 for the rest of the column

Locate all the leading 1s in an REF matrix, if the values **above and below** them are **all 0**, then the matrix is in RREF.

> [!important] Every matrix has a **unique** reduced row-echelon form


### RREF Examples

| Matrix                                                            | Is RREF | Explanation                                                 |
| ----------------------------------------------------------------- | ------- | ----------------------------------------------------------- |
| $\begin{bmatrix}1&0&0&6\\0&1&1&5\\0&0&\boxed{ 1 }&1\end{bmatrix}$ | No      | The leading 1 in the third column (boxed) has a 1 above it. |
| $\begin{bmatrix}1&0&2&4\\0&1&0&7\\0&0&\boxed{ 1 }&8\end{bmatrix}$ | No      | The leading 1 in the third column (boxed) has a 2 above it. |
| $\begin{bmatrix}1&0&0&4\\0&1&0&7\\0&0&1&8\end{bmatrix}$           | **Yes** |                                                             |
| $\begin{bmatrix}1&0&0\\0&1&0\\0&0&1\end{bmatrix}$                 | **Yes** |                                                             |

---

## Converting to RREF (Gauss-Jordan)

An non-reduced [[#Row Echelon Form|REF]] matrix can be converted to RREF using **Gauss-Jordan Elimination**

Goal: convert this matrix (from above) to RREF form:
$$
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
0 & 0 & 1 & -\frac{1}{3} & -1 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
1. Locate all **leading 1s**
$$
\begin{bmatrix}
\boxed{ 1 } & 2 & 3 & 4 & 1 \\
0 & 0 & \boxed{ 1 } & -\frac{1}{3} & -1 \\
0 & 0 & 0 & \boxed{ 1 } & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$


2. Due to the [[#Reduced Row Echelon Form|RREF constraints]], all values **above and below** all leadings 1s have to be 0. Locate all values that don't follow this rule.
$$
\begin{bmatrix}
1 & 2 & \boxed{ 3 } & \boxed{ 4 } & 1 \\
0 & 0 & 1 & \boxed{\textstyle-\frac{1}{3} } & -1 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
- In this case: the $\boxed{ 3 }$ is above 1 in the third column. The $\boxed{ 4 }$ and $\boxed{ \textstyle-\frac{1}{3} }$ are above the 1 in the fourth column.


3. Start from the **bottom-right-most** value, **subtract** the row by the product of that value and the row **with a leading 1** in the same column
   $R_{n}\mapsto R_{n}-(\text{value}\times R$ (with a leading 1 in the same column) $)$

- In this case, $\boxed{ \textstyle-\frac{1}{3} }$ is the bottom-right-most value.
- Subtract the row that the value is in ($R_{2}$) by the product of $-\frac{1}{3}\times R_{3}$ (Row $R_{3}$ is chosen because $R_{3}$ has a leading 1 in the same column as $\boxed{ \textstyle-\frac{1}{3} }$)
- $R_{2}\mapsto R_{2}-\left(-\dfrac{1}{3}R_{3}\right)$

$$
\begin{matrix}
R_{2}\Rightarrow & 0 & 0 & 1 & -\frac{1}{3} & -1 \\
-\frac{1}{3}R_{3}\Rightarrow & 0 & 0 & 0 & -\frac{1}{3} & 0 \\
\hline \\
R_{2}\mapsto & 0 & 0 & 1 & 0 & -1
\end{matrix}
$$


4. Repeat **Step 2-3** until the matrix is in the RREF format
- Step 2: Locate the remaining non-reduced values
$$
\begin{bmatrix}
1 & 2 & \boxed{ 3 } & \boxed{ 4 } & 1 \\
0 & 0 & 1 & 0 & -1 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
- Step 3: Subtract bottom-right-most value (in this case $\boxed{ 4 }$)
	- $R_{1}\mapsto R_{1}-(4R_{3})$
$$
\begin{matrix}
R_{1}\Rightarrow & 1 & 2 & 3 & 4 & 1 \\
4R_{3}\Rightarrow & 0 & 0 & 0 & 4 & 0 \\
\hline \\
R_{1}\mapsto & 1 & 2 & 3 & 0 & 1
\end{matrix}
$$
- Step 2: Locate the remaining non-reduced values
$$
\begin{bmatrix}
1 & 2 & \boxed{ 3 } & 0 & 1 \\
0 & 0 & 1 & 0 & -1 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
- Step 3: Subtract the last value $\boxed{ 3 }$
	- $R_{1}\mapsto R_{1}-(3R_{2})$
$$
\begin{matrix}
R_{1}\Rightarrow & 1 & 2 & 3 & 0 & 1 \\
3R_{2}\Rightarrow & 0 & 0 & 3 & 0 & -3 \\
\hline \\
R_{1}\mapsto & 1 & 2 & 0 & 0 & 4
\end{matrix}
$$
- After mapping, the matrix becomes:
$$
\begin{bmatrix}
1 & 2 & 0 & 0 & 4 \\
0 & 0 & 1 & 0 & -1 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
- This is now in RREF format.

---

## Applying RREF
*Also see* [[2_Row Echelon#Interpreting REF|Interpreting REF]]

### Solution Set
To find the solution set from an RREF,
- **assign** variables to each [[2_Row Echelon#Type of Solutions|free variable]]
	- this can be anything $\in\mathbb{R}$
- **solve** each [[2_Row Echelon#Type of Solutions|leading variables]] in terms of those variables

For example, solving the RREF augmented matrix above:
$$
\begin{bmatrix}
1 & 2 & 0 & 0 & 4 \\
0 & 0 & 1 & 0 & -1 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
Since $x_{2}$ is the free variable, let $t=x_{2}$.
A system of equations for the rest of the variables can be derived.
- $x_{1}+t=4 \implies x_{1}=4-t$
- $x_{3}=-1$
- $x_{4}=0$

Then, set up a set of solutions
$s=\left\{ \vec{x} \mid \vec{x}=\begin{bmatrix}4-t\\-1\\t\end{bmatrix},t\in \mathbb{R} \right\}$

Simplify by factoring the free variables out
$s=\left\{ \vec{x}\mid \vec{x}=t\begin{bmatrix}-1\\0\\1\end{bmatrix}+\begin{bmatrix}4\\-1\\0\end{bmatrix},t\in \mathbb{R} \right\}$

$\therefore$ This is a line through $P(4,-1,0)$


### Linear Independence
*Also see* [[2_Vector Spans and Basis#Linear independence|Linear independence]]

A set of vectors is linearly independent if:
- when setting its [[2_Vector Spans and Basis#Span|span]] $=0$, the **trivial solution** (all variables are 0) is the only solution

Therefore, an augmented matrix of a [[1_Augmented Matrix#Homogeneous Systems|homogeneous system]] can be **set up and solved** to see if the trivial solution is the only one.

#### Linear Independence Examples

>  Are the vectors in $S$ linearly independent? Given:
>  $S=\left\{ \begin{bmatrix}1\\1\\0\\1\\1\end{bmatrix},\begin{bmatrix}2\\3\\1\\3\\3\end{bmatrix},\begin{bmatrix}0\\1\\1\\1\\1\end{bmatrix} \right\}$

The span of $S$ is: $c_{1}\begin{bmatrix}1\\1\\0\\1\\1\end{bmatrix}+c_{2}\begin{bmatrix}2\\3\\1\\3\\3\end{bmatrix}+c_{3}\begin{bmatrix}0\\1\\1\\1\\1\end{bmatrix}\mid c_{1},c_{2},c_{3}\in \mathbb{R}$

Set this span equal to 0 and set up an augmented matrix:
$M=\begin{bmatrix}1&2&0&0\\1&3&1&0\\0&1&1&0\\1&3&1&0\\1&3&1&0\end{bmatrix}\implies \text{rref}(M)=\begin{bmatrix}1&0&0&0\\0&1&0&0\\0&0&1&0\\0&0&0&0\\0&0&0&0\end{bmatrix}$

Since there are 3 variables and the [[2_Row Echelon#Ranks|rank]]$(M)$ is 3, there is no [[2_Row Echelon#Type of Solutions|free variables]], and therefore there is only **one solution** (trivial)

$\therefore S$ is linearly independent 


### Spans and Dimensions
From a set of vectors, set up an augmented matrix of its **span** $=0$ (same as what we did in [[#Linear Independence]])

If the RREF form of that matrix is [[#Consistency|consistent]],
- the [[#Ranks|rank]] is **equal to** the dimensions of the set
	- denoted $\text{dim}(set)$

| Rank/<br>Dimension | Spans<br>in $\mathbb{R}^{1}$ | Spans<br>in $\mathbb{R}^{2}$ | Spans<br>in $\mathbb{R}^{3}$ | Spans<br>in $\mathbb{R}^{4}$ |
| ------------------ | ---------------------------- | ---------------------------- | ---------------------------- | ---------------------------- |
| 1                  | All $\mathbb{R}^{1}$         | line                         | line                         | line                         |
| 2                  | -                            | All $\mathbb{R}^{2}$         | plane                        | plane                        |
| 3                  | -                            | -                            | All $\mathbb{R}^{3}$         | hyperplane                   |
| 4                  | -                            | -                            | -                            | All $\mathbb{R}^{4}$         |

To check whether a set forms a [[2_Vector Spans and Basis#Basis|basis]], check if the set:
- is linearly independent
- spans the space (see table above)

#### Spans and Dimensions Examples

> Does $S$ form a basis for $\mathbb{R}^{3}$? Given:
> $S=\left\{ \begin{bmatrix}-2\\2\\1\end{bmatrix},\begin{bmatrix}3\\-1\\2\end{bmatrix} \right\}$

1. Determine if $S$ is linearly independent
	- Set up an augmented matrix for the span of $S$ equal to $0$
	- $M=\begin{bmatrix}-2&3&0\\2&-1&0\\1&2&0\end{bmatrix}\implies \text{rref}(M)=\begin{bmatrix}1&0&0\\0&1&0\\0&0&0\end{bmatrix}$
	- There is no free variables, meaning that $S$ is **linearly independent**
2. Determine if $S$ spans $\mathbb{R}^{3}$
	- In the RREF shown above, the dimension of $S$ is 2 ($\text{dim}(S)=2$)
	- This means that $S$ only spans **a plane**

$\therefore S$ *does not* form a basis for $\mathbb{R}^{3}$


> Does $S$ form a basis for $\mathbb{R}^{3}$? Given:
> $S=\left\{ \begin{bmatrix}-2\\2\\1\end{bmatrix},\begin{bmatrix}3\\-1\\2\end{bmatrix},\begin{bmatrix}2\\1\\1\end{bmatrix} \right\}$

1. Determine if $S$ is linearly independent
	- Set up an augmented matrix for the span of $S$ equal to $0$
	- $M=\begin{bmatrix}-2&3&2&0\\2&-1&1&0\\1&2&1&0\end{bmatrix}$
	- $\implies \text{rref}(M)=\begin{bmatrix}1&0&0&0\\0&1&0&0\\0&0&1&0\end{bmatrix}$
	- There is no free variables, meaning that $S$ is **linearly independent**
2. Determine if $S$ spans $\mathbb{R}^{3}$
	- In the RREF shown above, the dimension of $S$ is 3 ($\text{dim}(S)=3$)
	- This means that $S$ spans $\mathbb{R}^{3}$

$\therefore S$ **forms** a basis for $\mathbb{R}^{3}$