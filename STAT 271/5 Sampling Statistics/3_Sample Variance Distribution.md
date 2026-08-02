Lecture 15

## Sample Variance Distribution
Consider a random *iid* **sample** $X_{1},X_{2},\dots,X_{n}$, taken from population where the **population mean** is $\mu$, and **population variance** is $\sigma^{2}$.

The [[2_Common Statistics#Sample variance|sample variance]], defined by:
$$
S^{2}=\dfrac{1}{n-1}\sum_{i=1}^{n}(X_{i}-\overline{X})^{2} 
$$
is a [[2_Random Variables#Random Variables|random variable]], since it is determined by $n$ random variables.

### Expected value
To find the sample variance's [[1_Expectation#Expected value|expected value]]:
$$
\begin{align}
(n-1)E[S^{2}] & =E\left[ \sum_{i=1}^{n}(X_{i}-\overline{X})^{2}  \right]  \\
 & =E\left[ \sum_{i=1}^{n} X_{i}^{2} \right]-nE\left[\overline{X}^{2}\right] \\
 & = nE[X_{1}^{2}]-nE[\overline X^{2}] \\
 & =n\left( \text{Var}[X_{1}]+E[X_{1}]^{2} \right)-n\left( \text{Var}[\overline X] +E[\overline X] \right)^{2} \\
 &  = n\sigma^{2}+n\mu^{2}-n(\sigma^{2}/n)-n\mu^{2} \\
 &  = (n-1)\sigma^{2} 
\end{align}
$$
$$
\implies \boxed{ E[S^{2}]=\sigma^{2} }
$$

The expected sample variance is the population variance.