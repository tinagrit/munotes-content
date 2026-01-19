Lecture 4

## Split of a set

A split of a [[1_Sets#Sets|set]] is a [[3_Sequences#Sequences|sequence]] of [[1_Sets#Set operations|disjoint]] [[1_Sets#Subsets|subsets]] as parts of the original set.

For example, a $(2,1,3)-\text{split of }A$ where $A=\left\{ 1,2,3,4,5,6 \right\}$ is:
$$
(\left\{ 1,2 \right\} ,\left\{ 3 \right\} ,\left\{ 4,5,6 \right\} )
$$
Notice that the first subset has 2 elements, the second has 1, and the third has 3. Since sets do not define orders, the subsets in the split can be in **a different order**. (this is only one example)

Formal definition:
A $(k_{1},k_{2},\dots,k_{m})-\text{split of }A$ is:
- a sequence of sets $(A_{1},A_{2},\dots,A_{m})$ such that $A_{1}\cup A_{2}\cup\dots\cup A_{m}=A$
- For all $i \in \left\{ 1,2,\dots,m \right\}$, $|A_{i}|=|k_{i}|$
- For all $i,j \in \left\{ 1,2,\dots,m \right\}$ and $i \neq j$, $A_{i} \cap A_{j} = \varnothing$

### Counting results of a split
The number of ways to obtain a $(k_{1},k_{2},\dots,k_{m})-\text{split of }A$ with $|A|=n$ is:
$$
\dbinom{n}{k_{1},k_{2},\dots,k_{m}} = \dfrac{n!}{k_{1}!\cdot k_{2}! \cdot \ldots \cdot k_{m}!}
$$
where all $k$s add up to $n$


> Consider the letters in the work $\text{BOOKKEEPER}$
> Count the number of arrangements of the letters, where the same letters are indistinguishable from one another

From the 10 letters, there are 1 $\text{B}$, 2 $\text{O}$s, 2 $\text{K}$s, 3 $\text{E}$s, 1 $P$, and 1 $R$.
We can represent the letters as $(1,2,2,3,1,1)-\text{split of }A$ where $A=\left\{ 1,2,3,4,5,6,7,8,9,10 \right\}$, each split being positions of the letter

Assuming index 1 starting,
$$
\begin{align}
\text{B} && \text{O} && \text{O} && \text{K} && \text{K} && \text{E} && \text{E} && \text{P} && \text{E} && \text{R} \\
\text{1} && \text{2} && \text{3} && \text{4} && \text{5} && \text{6} && \text{7} && \text{8} && \text{9} && \text{10}
\end{align}
$$

The $(1,2,2,3,1,1)-\text{split of }A$ for the original arrangement (BOOKKEEPER) is:
$$
\left( \underbrace{ \left\{ 1 \right\} }_{ \text{B} } ,\underbrace{ \left\{ 2,3 \right\} }_{ \text{O} } ,\underbrace{ \left\{ 4,5 \right\} }_{ \text{K} } ,\underbrace{ \left\{ 6,7,9 \right\} }_{ \text{E} } ,\underbrace{ \left\{ 8 \right\} }_{ \text{P} } ,\underbrace{ \left\{ 10 \right\} }_{ \text{R} }  \right) 
$$

Notice that for each subset of the split, it does not matter where each individual letter of the same letter is. For example, in the $\text{E}$ subset, $\left\{ 6,7,9 \right\}$ and $\left\{ 7,9,6 \right\}$ would be identical, as they are all $\text{E}$s.

The total number of strings that we can form with those letters is the number of ways we can obtain $(1,2,2,3,1,1)-\text{splits of }A$, which is:
$$
\dbinom{10}{1,2,2,3,1,1}=\dfrac{10!}{1!\cdot 2! \cdot 2!\cdot 3! \cdot 1! \cdot 1!}
$$


## Multinomial Theorem
*Extension of the* [[5_Binomial Theorem#Binomial Theorem|Binomial Theorem]]

The Multinomial Theorem **expands powers** of a polynomial in the form of:
$$
(x_{1}+x_{2}+\dots+x_{m})^{n}
$$
where $m,n \in \mathbb{N}$ and $x_{1},x_{2},\dots,x_{m} \in \mathbb{R}$.

$$
=\sum_{\begin{align}
k_{1},k_{2},\dots,k_{m} \text{ where}  \\
\text{}k_{1}+k_{2}+\dots+k_{m}=n
\end{align}} \dbinom{n}{k_{1},k_{2},\dots,k_{m}}x_{1}^{k_{1}}x_{2}^{k_{2}}\dots x_{m}^{k_{m}}
$$

For example,
> Find the coefficient of the term $xyz^{2}$ in the expansion of $(x+y+z)^{4}$

Here, we have $m=3$ (number of terms), and $n=4$ (power).

Since we are looking for the term $xyz^{2}$, we can take the power of each variable as $k$. 
Therefore, $k_{1}=1$ (power of $x$), $k_{2}=1$ (power of $y$), and $k_{3}=2$ (power of $z$)

The coefficient of the term is:
$$
\dbinom{4}{1,1,2}=\dfrac{4!}{1! \cdot 1! \cdot 2!}
$$

