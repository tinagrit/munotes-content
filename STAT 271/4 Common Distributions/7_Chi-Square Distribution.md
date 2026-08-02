Lecture 13

## Chi-Square Random Variable
A chi-square random variable takes a parameter $n$. If $X$ is a chi-square random variable, it is written as:
$$
X\sim \chi_{n}^{2}
$$

This distribution approximates the **sum of squared deviation** with $n$ degrees of freedom.

The chi-square is the [[6_Gamma Distribution#Gamma Random Variable|Gamma distribution]] with $\alpha=\dfrac{n}{2}$ and $\lambda=\dfrac{1}{2}$. This means that if $n=2$, then $X\sim\chi_{2}^{2}=\text{Exp}(1/2)$.

If $Z_{i}$ is a [[4_Normal Distribution#Standard Normal Distribution|standard normal variable]], then:
$$
X=Z_{1}^{2}+Z_{2}^{2}+\dots+Z_{n}^{2}\implies X\sim\chi_{n}^{2}
$$

| Property                                                                  | Formula                                                            |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| PDF [[3_Distribution Functions#Probability Density Function (PDF)\|→]]    | $f(x)=\dfrac{0.5 e^{-x/2}(x/2)^{n/2-1}}{\Gamma(n / 2)}$, $x\geq 0$ |
| Mean [[1_Expectation#Expected value\|→]]                                  | $E[X]=n$                                                           |
| Variance [[2_Variance#Variance\|→]]                                       | $\text{Var}[X]=2n$                                                 |
| MGF [[3_Moment Generating Functions#Moment Generating Function (MGF)\|→]] | $\phi(t)=(1-2t)^{-n/2}$, $t< \dfrac{1}{2}$                         |

### Sum of Independent
For independent $X_{i}\sim \chi_{n_{i}}^{2}$ where $i=1,2,\dots,n$, we have: $$\sum_{i=1}^{n}X_{i}\sim \chi_{\sum_{i=1}^{n}n_{i}}^{2}$$


