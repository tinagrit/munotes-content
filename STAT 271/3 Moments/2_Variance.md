Lectures 6-8

## Variance
While the [[1_Expectation#Expected value|expected value]] summarizes the **location** of the distribution, the **variance**, denoted $\text{Var}[X]$, measures the **spread** (how far off the mean) of the distribution.

This is measured as the **expectation of** [[1_Expectation#Squared Prediction Error|squared]] **distance** between $X$ and its mean.
$$
\text{Var}[X]=E[(X-\mu)^{2}]
$$
or similarly
$$
\text{Var}[X]=E[X^{2}]-\mu^{2}
$$
where $\mu=E[X]$, the mean of $X$.

### Linear Transformation
Unlike expectation, variance is not a linear operator, but has a linear identity:
$$
\text{Var}[aX+b]=a^{2}\text{Var}[X]
$$
Since variance measures the spread, simply doing $+b$ will shift the entire distribution, and **will not change** the spread itself.

Therefore:
- $\text{Var}[aX]=a^{2}\text{Var}[X]$
- $\text{Var}[X+b]=\text{Var}[X]$

### Sum of Random Variables
We can calculate $\text{Var}[X_{1}+X_{2}+\dots +X_{n}]$ by:
$$
\text{Var}\left[ \sum_{i=1}^{n} X_{i} \right]=\sum_{i=1}^{n}\text{Var}[X_{i}]+2\sum_{i=1}^{n} \sum_{j=i+1}^{n}\text{Cov}[X_{i},X_{j}]  
$$

For $n=2$, or where $\text{Var}[X+Y]$, we have:
$$
\text{Var}[X+Y]=\text{Var}[X]+\text{Var}[Y]+2\text{Cov}[X,Y]
$$

### Standard deviation
The **population** standard deviation, denoted $\sigma$, is the square root of variance. It has the **same unit** as the variance.
$$
\sigma_{X}=\sqrt{ \text{Var}[X] }
$$
Using the variance linear transformation, the standard deviation linear transformation is:
$$
\sigma_{aX+b}=|a|\sigma_{X}
$$


---
## Covariance
The covariance, denoted $\text{Cov}[X,Y]$, measures the **strength of linear relationship** between two random variables, is defined as:
$$
\text{Cov}[X,Y]=E[(X-\mu_{x})(Y-\mu_{y})]
$$
or:
$$
\text{Cov}[X,Y]=E[XY]-\mu_{x}\mu_{y}
$$

- A **positive** covariance indicates that $X$ and $Y$ tend to move in the **same** direction. 
- A **negative** covariance indicates that $X$ and $Y$ tend to move in **opposite** directions.

If $X$ and $Y$ are [[2_Random Variables#Independence|independent]], then $\text{Cov}[X,Y]=0$.

Some covariance properties include:
1. $\text{Cov}[X,Y]=\text{Cov}[Y,X]$
2. $\text{Cov}[X,X]=\text{Var}[X]$
3. $\text{Cov}[aX,Y]=a\text{Cov}[X,Y]$
4. $\text{Cov}[X_{1}+X_{2},Y]=\text{Cov}[X_{1},Y]+\text{Cov}[X_{2},Y]$

General additive property:
$$
\text{Cov}\left[ \sum_{i=1}^{n} X_{i},\sum_{j=1}^{m} Y_{j} \right] =\sum_{i=1}^{n} \sum_{j=1}^{m} \text{Cov}[X_{i},Y_{j}]
$$

### Correlation
A normalized covariance, dimensionless, denoted $\rho$. Can take values $-1\leq \rho \leq 1$.
$$
\rho=\text{Corr}[X,Y]=\dfrac{\text{Cov}[X,Y]}{\sqrt{ \text{Var}[X]\text{Var}[Y] }}
$$
