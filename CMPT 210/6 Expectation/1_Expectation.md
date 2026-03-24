Lectures 15 & 18

## Expectation

Consider a [[2_Random Variables#Random Variable|Random Variable]] $R:S\to V$. The **expectation** or **mean** of $R$ is the weighted average of the values in the range:
$$
\mathbb{E}[R]=\sum_{w \in S} \text{Pr}[\{w\}]R[w] 
$$
where $\mathbb{E}[\cdot]$ is the **expectation operator** and $w$ is a sample in $S$.

The expectation is the **average value** of $R$ in the long run. It doesn't have to be a possible value.

For example, rolling a 6-sided die, and $R$ be the number that is rolled.
- We have $S=\left\{ 1,2,3,4,5,6 \right\}$
- Since this is a [[4_Uniform Probability#Uniform Probability Space|uniform space]], we have: $\text{Pr}[\{w\}]=\dfrac{1}{6}$
- The expectation is then: $\mathbb{E}[R]=\dfrac{1}{6}(1+2+3+4+5+6)=3.5$

If $R_{1}$ and $R_{2}$ are random variables on the same probability space, the **linearity of expectation** applies:
$$
\mathbb{E}[R_{1}+R_{2}]=\mathbb{E}[R_{1}]+\mathbb{E}[R_{2}]
$$
The linearity of expectation is **regardless of independence**. Values can always be added even if one influences the other.


### Using Distribution
Different from the above definition, the expected value can be found using the [[3_Distribution Functions#Distribution Functions|probability distribution]] as well.
$$
\boxed{ \mathbb{E}[R]=\sum_{x \in \text{Range}(R)}\text{Pr}[R=x]\cdot x  }
$$
This only iterates through the distinct values in the range of $R$.

Proof that the two expressions are equivalent:
$$
\begin{align}
\mathbb{E}[R]=\sum_{w\in S}\text{Pr}[\left\{ w \right\} ]R[w] & =\sum_{x \in \text{Range}(R)}\left( \sum_{w \in S \mid R[w]=x} \text{Pr}[\left\{ w \right\} ]R[w]  \right)  \\
 & =\sum_{x\in \text{Range}(R)}\sum_{w \in S \mid R[w]=x} \text{Pr}[\left\{ w \right\} ]\cdot x  \\
 & =\sum_{x \in \text{Range}(R)}\text{Pr}[\left\{ w \in S\mid R(w)=x \right\} ]\cdot x \\
 & = \sum_{x\in \text{Range}(R)}\text{Pr}[R=x]\cdot x     
\end{align}
$$

If $R$ is inside of a function, the expectation is:
$$
\mathbb{E}[g(R)]=\sum_{x \in \text{Range}(R)}\text{Pr}[R=x]\cdot g(x) 
$$


| Random Variable | Condition                           | Expectation $\mathbb{E}$             |
| --------------- | ----------------------------------- | ------------------------------------ |
| Indicator       | Event $E$                           | $\text{Pr}[E]$                       |
| Bernoulli       | Success probability $p$             | $p$                                  |
| Uniform         | Size of range $n$                   | $\dfrac{v_{1}+v_{2}+\dots+v_{n}}{n}$ |
| Binomial        | $n$ trials, success probability $p$ | $np$                                 |
| Geometric       | Success probability $p$             | $\dfrac{1}{p}$                       |


### Indicator random variable
See [[2_Random Variables#Indicator Random Variable|Indicator random variable]]

If $I_{E}$ is an indicator variable for event $E$, the expected value is:
$$
\begin{align}
\mathbb{E}[I_{E}] & =\sum_{x \in \left\{ 1,0 \right\} } \text{Pr}[I_{E}=x] \cdot x  \\
 & =\text{Pr}[I_{E}=1]\cdot 1 + \text{Pr}[I_{E}=0]\cdot 0 \\
 & =\text{Pr}[I_{E}=1] \\
 & =\text{Pr}[E]
\end{align}
$$

Therefore, its expected value is given by:
$$
\boxed{ \mathbb{E}[I_{E}]=\text{Pr}[E] }
$$


### Bernoulli random variable
See [[3_Distribution Functions#Bernoulli distribution|Bernoulli distribution]]

If $R$ is a Bernoulli random variable with success probability $p$, the expected value is:
$$
\mathbb{E}[R]=\sum_{x \in \left\{ 0,1 \right\} }\text{Pr}[R=x]\cdot x =(1-p)(0)+(p)(1)=p 
$$

Therefore, its expected value is given by:
$$
\boxed{ \mathbb{E}[R]=p }
$$


### Uniform random variable
See [[3_Distribution Functions#Uniform distribution|Uniform distribution]]

If $R$ is a uniform random variable with $\text{Range}(R)=\left\{ v_{1},v_{2},\dots,v_{n} \right\}$, then $\text{Pr}[R=v_{1}]=\text{Pr}[R=v_{2}]=\dots=\text{Pr}[R=v_{n}]=\dfrac{1}{n}$.

The expected value is given by:
$$
\boxed{ \mathbb{E}[R]=\dfrac{v_{1}+v_{2}+\dots+v_{n}}{n} }
$$


### Binomial random variable
See [[3_Distribution Functions#Binomial distribution|Binomial distribution]]

If $R$ is a binomial random variable on $n$ independent trials, and a success probability of $p$ for each trial, the expected value is:
$$
\begin{align}
\mathbb{E}[R] & = \mathbb{E}\left[ \sum_{i=1}^{n} R_{i}  \right] \\
 & =\mathbb{E}[R_{1}]+\mathbb{E}[R_{2}]+\dots+\mathbb{E}[R_{n}] \\
 & =p+p+\dots+p \\
 & =np 
\end{align}
$$

Therefore, the expected value is given by:
$$
\boxed{ \mathbb{E}[R]=np }
$$


### Geometric random variable
See [[3_Distribution Functions#Geometric distribution|Geometric distribution]]

Recall that the **PMF** of geometric distribution is:
$$
\text{Pr}[R=x]=(1-p)^{x-1}\cdot p
$$
If $R$ is a geometric random variable, the expected value is:
$$
\begin{align}
\mathbb{E}[R] & =\sum_{x \in \left\{ 1,2,\dots \right\} } \text{Pr}[R=x]\cdot x \\
 & = \sum_{x \in \left\{ 1,2,\dots \right\} }(1-p)^{x-1}p\cdot x \\
 & = \sum_{x=1}^{\infty}(1-p)^{x-1}\cdot x  \\
 & = \dfrac{1}{p}
\end{align}
$$

Therefore, its expected value is given by:
$$
\boxed{ \mathbb{E}[R]=\dfrac{1}{p} }
$$
