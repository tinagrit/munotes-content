Lecture 20

## Covariance
For two random variables $R_{1}$ and $R_{2}$, the **covariance** between $R_{1}$ and $R_{2}$ is:
$$
\text{Cov}[R_{1},R_{2}]=\mathbb{E}[(R_{1}-\mathbb{E}[R_{1}])(R_{2}-\mathbb{E}[R_{2}])]
$$
An alternative computation is:
$$
\text{Cov}[R_{1},R_{2}]=\mathbb{E}[R_{1}R_{2}]-\mathbb{E}[R_{1}]\mathbb{E}[R_{2}]
$$

Covariance takes the [[1_Variance and SD#Variance|Variance]] of **multiple** [[2_Random Variables#Random Variable|random variables]]. If we plug in the same random variables into a $\text{Cov}$:
$$
\begin{align}
\text{Cov}[R,R] & =\mathbb{E}[(R-\mathbb{E}[R])(R-\mathbb{E}[R])] \\
 & = \mathbb{E}[(R-\mathbb{E}[R])^{2}] \\
 & = \mathbb{E}[(R-\mu)^{2}] \\
 & =\text{Var}[R]
\end{align}
$$

### Independence
If $R_{1}$ and $R_{2}$ are independent, then their covariance **is zero**. However, the opposite isn't always true.

### Symmetric
The covariance between any two random variables is symmetric
$$
\text{Cov}[R_{1},R_{2}]=\text{Cov}[R_{2},R_{1}]
$$

### Sum of Variance
For two non-independent random variables, their sum of variance can be calculated by:
$$
\begin{align}
\text{Var}[R_{1}+R_{2}] & =\text{Var}[R_{1}]+\text{Var}[R_{2}]+2(\mathbb{E}[R_{1}R_{2}]-\mathbb{E}[R_{1}]\mathbb{E}[R_{2}]) \\
 & =\text{Var}[R_{1}]+\text{Var}[R_{2}]+2\text{Cov}[R_{1},R_{2}]
\end{align}
$$


---
## Correlation
For two random variables $R_{1}$ and $R_{2}$, the **correlation** between $R_{1}$ and $R_{2}$ is:
$$
\text{Corr}[R_{1},R_{2}]=\dfrac{\text{Cov}[R_{1},R_{2}]}{\sqrt{ \text{Var}[R_{1}]\text{Var}[R_{2}] }}
$$

Correlation is a normalized covariance. It has no unit, and can be $\in [-1,1]$.

### Independence
If $R_{1}$ and $R_{2}$ are independent, then their covariance is zero, and their correlation **is also zero**. 

