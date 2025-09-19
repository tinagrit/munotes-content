Chapter 6.2 and 6.3


## Similar matrices
Recall the [[2_Coordinates#Matrix mapping with basis|Change of Basis in a Matrix Mapping]] formula:
$$
[L]_{B}=P_{B\to S}\times [L]_{S}\times P_{S\to B}
$$
Or simply:
$$
[B]=P^{-1}\times[A]\times P
$$
This means that $[B]$ and $[A]$ represent the same linear mapping, just with different basis (axis).

If two matrices represent the same linear mapping in different basis, they are **similar matrices**.

When two matrices are similar, they have the same:
- [[1_Determinants#The Determinant|determinant]]
- [[1_Eigenvectors#Eigenvalues|eigenvalues]]
- [[2_Row Echelon#Ranks|rank]]
- *trace* - the sum of diagonal entries


---

## Eigenvectors as basis

Recall: For any [[1_Matrix#Triangular matrices|Triangular matrices]], the eigenvalues are the **entires on the main diagonal**. 

For example, finding the eigenvalues of $A$:
$$
A=\begin{bmatrix}
\boxed{ 8 } & 0 \\
0 & \boxed{ 6 }
\end{bmatrix}
$$
It follows that $\lambda=8,6$

This means that each basis vectors of $A$ **are the eigenvectors**.

This makes it **convenient** to compute powers of the transformation without having to multiply matrices multiple times. (Since $A^{n}\vec{v}=\lambda^{n}\vec{v}$)

However, the basis vectors aren't always the eigenvectors. 
- If there are 2 distinct eigenvalues in $\mathbb{R}^{2}$
- We can use the [[2_Coordinates#Change of Basis|Change of Basis]] to **convert them into the basis vectors** in our custom coordinate system
- This is called **Diagonalization**


### Diagonalization
- assuming eigenvectors exist, if
	- matrices $A$ and $B$ are [[#Similar matrices|similar]] by $B=P^{-1}AP$
	- $B$ is a [[1_Matrix#Diagonal matrices|diagonal matrix]]
- then $P$ **diagonalizes** $A$ into $B$

For a matrix $A$ to be **diagonalizable**, it needs to satisfy:
- there exists $n$ distinct eigenvalues for an $n\times n$ matrix
- every eigenvalue has its [[1_Eigenvectors#Geometric multiplicity|geometric multiplicity]] **equal to** its [[1_Eigenvectors#Algebraic multiplicity|algebraic multiplicity]]


### Diagonalization Steps

> Diagonalize $A$ given:
> $A=\begin{bmatrix}3&2\\5&6\end{bmatrix}$

Goal: write $A$ as a diagonal matrix by changing the basis vectors.

1. Find the eigen**values** by steps described [[1_Eigenvectors#Finding eigenvalues and eigenvectors|here]].
	- Finding $\lambda I-A$
		- $=\lambda \begin{bmatrix}1&0\\0&1\end{bmatrix}-\begin{bmatrix}3&2\\5&6\end{bmatrix}$
		- $=\begin{bmatrix}\lambda-3&-2\\-5&\lambda-6\end{bmatrix}$
	- Finding $\det(\lambda I-A)$
		- $=(\lambda-3)(\lambda-6)-(-5)(-2)$
		- $=\lambda^{2}-9\lambda+18-10$
		- $=\lambda^{2}-9\lambda+8$
		- $=(\lambda-8)(\lambda-1)$
	- Setting $\det(\lambda I-A)=0$
		- $\lambda=1,8$

2. Find an eigen**vector** associated with $\lambda=1$
	- Using $\vec{0}=(\lambda I-A)\vec{v}$, substitute $\lambda$ and $A$
		- $\implies 0=\left(\begin{bmatrix}1&0\\0&1\end{bmatrix}-\begin{bmatrix}3&2\\5&6\end{bmatrix}\right)\vec{v}$
		- $\implies 0=\begin{bmatrix}-2&-2\\-5&-5\end{bmatrix}\vec{v}$
	- Solve for $\vec{v}$
		- $\left[ \begin{array}{@{}cc|c@{}}-2&-2&0\\-5&-5&0\end{array} \right]\sim\left[ \begin{array}{@{}cc|c@{}}1&1&0\\0&0&0\end{array} \right]$
		- $\vec{v}=\begin{bmatrix}-1\\1\end{bmatrix}t$
	- Therefore, $\begin{bmatrix}-1\\1\end{bmatrix}$ is an eigenvector associated with $\lambda=1$

3. Find an eigen**vector** associated with $\lambda=8$
	- Using $\vec{0}=(\lambda I-A)\vec{v}$, substitute $\lambda$ and $A$
		- $\implies 0=\left(\begin{bmatrix}8&0\\0&8\end{bmatrix}-\begin{bmatrix}3&2\\5&6\end{bmatrix}\right)\vec{v}$
		- $\implies 0=\begin{bmatrix}5&-2\\-5&2\end{bmatrix}\vec{v}$
	- Solve for $\vec{v}$
		- $\left[ \begin{array}{@{}cc|c@{}}5&-2&0\\-5&2&0\end{array} \right]\sim\left[ \begin{array}{@{}cc|c@{}}1&-\frac{2}{5}&0\\0&0&0\end{array} \right]$
		- $\vec{v}=\begin{bmatrix} \frac{2}{5} \\1\end{bmatrix}t=\begin{bmatrix}2\\5\end{bmatrix}t$
	- Therefore, $\begin{bmatrix}2\\5\end{bmatrix}$ is an eigenvector associated with $\lambda=8$

4. Take each eigenvector and construct a **transition matrix** $P$ ($P_{B \to S}$)
	- Eigenvector of $A$ where $\lambda=1$: $\begin{bmatrix}-1\\1\end{bmatrix}$
	- Eigenvector of $A$ where $\lambda=8$: $\begin{bmatrix}2\\5\end{bmatrix}$
	- Transition matrix $P$: $\begin{bmatrix}-1&2\\1&5\end{bmatrix}$

5. Find the **inverse** of $P$ ($P^{-1}$)
	- Using the formula from [[7_Inverses#General 2x2 Inverse|General 2x2 Inverse]]
	- $P^{-1}=\dfrac{1}{(-1)(5)-(2)(1)}\begin{bmatrix}5&-2\\-1&-1\end{bmatrix}$
	- $P^{-1}=\begin{bmatrix}- \frac{5}{8} & \frac{1}{4} \\  \frac{1}{8} &  \frac{1}{8} \end{bmatrix}$

6. Compute $B=P^{-1}AP$
	- $B=\begin{bmatrix}- \frac{5}{8} & \frac{1}{4} \\  \frac{1}{8} &  \frac{1}{8} \end{bmatrix}\begin{bmatrix}3&2\\5&6\end{bmatrix}\begin{bmatrix}-1&2\\1&5\end{bmatrix}$
	- $B=\begin{bmatrix}-\frac{7}{8}&0\\0&7\end{bmatrix}$

Notice that $B$ must be a diagonal matrix.

$\therefore\begin{bmatrix}-\frac{7}{8}&0\\0&7\end{bmatrix}$ is the **diagonalization** of $\begin{bmatrix}3&2\\5&6\end{bmatrix}$ using $P=\begin{bmatrix}-1&2\\1&5\end{bmatrix}$


---

## Computing power

Diagonalization makes it easy to compute powers of matrices

Using the [[2_Coordinates#Change of Basis|Change of Basis]] formula, we have:
$$
\begin{align}
B=P^{-1}AP &  & A=PBP^{-1} &  & \implies A^{n}=PB^{n}P^{-1}
\end{align}
$$
where $B$ is the diagonalization of $A$ by $P$

Basically, instead of computing $A^{n}$, we can:
- diagonalize $A$ to $B$
- compute $B^{n}$
- convert $B$ back to the basis in $A$

### Computing power example

> Compute $A^{25}$ using the following information (from last example)
> - $A=\begin{bmatrix}3&2\\5&6\end{bmatrix}$
> - $B=\begin{bmatrix}-\frac{7}{8}&0\\0&7\end{bmatrix}$
> - $P=\begin{bmatrix}-1&2\\1&5\end{bmatrix}$
> - $P^{-1}=\begin{bmatrix}- \frac{5}{8} & \frac{1}{4} \\  \frac{1}{8} &  \frac{1}{8} \end{bmatrix}$

Since $A$ is already diagonalized, we can compute $B^{25}$.

$B^{25}=\begin{bmatrix}\left( -\frac{7}{8} \right)^{25}&0\\0&7^{25}\end{bmatrix}$

We can do this directly since $B$ is a [[1_Matrix#Diagonal matrices|diagonal matrix]].
Note: $7^{25}$ and $8^{25}$ are large numbers that we don't need to calculate. This is already in calculator ready form.

Now we can take $B^{25}$ and convert it back into the standard basis.

$$A^{25}=PB^{25}P^{-1}$$
$$
A^{25}=\begin{bmatrix}-1&2\\1&5\end{bmatrix}\begin{bmatrix}\left( -\frac{7}{8} \right)^{25}&0\\0&7^{25}\end{bmatrix}\begin{bmatrix}- \frac{5}{8} & \frac{1}{4} \\  \frac{1}{8} &  \frac{1}{8} \end{bmatrix}
$$

While this is still tedious, it is a lot better than performing matrix multiplication on $A$ 25 times.


---

## Probability

A **probability** is the ratio of **event** and **sample space**. 
$$
\text{Probability}=\dfrac{\text{Event}}{\text{Sample Space}}
$$
For example
- if 25 out of 100 viewers watch channel A
- there is a 25% chance that a random viewer is watching channel A
- the probability is 0.25


### Probability vector
Listing all probabilities vertically will create a **probability [[1_Vectors#Vectors|vector]]** if all of them add up to 1 (the entire sample space).

For example, out of 100 viewers
- 25 people watch channel A
- 40 people watch channel B
- 35 people watch channel C

Then, the probability vector of viewers is:
$$
\vec{v}=\begin{bmatrix}
0.25\\0.40\\0.35
\end{bmatrix}
$$
Notice that all of them **add up to 1**.


### Markov chain
If there is a **movement** or **dynamic** among the state of vectors with respect to time, we can draw a **Markov chain** describing the changes.

Using our last example, if every day, people switch channels as follows:

- For every 100 people watching channel A:
	- 60 people **keep watching** channel A
	- 30 people **switch** to channel B
	- 10 people **switch** to channel C
- For every 100 people watching channel B:
	- 10 people **switch** to channel A
	- 80 people **keep watching** channel B
	- 10 people **switch** to channel C
- For every 100 people watching channel C:
	- 20 people **switch** to channel A
	- 40 people **switch** to channel B
	- 40 people **keep watching** channel C

We can use this information to draw a **Markov chain**:
![[Note Apr 1, 2025 (2).jpeg|500]]


### Stochastic matrix
- [[1_Matrix#Matrices|matrix]] with columns being the **probability vectors**
- is used to describe a **Markov chain**

Using the information from the example above, we can create a **Stochastic matrix** as follows:
$$
P=\begin{bmatrix}
0.6&0.1&0.2 \\
0.3&0.8&0.4 \\
0.1&0.1&0.4
\end{bmatrix}
$$
where **each column** represents the movement of viewers for **each channel**.

In Markov chain terms, this Stochastic matrix is called a **transition matrix**.
$$
\vec{x}(k+1)=P\vec{x}(k)
$$
where $\vec{x}$ is a probability matrix, and $\vec{x}(k)$ describes the probability at time $k$.

This recursive algorithm multiplies $\vec{x}$ by the transition matrix to find the **next iteration**.

For example, finding the viewer probability vector after 1 day, we multiply $P$ into $\vec{v}$:
$$
P\vec{v}=\begin{bmatrix}
0.6&0.1&0.2 \\
0.3&0.8&0.4 \\
0.1&0.1&0.4
\end{bmatrix}\begin{bmatrix}
0.25\\0.40\\0.35
\end{bmatrix}=\begin{bmatrix}
0.260\\0.535\\0.205
\end{bmatrix}
$$
Therefore, after 1 day:
- ~26% of viewers watch channel A
- ~54% of viewers watch channel B
- ~21% of viewers watch channel C

To find this probability in $n$ number of days, apply the transition matrix $n$ times, and $P^{n}\vec{v}$.

To reduce the amount of calculation, **apply diagonalization** to compute the power.


### Regular Markov chain

If there exists at least one
- Markov **transition matrix** or **any power** of the transition matrix
- there is no 0 entries
Then the Markov chain is **regular**.

In long term, the chain looks like:
$$
x_{0},Px_{1},P^{2}x_{2},P^{3}x_{3},\dots,P^{n}x_{n}
$$
as $n\to \infty$, all regular Markov chains **converges** to a specific probability vector.

That probability vector is called $\vec{q}$, the **steady-state vector**. This is when a transition matrix doesn't do any more effects on the probability vector, and:
$$
P\vec{q}=\vec{q}
$$

Notice that $\vec{q}$ is an [[1_Eigenvectors#Eigenvectors|Eigenvector]] with $\lambda=1$.

We can solve for $q$ by using the formula from [[1_Eigenvectors#Eigenvalues|Eigenvalues]]:
$$
(\lambda I-A)\vec{v}=\vec{0}
$$
Substituting $\lambda=1$, $A=P$, and $\vec{v}=\vec{q}$:
$$
(I-P)\vec{q}=\vec{0}
$$
$$
\left(\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}-\begin{bmatrix}
0.6&0.1&0.2 \\
0.3&0.8&0.4 \\
0.1&0.1&0.4
\end{bmatrix}\right)\vec{q}=\vec{0}
$$
$$
\begin{bmatrix}
0.4 & -0.1 & -0.2 \\
-0.3 & 0.2 & -0.4 \\
-0.1 & -0.1 & 0.6
\end{bmatrix}\vec{q}=\vec{0}
$$
Solve for $\vec{q}$:
$$\left[  
\begin{array}{@{}ccc|c@{}}
0.4 & -0.1 & -0.2 & 0 \\
-0.3 & 0.2 & -0.4 & 0 \\
-0.1 & -0.1 & 0.6 & 0
\end{array} \right]\sim \left[   \begin{array}{@{}ccc|c@{}}
1 & 0 & -1.6 & 0 \\
0 & 1 & -4.4 & 0 \\
0 & 0 & 0 & 0
\end{array} \right]
$$
We get the solution space for $\vec{q}$:
$$
\vec{q}=\begin{bmatrix}
1.6\\4.4\\1
\end{bmatrix}t\implies   \vec{q}=\begin{bmatrix}
0.229\\0.629\\0.143
\end{bmatrix}
$$
Therefore, in the long term:
- ~23% of viewers watch channel A
- ~63% of viewers watch channel B
- ~14% of viewers watch channel C

