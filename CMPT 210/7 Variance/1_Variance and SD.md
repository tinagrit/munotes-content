Lectures 18 & 19

## Variance
While the [[1_Expectation#Expectation|expected value]] of $\mathbb{E}[R]$ describes the **mean** of the distribution, it does not describe **how dispersed** the distribution is.

**Variance** measures the expected squared deviation from its mean, which is defined as:
$$
\text{Var}[R]=\mathbb{E}\left[ (R-\mu)^{2} \right] =\sum_{x \in \text{Range}(R)} \text{Pr}[R=x] \cdot (x-\mu)^{2} 
$$
where $\mu = \mathbb{E}[R]$ is the mean.

Alternatively, variance can be calculated with:
$$
\text{Var}[R]=\mathbb{E}[R^{2}]-\mu^{2}=\mathbb{E}[R^{2}]-(\mathbb{E}[R])^{2}
$$

Proof for this alternative calculation:
$$
\begin{align}
\text{Var}[R] & =\sum_{x \in \text{Range}(R)} \text{Pr}[R=x] \cdot (x-\mu)^{2}  \\\\
 & =\sum_{x \in \text{Range}(R)} \text{Pr}[R=x] \cdot (x^{2}-2x\mu+\mu^{2}) \\\\
 & = \left( \sum_{x \in \text{Range}(R)} \text{Pr}[R=x]\cdot x^{2} \right)-2\mu \left( \sum_{x \in \text{Range}(R)} \text{Pr}[R=x]\cdot x \right)+\mu^{2} \left( \sum_{x \in \text{Range}(R)} \text{Pr}[R=x] \right)  \\\\
 & =   \mathbb{E}[R^{2}]-2\mu \mathbb{E}[R]+\mu^{2} \\
 & = \mathbb{E}[R^{2}]- 2\mu \mu + \mu^{2} \\
 & =\mathbb{E}[R^{2}]-\mu^{2} \\
 & =\mathbb{E}[R^{2}]-(\mathbb{E}[R])^{2}
\end{align}
$$


### Linear Transformations
For constants $a$, $b$, and a random variable $R$, the following is true:
$$
\text{Var}[aR+b]=a^{2}\text{Var}[R]
$$

### Independence
If two random variables $R_{1}$ and $R_{2}$ are [[4_Independent Random Variables#Independence|independent]], then:
$$
\text{Var}[R_{1}+R_{2}]=\text{Var}[R_{1}]+\text{Var}[R_{2}]
$$

### Pairwise Independence
If for a set of random variables $R_{1},R_{2},\dots,R_{n}$, every possible possible pair is independent, then:
$$
\text{Pr}[R_{i}=x\cap R_{j}=y]=\text{Pr}[R_{i}=x]\cdot \text{Pr}[R_{j}=y]
$$


---
## Distribution variance

### Bernoulli variance
See [[3_Distribution Functions#Bernoulli distribution|distribution]] and [[1_Expectation#Bernoulli random variable|expectation]]

If $R$ is a Bernoulli random variable and $p$ is the probability of success, then:
$$
\boxed{ \text{Var}[R]=p(1-p) }
$$
Since $\mathbb{E}[R]=p$, we have:
$$
\begin{align}
\text{Var}[R] & =\sum_{x \in \left\{ 0,1 \right\} } \text{Pr}[R=x]\cdot (x-p)^{2} \\
 & =\text{Pr}[R=0](0-p)^{2}+\text{Pr}[R=1](1-p)^{2} \\
 & =(1-p)p^{2}+p(1-p)^{2} \\
 & =p(1-p) 
\end{align}
$$

The function $f(p)=p(1-p)$ has a maximum at $p=0.5$ and $f=0.25$

![[Screenshot 2026-03-23 at 4.44.37 PM.png|400]]

Therefore, in a Bernoulli random variable, the maximum value of $\text{Var}[R]$ is $0.25$.


### Uniform variance
See [[3_Distribution Functions#Uniform distribution|distribution]] and [[1_Expectation#Uniform random variable|expectation]]

If $R$ is a uniform random variable with $\text{Range}(R)=\left\{ v_{1},v_{2},\dots,v_{n} \right\}$, then
$$
\boxed{ \text{Var}[R]=\dfrac{1}{n}\sum_{i=1}^{n} v_{i}^{2}-\left( \dfrac{1}{n} \sum_{i=1}^{n}v_{i}  \right)^{2} } 
$$
Using the alternate calculation of variance, with $\mathbb{E}[R]=\dfrac{v_{1}+v_{2}+\dots+v_{n}}{n}$

### Binomial variance
See [[3_Distribution Functions#Binomial distribution|distribution]] and [[1_Expectation#Binomial random variable|expectation]]

If $R$ is a binomial random variable on $n$ independent trials, and a success probability of $p$ for each trial, then
$$
\boxed{ \text{Var}[R]=np(1-p) }
$$

### Geometric variance
See [[3_Distribution Functions#Geometric distribution|distribution]] and [[1_Expectation#Geometric random variable|expectation]]

If $R$ is a geometric random variable with a success probability of $p$, then
$$
\boxed{ \text{Var}[R]=\dfrac{1-p}{p^{2}} }
$$


---
## Standard deviation

The standard deviation (SD, $\sigma$) for a random variable $R$, denoted $\sigma_{R}$ is the **square root** of variance:
$$
\sigma_{R}=\sqrt{ \text{Var}[R] }
$$

Unlike variance, the standard deviation has the same units as the expectation and the random variable itself.

### Linear Transformation of SD
For constants $a$, $b$, and a random variable $R$, the following is true:
$$
\sigma_{aR+b}=\sqrt{ \text{Var}[aR+b] }=\sqrt{ a^{2}\text{Var}[R] }=|a|\sigma_{R}
$$
