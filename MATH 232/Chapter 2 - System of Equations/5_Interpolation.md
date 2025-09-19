Chapter 2.4


## Polynomial Interpolation
is used to find 
- the **polynomial** equation through a **set of points**
- each point having different x-values.

With $n$ number of points,
- there is a polynomial with **degree at most**  $n-1$
- for example, 
	- 2 points → degree 1 (a line)
	- 3 points → degree 2 (a parabola)

If the $n$ points include $(x_{1},y_{1}),(x_{2},y_{2}),\dots,(x_{n}y_{n})$, the polynomial should have the form:
$$
y=a_{0}+a_{1}x+a_{2}x^{2}+a_{3}x^{3}+\dots+a_{n-2}x^{n-2}+a_{n-1}x^{x-1}
$$
- For each point given, **plug** $x$ and $y$ into the equation. 
- The number of equations created should be equal to the number of points.


### Interpolation example

> Find a polynomial interpolation through the following points.
> $(-4,-2),(-2,1),(2,-3),(4,3)$
> ![[Screenshot 2025-02-04 at 3.57.04 PM.png|300]]


Since there are 4 points, we can have up to degree 3.
Setting up:
$$
y=a_{0}+a_{1}x+a_{2}x^{2}+a_{3}x^{3}
$$
where $(x,y)$$=(-4,-2),(-2,1),(2,-3),(4,3)$

We have:
$$
\begin{align}
-2 & = a_{0}+a_{1}(-4)+a_{2}(-4)^{2}+a_{3}(-4)^{3} \\
1 & = a_{0}+a_{1}(-2)+a_{2}(-2)^{2}+a_{3}(-2)^{3} \\
-3 & =a_{0}+a_{1}(2)+a_{2}(2)^{2}+a_{3}(2)^{3} \\
3 & =a_{0}+a_{1}(4)+a_{2}(4)^{2}+a_{3}(4)^{3}
\end{align}
$$
$$
\Downarrow
$$
$$
\begin{align}
a_{0}-4a_{1}+16a_{2}-64a_{3} & =-2 \\
a_{0}-2a_{1}+4a_{2}-8a_{3}  & =1\\
a_{0}+2a_{1}+4a_{2}+8a_{3}  & =-3\\
a_{0}+4a_{1}+16a_{2}+64a_{3} & =3
\end{align}
$$

Using the system of linear equations, set up an [[1_Augmented Matrix|augmented matrix]].
$$
\begin{bmatrix}
1 & -4 & 16 & -64 & -2 \\
1 & -2 & 4 & -8 & 1 \\
1 & 2 & 4 & 8 & -3 \\
1 & 4 & 16 & 64 & 3
\end{bmatrix}
$$
Concerting this matrix into [[3_Reduced REF|RREF]], the result is:
$$
\begin{bmatrix}
1 & 0 & 0 & 0 & -\dfrac{3}{2} \\
0 & 1 & 0 & 0 & -\dfrac{37}{24} \\
0 & 0 & 1 & 0 & \dfrac{1}{8} \\
0 & 0 & 0 & 1 & \dfrac{13}{96}
\end{bmatrix}
$$

Therefore, $a_{0}=-\dfrac{3}{2}$, $a_{1}=-\dfrac{37}{24}$, $a_{2}=\dfrac{1}{8}$, and $a_{3}=\dfrac{13}{96}$

The polynomial that passes through the points is:
$$
y=-\dfrac{3}{2}-\dfrac{37}{24}x+\dfrac{1}{8}x^{2}+\dfrac{13}{96}x^{3}
$$

![[Screenshot 2025-02-04 at 4.11.40 PM.png|400]]
