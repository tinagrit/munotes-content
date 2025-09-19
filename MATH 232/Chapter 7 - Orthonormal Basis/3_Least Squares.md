Chapter 7.3


## Line of Best Fit
Also see [[5_Interpolation|Interpolation]], where all points fit perfectly on the line.

- linear **regression**
- putting a best line through a **set of points**
- **not all points** lie on the line

For example, trying to find a linear equation $a+bx=y$ to fit the following points:
- $(1,2)$
- $(2,4)$
- $(3,6)$
- $(4,7)$

We can plug in the $x$'s and $y$'s into the linear equation, and solve the system of equations.
$$
\begin{align}
a+b(1) & =2 \\
a+b(2) & =4 \\
a+b(3) & =6 \\
a+b(4) & =7
\end{align}\implies \begin{bmatrix}
1 & 1 \\
1 & 2 \\
1 & 3 \\
1 & 4
\end{bmatrix}\begin{bmatrix}
a \\
b
\end{bmatrix}=\begin{bmatrix}
2 \\
4 \\
6 \\
7
\end{bmatrix}
$$

If we set up an [[1_Augmented Matrix|augmented matrix]] for this system, we will find out that the system is **inconsistent**, that is, it is **impossible** to create a linear equation that goes through all points.
$$\left[\begin{array}{@{}cc|c@{}}
1 & 1 & 2 \\
1 & 2 & 4 \\
1 & 3 & 6 \\
1 & 4 & 7
\end{array} \right]\sim \left[ \begin{array}{@{}cc|c@{}}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
0 & 0 & 0
\end{array} \right]
$$

Instead of finding the exact linear equation, which doesn't exist, we can use draw a line that is **close enough** to all of the points, even if not all the points are directly on the line.


### Method of Least Squares
Using the example above, we are trying to solve:
$$
\begin{bmatrix}
1 & 1 \\
1 & 2 \\
1 & 3 \\
1 & 4
\end{bmatrix}\begin{bmatrix}
a \\
b
\end{bmatrix}=\begin{bmatrix}
2 \\
4 \\
6 \\
7
\end{bmatrix}
$$
This can be written as a $A\vec{x}=\vec{b}$ problem where:
- $A$ is a matrix
- $\vec{x}$ is the solution set (the coefficients that we are looking for)
- $\vec{b}$ is a vector

If the system if **consistent**, we should have:
$$
A\vec{x}-\vec{b}=\vec{0}
$$
However, we've already shown that it is **not consistent**. If we use a solution set $\vec{x}$ that is off from some points provided, we will have:
$$
A\vec{x}-\vec{b}=\vec{e}
$$
where $\vec{e}$ is the error measuring how far the approximation is from the actual points.

The line of **best** fit can be found by **minimizing** the magnitude of $\lVert \vec{e} \rVert$. 

Since $\lVert \vec{e} \rVert=\sqrt{ e_{1}^{2}+e_{2}^{2}+\dots+e_{n}^{2} }$
The easiest way to minimize this value, is to minimize $\lVert \vec{e} \rVert^{2}$ instead, where:
$$
\lVert \vec{e} \rVert^{2}=e_{1}^{2}+e_{2}^{2}+\dots+e_{n}^{2}
$$
This is why the process is called the method of **Least Squares**.


> [!success] Formula for the Method of Least Squares
> $\vec{x}=(A^{T}A)^{-1}A^{T}\vec{b}$


Continuing on with the example above, we have that:
- $A=\begin{bmatrix}1 & 1 \\1 & 2 \\1 & 3 \\1 & 4\end{bmatrix} \implies A^{T}=\begin{bmatrix}1&1&1&1\\1&2&3&4\end{bmatrix}$
- $\vec{x}=\begin{bmatrix}a\\b\end{bmatrix}$
- $\vec{b}=\begin{bmatrix}2 \\4 \\6 \\7\end{bmatrix}$

Using a computer, we can calculate:
- $A^{T}A=\begin{bmatrix}1&1&1&1\\1&2&3&4\end{bmatrix}\begin{bmatrix}1 & 1 \\1 & 2 \\1 & 3 \\1 & 4\end{bmatrix}=\begin{bmatrix}4&10\\10&30\end{bmatrix}$
- $(A^{T}A)^{-1}=\begin{bmatrix} \frac{3}{2} & -\frac{1}{2} \\ -\frac{1}{2} & \frac{1}{5} \end{bmatrix}$
- $(A^{T}A)^{-1}A^{T}\vec{b}=\vec{x}=\begin{bmatrix} \frac{1}{2}\\ \frac{17}{10}  \end{bmatrix}$
	- $\implies a=\dfrac{1}{2}$
	- $\implies b=\dfrac{17}{10}$

$\therefore$ The linear line of best fit for $(1,2),(2,4),(3,6),(4,7)$ is $\dfrac{1}{2}+\dfrac{17}{10}x=y$
