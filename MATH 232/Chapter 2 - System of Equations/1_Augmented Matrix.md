Chapter 2.1

<div class="PWW">
<div data-callout-metadata="" data-callout-fold="" data-callout="warning" class="callout"><div class="callout-title" dir="auto"><div class="callout-icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-alert-triangle"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3"></path><path d="M12 9v4"></path><path d="M12 17h.01"></path></svg></div><div class="callout-title-inner">Narrow Screen</div></div><div class="callout-content">
<p dir="auto">This page includes wide mathematical graphics which may not fit well on your screen. Viewing this on a wider screen is highly recommended.</p>
</div></div>
</div>

## Linear Equation
is a [[1_Vectors#Linear combinations|linear combination]] of each vector components; can be expressed with
$$
a_{1}x_{1}+a_{2}x_{2}+\dots+ a_{n}x_{n}=b
$$
where
- $a_{1},a_{2},\dots ,a_{n},b$ are constants 
- $a_{i}$ cannot all be 0

If $b=0$, then the equation is called a **homogenous linear equation**.

For example,
- $x+y=0$ is homogenous
- $2x+3y=4$ is *not* homogenous

The **solution set** refers to all values that satisfy the equation
See [[3_Reduced REF#Solution Set|RREF]] for finding the solution set.

For example, $x+y=0$ can include
$\left\{ \dots,(1,-1),(2,-2),(3,-3),\dots \right\}$


---
## System of Equations
consist of **multiple** linear equations
$$
\begin{align}
a_{11}x_1 &+ a_{12}x_2 + \cdots + a_{1n}x_n =  b_1 \\
a_{21}x_1 &+ a_{22}x_2 + \cdots + a_{2n}x_n = b_2 \\
\vdots\\
a_{m1}x_1 &+ a_{m2}x_2 + \cdots + a_{mn}x_n = b_m
\end{align}
$$

where
- $a_{i},b_{i}$ are constants
- in each line, $a_{i}$ cannot all be 0

### Solutions
- a system is **consistent** if it has $\geq 1$ solutions
- any linear system can have:
	- 1 solution,
	- no solutions, or
	- infinite number of solutions

#### System of lines
- a system of [[1_Vectors#Vector equation of lines|lines]] can have:
	- 1 solution if **lines intersect**![[IMG_9B2AAD7F2C84-1.jpeg|300]]
	- no solutions if **lines are parallel![[IMG_F6B0FA4A290D-1.jpeg|300]]**
	- infinite number of solutions if **lines overlap**![[IMG_9B79BA3D3A94-1.jpeg|300]]

#### System of planes
- a system of [[1_Vectors#Vector equation of planes|planes]] can have:
	- 1 solution if **3 or more planes intersect** at one point![[IMG_59FD89321653-1.jpeg|100]]
	- no solutions if **planes are parallel**![[IMG_BBE3BB3B836E-1.jpeg|100]]![[IMG_F734A240E9F2-1.jpeg|100]]
	- no solutions if there is **no common intersection**![[IMG_B47F1B8CE8D0-1.jpeg|100]]![[IMG_1DBD8E046FD5-1 1.jpeg|100]]
	- a line solution (infinite) if the planes **intersect as a line**![[IMG_AF7A0BD97E1B-1.jpeg|100]]
	- infinite number of solutions if **planes overlap**![[IMG_F6FB684F781E-1.jpeg|100]]

---
## Augmented Matrix
represents a system of equations by:
- only showing the **coefficients**
- ignore the $+$ and $=$

$$
\begin{align}
a_{11}x_1 &+ a_{12}x_2 + \cdots + a_{1n}x_n =  B_1 \\
a_{21}x_1 &+ a_{22}x_2 + \cdots + a_{2n}x_n =  B_2 \\
\vdots\\
a_{m1}x_1 &+ a_{m2}x_2 + \cdots + a_{mn}x_n =  B_n
\end{align}
$$
$$
\downarrow
$$
$$
\begin{bmatrix}
a_{11} & a_{12} & \dots & a_{1n} & B_{1} \\
a_{21} & a_{22} & \dots & a_{2n} & B_{2} \\
\vdots&\vdots&\ddots&\vdots&\vdots \\
a_{m 1} & a_{m2} & \dots & a_{mn} & B_{n}
\end{bmatrix}
$$

An *optional* vertical dash can be used to distinguish the equal sign:
$$
\left[\begin{array}{@{}cccc|c@{}}
a_{11} & a_{12} & \dots & a_{1n} & B_{1} \\
a_{21} & a_{22} & \dots & a_{2n} & B_{2} \\
\vdots&\vdots&\ddots&\vdots&\vdots \\
a_{m 1} & a_{m2} & \dots & a_{mn} & B_{n}
\end{array}\right]
$$

For example:
> Write the following system of equations in the form of augmented matrix:
> $\begin{align}w-2x+2y-3z & =4 \\2w+3x-y+5z&=-5\end{align}$

$$
\begin{bmatrix}
1 & -2 & 2 & -3 & 4 \\
2 & 3 & -1 & 5 & -5
\end{bmatrix}
\text{ or }
\left[ 
\begin{array}{a{}cccc|ca{}}
1 & -2 & 2 & -3 & 4 \\
2 & 3 & -1 & 5 & -5
\end{array}
\right] 

$$

### Homogeneous Systems
Similar to linear [[#Linear Equation|equations]], a matrix with the last column being all 0s is a **homogeneous** system.
$$
\left[\begin{array}{@{}cccc|c@{}}
a_{11} & a_{12} & \dots & a_{1n} & 0 \\
a_{21} & a_{22} & \dots & a_{2n} & 0 \\
\vdots&\vdots&\ddots&\vdots&\vdots \\
a_{m 1} & a_{m2} & \dots & a_{mn} & 0
\end{array}\right]
$$
Every homogenous system has **at least one** solution, the **trivial** solution.
- where all variables are $=0$

However, if there is a **nontrivial** solution (not all variables are 0), then there are **infinitely as many** solutions.

The solution set to a homogenous system is **always**
- [[4_Subspaces#Closure under addition|Closed under addition]] and
- [[4_Subspaces#Closure under scalar multiplication|Closed under scalar multiplication]]
Therefore, the solution set is a **[[4_Subspaces#Subspaces|Subspace]]**, also called the **Solution Space**


### Coefficient Matrix
In a linear system, a **coefficient matrix** is the matrix that does not include the equal (last) column

For example, the coefficient matrix of $M$ is $N$
$$
M=\begin{bmatrix}
1 & 2 & 3 & 4 \\
5 & 6 & 7 & 8 \\
9 & 10 & 11 & 12
\end{bmatrix},
N=\begin{bmatrix}
1 & 2 & 3 \\
5 & 6 & 7 \\
9 & 10 & 11
\end{bmatrix}
$$

### Triangular system
includes a lot of 0 in the matrix, and is easy to solve

For example:
$$
\begin{align}
\begin{bmatrix} 
w & x & y & z & =\\
\downarrow & \downarrow & \downarrow & \downarrow & \downarrow\\\\
1 & -5 & 4 & -4 & 3 \\
0  & 20 & -4 & -\dfrac{1}{5} & 8 \\
0 & 0 & 3 & 2 & 13  \\
0 & 0 & 0 & 1 & 5
\end{bmatrix}
\end{align}


$$

Work this out from the **bottom up**

- $z=5$
- $3y+2z=13$
	- $\implies 3y+2(5)=13$
	- $\implies y=1$
- $20x-4y-\dfrac{1}{5}z=8$
	- $\implies 20x-4(1)-\dfrac{1}{5}(5)=8$
	- $\implies x=\dfrac{13}{20}$
- $w-5x+4y-4z=3$
	- $\implies w-5\left( \dfrac{13}{20} \right)+4(1)-4(5)=3$
	- $\implies w=19+\dfrac{13}{4}$

$\therefore z=5,y=1,x=\dfrac{13}{20},w=19+\dfrac{13}{4}$


### Elementary Row Operations
Also see [[1_Matrix#Basic matrix operations|Basic Matrix Operations]]

These **operations** can be performed on any linear matrix:
- **multiply** a row by a non-zero scalar
	- $\begin{bmatrix}3&5&7\end{bmatrix}$
	- $\to 2\times\begin{bmatrix}3&5&7\end{bmatrix}$
	- $\to \begin{bmatrix}6&10&14\end{bmatrix}$
- **swap** any two rows
	- $R_{1}\mapsto R_{2}$ and $R_{2}\mapsto R_{1}$ ($\mapsto$ called **maps to**)
	- $\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}\begin{array}{}\searrow\\\nearrow\\\text{}\end{array} \begin{bmatrix}4&5&6\\1&2&3\\7&8&9\end{bmatrix}$
- **add** a multiple of one row to another
	- $\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}$
	- Subtract row 1 from row 4
	- $R_{2}\mapsto R_{2}-R_{1}$
	- $\to\begin{bmatrix}1&2&3\\4-1&5-2&6-3\\7&8&9\end{bmatrix}$
	- $\to \begin{bmatrix}1&2&3\\3&3&3\\7&8&9\end{bmatrix}$
