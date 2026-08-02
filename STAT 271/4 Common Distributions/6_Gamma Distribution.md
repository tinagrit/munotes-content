Lecture 13

## Gamma Random Variable
A gamma random variable takes parameters $\alpha$ and $\lambda$. If $X$ is a gamma random variable, it is written as:
$$
X\sim \Gamma(\alpha,\lambda)
$$

This distribution approximates the **time until** $\alpha$ **events have occurred**.

The Gamma function is
$$
\Gamma(\alpha)=\int_{0}^{\infty}e^{-y}y^{\alpha-1}\,dy
$$
, or for integers,
$$
\Gamma(n)=(n-1)!
$$

| Property                                                                  | Formula                                                                                |
| ------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| PDF [[3_Distribution Functions#Probability Density Function (PDF)\|→]]    | $f(x)=\dfrac{\lambda e^{-\lambda x}(\lambda x)^{\alpha-1}}{\Gamma(\alpha)}$, $x\geq 0$ |
| Mean [[1_Expectation#Expected value\|→]]                                  | $E[X]=\dfrac{a}{\lambda}$                                                              |
| Variance [[2_Variance#Variance\|→]]                                       | $\text{Var}[X]=\dfrac{a}{\lambda^{2}}$                                                 |
| MGF [[3_Moment Generating Functions#Moment Generating Function (MGF)\|→]] | $\phi(t)=\left(\dfrac{\lambda}{\lambda -t}\right)^{a}$, $t<\lambda$                    |

### Reduction Property
With $\alpha = 1$, we are looking for the time it takes for 1 event to occur. This is simply [[5_Exponential Distribution#Exponential Random Variable|exponential distribution]].
$$
X\sim \Gamma(1,\lambda)=\text{Exp}(\lambda)
$$

### Sum of Independent Gamma
For independent $X_{i}\sim \Gamma(\alpha_{i},\lambda)$ where $i=1,2,\dots,n$, we have:
$$
\sum_{i=1}^{n}X_{i}\sim \Gamma \left( \sum_{i=1}^{n} \alpha_{i},n \right)  
$$

### Sum of Independent Exponential
For $n$ independent $X_{i}\sim \text{Exp}(\lambda)$, we have:
$$
\text{Exp}(\lambda)=\Gamma(1,\lambda)\implies \sum_{i=1}^{n}X_{i}=\Gamma(n,\lambda) 
$$
