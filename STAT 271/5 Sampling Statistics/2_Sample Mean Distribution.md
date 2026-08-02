Lectures 14-16

## Sample Mean Distribution
Consider a random *iid* **sample** $X_{1},X_{2},\dots,X_{n}$, taken from population where the **population mean** is $\mu$, and **population variance** is $\sigma^{2}$.

The [[2_Common Statistics#Sample mean|sample mean]], defined by:
$$
\overline{X}=\dfrac{1}{n}\sum_{i=1}^{n}X_{i} 
$$
is a [[2_Random Variables#Random Variables|random variable]], since it is determined by $n$ random variables.

### Expected value
The sample mean's [[1_Expectation#Expected value|expected value]] is:
$$
E[\overline{X}]=\dfrac{1}{n}E[X_{1}+X_{2}+\dots+X_{n}]=\dfrac{1}{n}n\mu \implies \boxed{ E[\overline{X}]=\mu }
$$
Over many samples, the values of $\overline{X}$ are **centred around** $\mu$.

### Variance
The sample mean's [[2_Variance#Variance|variance]] is:
$$
\text{Var}[\overline{X}]=\dfrac{1}{n^{2}}\text{Var}[X_{1}+X_{2}+\dots+X_{n}]=\dfrac{1}{n^{2}}n\sigma^{2}
$$
$$
\implies \boxed{ \text{Var}[\overline{X}]=\dfrac{\sigma^{2}}{n} }
$$
The variance is small when $\sigma^{2}$ is small, or $n$ is large.


---
## Central Limit Theorem
Over many samples from the population, the **sampling distribution** of $\overline{X}$ is:
- **normal** if the population distribution is [[4_Normal Distribution#Normal Random Variable|normal]] 
- **approximately normal** if the population distribution is non-normal but $n$ is large
$$
\overline{X} \overset A\sim N\left(\mu,\frac{\sigma^{2}}{n}\right)
$$

Similar, the **sum of many** independent random variables is **approximately normal**. This explains why many natural populations have **bell-shaped** empirical frequencies.

Let $X_{1},X_{2},\dots,X_n$ be *iid* random variables with common mean $\mu$ and variance $\sigma^{2}$. For $n$ large, the sum of the random variables is **approximately normal** with mean $n\mu$ and variance $n\sigma^{2}$.
$$
\sum_{i=1}^{n} X_{i}\overset A\sim N(n\mu,n\sigma^{2})
$$

It follows that:
$$
\dfrac{X_{1}+X_{2}+\dots+X_{n}-n\mu}{\sigma \sqrt{ n }} \overset A\sim N(0,1)
$$
by the linear transformation property of [[4_Normal Distribution#Normal Random Variable|normal variables]].

Therefore,
$$
\boxed{ \dfrac{\overline{X}-\mu}{\sigma/\sqrt{ n }}\overset A\sim N(0,1) }
$$

### Sample Size
If the population is not normally distributed, a sample size of **at least 30** is generally enough to approximate the sample mean to be normal.

In practice, a sample size of 5 or 10 may be good enough to get a good approximation.

### Sampling from Finite Population
Consider a sample of size $n$ chosen from a finite population of $N$ individuals. The trials are **not independent**. However, if $N$ is large relative to $n$, the samples are almost independent.

