Lectures 3 & 4

## Distribution Functions
See more: [CMPT 210 > Distribution Functions](https://munotes.tinagrit.com/CMPT210/5-random-variables/3_distribution-functions.html)

### Probability Mass Function (PMF)
Let $R$ be a [[2_Random Variables#Types of Random Variables|discrete random variable]], the PMF, denoted $p(x)$, is the probability that the input value $x$ **is equal to** $R$.
$$
p(x)=\begin{cases}
P(R=x) & \text{if }x \in \text{range of }R \\
0 & \text{if }x \not\in \text{range of }R
\end{cases}
$$

In general,
$$
\sum_{x \in V}p(x)=1 
$$
for the random variable codomain $V$.


### Cumulative Distribution Function (CDF)
Let $R$ be a [[2_Random Variables#Types of Random Variables|discrete random variable]], the CDF, denoted $F(x)$, is the probability that the input value $x$ is **greater than or equal to** $R$.
$$
F(x)=P(R\leq x)
$$

The CDF is a **right continuous step function**.

$X\sim F$ denotes that $F$ is the distribution function of $X$.

Property derived using [[1_Probability#Axioms and Propositions|Axiom 3]]:
> Find $P(a<X\leq b)$:
> Since $P(X\leq a)$ and $P(a<X\leq b)$ are mutually exclusive, then:
> $P(X\leq b)=P(X \leq a)+P(a<X\leq b)$
> Rearranging, we get:
> $P(a<X\leq b)=P(X\leq b)-P(X\leq a)$
> which is the same as:
> $F(b)-F(a)$

The CDF can be written in terms of the PMF with:
$$
F(a)=\sum_{x\leq a}p(x) 
$$
since:
$$
P(R\leq x)=P(R=0)+P(R=1)+\dots+P(R=x)
$$
if $x \in \mathbb{Z}^{+}$, for example.


### Probability Density Function (PDF)
Let $R$ be a [[2_Random Variables#Types of Random Variables|continuous random variable]], the PDF, denoted $f(x)$, is the probability that $R$ is **within the range** of $[a,b]$.
$$
P\left\{ R \in A \right\}=P(a\leq R \leq b) =\int_{a}^{b}f(x)\,dx
$$

While the CDF works for discrete random variables, we need to use the PDF for continuous variables. Instead of adding each PMF value, we can take **the area under the curve** for infinite sum, hence the integral.

Based on [[1_Probability#Axioms and Propositions|Axiom 2]], the sum of all probability still has to equal to $1$. This is the same meaning as adding up all $p(x)$ PMF:
$$
\sum_{x \in V}p(x)=1  \iff  \int_{-\infty}^{\infty}f(x)\,dx=1
$$

If we let $A=\left\{ a \right\}$, then $P(R=a)=\int_{a}^{a}f(x)\, dx=0$.
Therefore, the probability that a continuous random variable takes any **particular value** is $0$.

> [!tip] Note
> The PDF is **the derivative** of CDF, expressed as:$$\dfrac{d}{dx}F(x)=f(x)$$

