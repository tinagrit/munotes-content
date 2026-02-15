Lecture 12

## Distribution Functions

### Probability Mass Function (PMF)
Let $R$ be a discrete [[2_Random Variables#Random Variable|random variable]] with codomain $V$. 

The **PMF** of $R$ is the function $f_{R}:V \to [0,1]$ such that:
$$
f_{R}(x)=\begin{cases}
\text{Pr}[R=x] & \text{if }x \in \text{range of }R \\
0 & \text{if }x \not\in \text{range of }R
\end{cases}
$$

In general,
$$
\sum_{x \in V}f_{R}(x)=1 
$$

Basically, PMF is the probability that $R=x$.


### Cumulative Distribution Function (CDF)
Let $R$ be a discrete random variable with codomain $V \in \mathbb{R}$.

The **CDF** of $R$ is the function $F_{R}:\mathbb{R} \to [0,1]$ such that:
$$
F_{R}(x)=\text{Pr}[x \geq R]
$$

In general,
$$
\begin{cases}
F_{R}(x)\to 1 &  \text{as} & x\to \infty \\
F_{R}(x)\to 0 & \text{as} & x\to - \infty
\end{cases}
$$

Basically, CDF is the probability that the input value $x$ is greater than or equal to $R$.


---
## Common Distributions

While the [[#Probability Mass Function (PMF)|PMF]] provides the specific point probability, the [[#Cumulative Distribution Function (CDF)|CDF]] **specifies the distribution** of random variable.


### Bernoulli distribution
Mathematical model for **single experiment** with only **two possible outcomes**. $1$ for success and $0$ for failure.

The PMF of Bernoulli distribution $f_{R}(x):\left\{ 0,1 \right\}\to [0,1]$:
$$
f_{R}(1)=p
$$
where $p$ is the likelihood of succeeding.

The CDF of Bernoulli distribution $F_{R}(x):\mathbb{R} \to [0,1]$:
$$
F_{R}(x)= \begin{cases}
0 & \text{for }x<0 \\
1-p & \text{for }0\leq x<1 \\
1 & \text{for } x\geq 1
\end{cases} 
$$


### Uniform distribution
*Also see* [[4_Uniform Probability#Uniform Probability Space|Uniform Probability]]

A random variable $R$ that takes on each value in $V$ with the **same probability**.

The PMF of Uniform distribution is the same for all outcomes $f_{R}(x)=V\to [0,1]$:
$$
f_{R}(x)=\dfrac{1}{|V|}
$$

The CDF of Uniform distribution $F_{R}:\mathbb{R} \to [0,1]$:
$$
F_{R}(x)=\begin{cases}
0 & \text{for }x < v_{1} \\
\dfrac{k}{|V|} & \text{for }v_{k} \leq
 x \lt v_{k+1}  \\
1 & \text{for }x\geq v_{|V|}
\end{cases}
$$


### Binomial distribution
Models the **number of successes** in a running $n$ independent [[#Bernoulli distribution|Bernoulli trials]], each with the same probability of success $p$.

The PMF of Binomial distribution $f_{R}:\left\{ 0,1,2,\dots,n \right\}\to [0,1]$:
$$
f_{R}(x)=\dbinom{n}{x}p^{x}(1-p)^{n-x}
$$
where $x \in \left\{ 0,1,2,\dots,n \right\}$

This calculates the number of getting $x$ successes in $n$ runs.

The CDF of Binomial distribution $F_{R}:\mathbb{R}\to [0,1]$:
$$
F_{R}(x)=\begin{cases}
0 & \text{for }x<0 \\
\sum_{i=0}^{k} \binom{n}{i}p^{i}(1-p)^{n-i} & \text{for }k\leq x < k+1 \\
1 & \text{for }x \geq n
\end{cases}
$$


### Geometric distribution
Similar to [[#Binomial distribution|Binomial distribution]], running $n$ independent [[#Bernoulli distribution|Bernoulli trials]] each with the same probability of success $p$, but models the **number of trials to get first success**.

The PMF of Geometric distribution $f_{R}:\left\{ 1,2,3,\dots \right\} \to [0,1]$:
$$
f_{R}(x)=(1-p)^{x-1}p
$$
where $x \in \left\{ 1,2,3,\dots \right\}$

This calculates the probability that the first success is on the $x$-th trial.

The CDF of Geometric distribution $F_{R}:\mathbb{R} \to [0,1]$:
$$
F_{R}(x)=\begin{cases}
0 & \text{for }x>1 \\
1-(1-p)^{\lfloor x \rfloor } & \text{for }k\leq x <k+1
\end{cases}
$$
