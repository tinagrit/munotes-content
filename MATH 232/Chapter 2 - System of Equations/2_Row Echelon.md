Chapter 2.1 and 2.2

<div class="PWW">
<div data-callout-metadata="" data-callout-fold="" data-callout="warning" class="callout"><div class="callout-title" dir="auto"><div class="callout-icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-alert-triangle"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3"></path><path d="M12 9v4"></path><path d="M12 17h.01"></path></svg></div><div class="callout-title-inner">Narrow Screen</div></div><div class="callout-content">
<p dir="auto">This page includes wide mathematical graphics which may not fit well on your screen. Viewing this on a wider screen is highly recommended.</p>
</div></div>
</div>

## Row Echelon Form

- a [[1_Augmented Matrix#Augmented Matrix|matrix]] is in row echelon form (REF) if:
	- if there is an **all 0s** row, it is **at the bottom**
	- for any other row, the **first non-zero must be 1** (leading 1)
	- from top to bottom, the **leading 1** in the lower row is **to the right** of the upper row

### REF Example

| Matrix                                                                      | Is REF  | Explanation                                                                          |
| --------------------------------------------------------------------------- | ------- | ------------------------------------------------------------------------------------ |
| $\begin{bmatrix}1 & 0 & 0 & 5 \\0 & 0 & 1 & 3 \\0 & 1 & 0 & 4\end{bmatrix}$ | *No*    | The leading 1 in the third row is to **the left** of the leading 1 in the second row |
| $\begin{bmatrix}1&-3&5\\0&0&0\\0&0&1\end{bmatrix}$                          | *No*    | The second row is all 0s. It should be at the bottom.                                |
| $\begin{bmatrix}1&0&0\\0&1&0\\0&0&4\end{bmatrix}$                           | *No*    | The first non-zero in the third row is 4, not 1.                                     |
| $\begin{bmatrix}1&0&2&4\\0&1&0&7\\0&0&1&8\end{bmatrix}$                     | **Yes** |                                                                                      |
| $\begin{bmatrix}1&0&0&4\\0&1&0&7\\0&0&1&8\end{bmatrix}$                     | **Yes** | This is also a [[3_Reduced REF#Reduced Row Echelon Form\|reduced REF]] (RREF).       |

### Pivot positions
- In an REF matrix, the **leading 1s** are the **pivot positions**
- The column with a leading 1, is a **pivot column**

For example, the boxed positions are the pivot positions
$\begin{bmatrix}\boxed{ 1 }&1&2&4\\0&\boxed{ 1 }&0&1\\0&0&\boxed{ 1 }&8\end{bmatrix}$
The first 3 columns are the pivot columns.


### Solving REF Matrix Examples

> Solve the linear system with $x,y,z$:
$$
\begin{bmatrix}
1 & 0 & 0 & 5 \\
0 & 1 & 0 & -2 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$

- First line $\implies x=5$
- Second line $\implies y=-2$
- However, on the third line, it implies that $0=1$

$\therefore$ No solutions


> Solve the linear system with $w,x,y,z$:
$$
\begin{bmatrix}
1 & 2 & 0 & 2 & -3 \\
0 & 0 & 1 & -5 & 8 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$

Translate into linear equations
- $w+2x+2z=-3$
	- $\implies w=-2x-2z-3$
- $y-5z=8$  
	- $\implies y=5z+8$
- $0=0$ 

Since there are not enough distinct equations to solve for each variable, these equations:
- $w=-2x-2z-3$
- $y=5z+8$
hold true for any value of $x$ and $z$

$\therefore$ The solution set is:
$\left\{ \begin{bmatrix}-2x-2z-3\\x\\5z+8\\z\end{bmatrix} \mid x,z\in \mathbb{R} \right\}$

Factoring out $x$ and $z$:
$\left\{ x\begin{bmatrix}-2\\1\\0\\0\end{bmatrix}+z\begin{bmatrix}-2\\0\\5\\1\end{bmatrix} +\begin{bmatrix}-3\\0\\8\\0\end{bmatrix} \mid x,z \in \mathbb{R} \right\}$

This is a [[1_Vectors#Vector equation of planes|plane]] through $P(-3,0,8,0)$ in $\mathbb{R}^{4}$


---

## Converting to REF (Gaussian)

A non-REF matrix can be converted to REF using **Gaussian Elimination**

Goal: convert this matrix to REF form:
$$
\begin{bmatrix}
2 & 4 & 6 & 8 & 2 \\
0 & 0 & 0 & 0 & 0 \\
2 & 4 & 6 & 2 & 2 \\
3 & 6 & 18 & 9 &-6 \\
4 & 8 & 12 & 10 & 4
\end{bmatrix}
$$
1. If there is a **all-0s row**, move it to the bottom 
$$
\begin{bmatrix}
2 & 4 & 6 & 8 & 2 \\
2 & 4 & 6 & 2 & 2 \\
3 & 6 & 18 & 9 &-6 \\
4 & 8 & 12 & 10 & 4 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$

2. Locate the top-left non-zero value, **divide the top row** with that value to introduce a leading 1 
- In this case, $R_{1}\mapsto \dfrac{1}{2}R_{1}$ 
$$
\begin{bmatrix}
\boxed{ 2 } & 4 & 6 & 8 & 2 \\
2 & 4 & 6 & 2 & 2 \\
3 & 6 & 18 & 9 &-6 \\
4 & 8 & 12 & 10 & 4 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
\begin{array}{}
\to \\
\text{} \\
\text{} \\
\text{} \\
\text{}
\end{array}
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
2 & 4 & 6 & 2 & 2 \\
3 & 6 & 18 & 9 &-6 \\
4 & 8 & 12 & 10 & 4 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
 - After the division, if the column below the located value is all 0, skip step 3

3. For each non-zero row, locate the value in the same column from Step 2 and **subtract the row** by the first row multiplied by that value 
$$
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
\boxed{ 2 } & 4 & 6 & 2 & 2 \\
\boxed{ 3 } & 6 & 18 & 9 &-6 \\
\boxed{ 4 } & 8 & 12 & 10 & 4 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
- For $R_{2}$, the first value is $2$, $R_{2}\mapsto 2R_{1}$
$$
\begin{matrix}
R_{2}\Rightarrow & 2 & 4 & 6 & 2 & 2 \\
2R_{1}\Rightarrow & 2 & 4 & 6 & 8 & 2 \\
\hline \\
R_{2}\mapsto & 0 & 0 & 0 & -6 & 0
\end{matrix}
$$
- For $R_{3}$, the first value is $3$, $R_{3}\mapsto 3R_{1}$
$$
\begin{matrix}
R_{3}\Rightarrow & 3 & 6 & 18 & 9 & -6 \\
3R_{1}\Rightarrow & 3 & 6 & 9 & 12 & 3 \\
\hline \\
R_{3}\mapsto & 0 & 0 & 9 & -3 & -9
\end{matrix}
$$
- For $R_{4}$, the first value is $4$, $R_{4}\mapsto 4R_{1}$
$$
\begin{matrix}
R_{4}\Rightarrow & 4 & 8 & 12 & 10 & 4 \\
4R_{1}\Rightarrow & 4 & 8 & 12 & 16 & 4 \\
\hline \\
R_{4}\mapsto & 0 & 0 & 0 & -6 & 0
\end{matrix}
$$
- After all mapping, the matrix becomes:
$$
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 9 & -3 & -9 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$

4. **Reorder** and group same rows 
$$
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
0 & 0 & 9 & -3 & -9 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$

5. **Ignore the top** row, and repeat all steps until the matrix is in REF format
- Step 2: divide top row (now $R_{2}$) 
$$
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
0 & 0 & \boxed{ 9 } & -3 & -9 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
\begin{array}{}
\text{} \\
\to \\
\text{} \\
\text{} \\
\text{}
\end{array}
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
0 & 0 & 1 & -\frac{1}{3} & -1 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
- Skip Step 3 since all values below $\boxed{9}$ are 0
- Back to Step 2: divide top row (now $R_{3}$)
$$
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
0 & 0 & 1 & -\frac{1}{3} & -1 \\
0 & 0 & 0 & \boxed{ -6 } & 0 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
\begin{array}{}
\text{} \\
\text{} \\
\to \\
\text{} \\
\text{}
\end{array}
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
0 & 0 & 1 & -\frac{1}{3} & -1 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & -6 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
- Step 3: Subtract $R_{4}$ by $-6(R_{3})$
$$
\begin{matrix}
R_{4}\Rightarrow & 0 & 0 & 0 & -6 & 0 \\
-6R_{3}\Rightarrow & 0 & 0 & 0 & -6 & 0 \\
\hline \\
R_{4}\mapsto & 0 & 0 & 0 & 0 & 0
\end{matrix}
$$
- After mapping, the matrix becomes:
$$
\begin{bmatrix}
1 & 2 & 3 & 4 & 1 \\
0 & 0 & 1 & -\frac{1}{3} & -1 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
- This is now in REF format


---

## Interpreting REF
*Also see* [[3_Reduced REF#Applying RREF|Applying RREF]]

### Ranks
In an REF (or [[3_Reduced REF#Reduced Row Echelon Form|RREF]]) matrix, 
- a **rank** is the number of [[2_Row Echelon#Pivot positions|pivot columns]]
- denoted by $\text{rank}(M)$

For example, the following matrix has a $\text{rank}(M)=3$
$M=\begin{bmatrix}1 & 2 & 3 & 4 & 1 \\0 & 0 & 1 & -\frac{1}{3} & -1 \\0 & 0 & 0 & 1 & 0 \\0 & 0 & 0 & 0 & 0 \\0 & 0 & 0 & 0 & 0\end{bmatrix}$


### Consistency
*See more:* [[1_Augmented Matrix#Solutions|Solutions of a Linear Equation]]

A linear system is **consistent** if:
- it has at least one solution

If an REF matrix has a row with **all 0s except for a 1 at the end**, it is *not consistent*
- For example, $\begin{bmatrix}0&0&0&1\end{bmatrix}$ would imply that $0x+0y+0z=1 \implies 0=1$ which is not true.

Alternate definition: A matrix is **consistent** if and only if:
- the [[#Ranks|rank]] of the [[1_Augmented Matrix#Coefficient Matrix|coefficient matrix]] is **equal to** the rank of the whole matrix
- aka. the leading 1 can't be in the equal column


### Type of Solutions
In a [[#Consistency|consistent]] REF (or [[3_Reduced REF#Reduced Row Echelon Form|RREF]]) matrix, 
- the [[#Ranks|rank]] is **equal to** the number of **leading variables**
- the non-leading variables are **free variables**

For example,
- an augmented matrix with 5 variables has 3 pivot columns
	- $\implies3$ leading variables
	- $\implies 5-3=2$ free variables

The type of solution set can be determined by the number of **free variables**.

| # of Free Variables | Type of Solution Set |
| ------------------- | -------------------- |
| No free variables   | Single point         |
| 1 free variable     | Line                 |
| 2 free variables    | Plane                |
| 3 free variables    | Hyperplane           |
| $\vdots$            | $\vdots$             |

An accurate solution set can be derived from the [[3_Reduced REF#Solution Set|Reduced Row-Echelon form]] 