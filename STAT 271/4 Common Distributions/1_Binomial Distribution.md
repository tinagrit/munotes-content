Lecture 11

## Binomial Random Variable
A binomial random variable takes parameters $n$ and $p$. If $X$ is a binomial random variable, it is written as:
$$
X\sim \text{Bin}(n,p)
$$

This distribution measures the **number of successes** in $n$ independent trials, each trial with a success probability of $p$.

| Property                                                                  | Formula                              |
| ------------------------------------------------------------------------- | ------------------------------------ |
| PMF [[3_Distribution Functions#Probability Mass Function (PMF)\|→]]       | $p(x)=\dbinom{n}{x}p^{x}(1-p)^{n-x}$ |
| Mean [[1_Expectation#Expected value\|→]]                                  | $E[X]=np$                            |
| Variance [[2_Variance#Variance\|→]]                                       | $\text{Var}[X]=np(1-p)$              |
| MGF [[3_Moment Generating Functions#Moment Generating Function (MGF)\|→]] | $\phi(t)=(1-p+pe^{t})^{n}$           |
