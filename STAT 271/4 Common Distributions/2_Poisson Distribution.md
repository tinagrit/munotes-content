Lecture 11

## Poisson Random Variable
A Poisson random variable takes a parameter $\lambda$. If $X$ is a Poisson random variable, it is written as:
$$
X\sim \text{Po}(\lambda)
$$

This distribution approximates the **number of events** occurring in a **fixed interval** of time, space, area, etc.

| Property                                                                  | Formula                                    |
| ------------------------------------------------------------------------- | ------------------------------------------ |
| PMF [[3_Distribution Functions#Probability Mass Function (PMF)\|→]]       | $p(x)=e^{-\lambda}\dfrac{\lambda^{x}}{x!}$ |
| Mean [[1_Expectation#Expected value\|→]]                                  | $E[X]=\lambda$                             |
| Variance [[2_Variance#Variance\|→]]                                       | $\text{Var}[X]=\lambda$                    |
| MGF [[3_Moment Generating Functions#Moment Generating Function (MGF)\|→]] | $\phi(t)=\exp(\lambda(e^{t}-1))$           |

The Poisson distribution is also a good approximation for [[1_Binomial Distribution#Binomial Random Variable|binomial distribution]] with $n$ large and $p$ small:
$$
X\sim \text{Bin}(n,p) \approx \text{Po}(np)
$$

### Reproductive Property
If we have two [[2_Random Variables#Independence|independent]] Poisson random variables, $X_{1}$ and $X_{2}$, where $X_{1}\sim \text{Po}(\lambda_{1})$ and $X_{2}\sim \text{Po}(\lambda_{2})$,

The sum of $X_{1}$ and $X_{2}$ is **also Poisson** with:
$$
\lambda=\lambda_{1}+\lambda_{2}
$$

### Classification Property
If we have a Poisson random variable $X\sim \text{Po}(\lambda)$, suppose that each event is **independently classified** as type $i$, where $i=1,2,\dots,n$, with probability $p_{i}$.

The number of events of type $i$ have **independent Poisson distributions** with respective parameters $\lambda p_{i}$:
$$
X_{i}\sim \text{Po}(\lambda p_{i})
$$
