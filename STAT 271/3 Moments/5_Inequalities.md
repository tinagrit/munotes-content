Lecture 10

## Markov's Inequality
For a non-negative [[2_Random Variables#Random Variables|random variable]] $X$, then for any $a>0$, the upper bound for $P\left\{ X\geq a \right\}$ is given in terms of the [[1_Expectation#Expected value|expected value]] of $X$.
$$
P\left\{ X\geq a \right\}\leq \dfrac{E[X]}{a} 
$$

---
## Chebyshev's Inequality
For any random variable $X$ with [[1_Expectation#Expected value|mean]] $\mu$ and [[2_Variance#Variance|variance]] $\sigma^{2}$, then for any $k>0$:

The probability that the value is **off the mean** by more than $k$ is upper bounded:
$$
P\left\{ |X-\mu |\geq k \right\} \leq \dfrac{\sigma^{2}}{k^{2}} 
$$

The probability that the value of **off the mean** by more than $k$ [[2_Variance#Standard deviation|standard deviations]] is upper bounded:
$$
P\left\{ |X-\mu|\geq k\sigma \right\}\leq \dfrac{1}{k^{2}} 
$$
