Lecture 12

## Normal Random Variable
A normal [[2_Random Variables#Types of Random Variables|continuous]] random variable takes parameters $\mu$ and $\sigma^{2}$. If $X$ is a normal random variable, it is written as:
$$
X\sim \text{N}[\mu,\sigma^{2}]
$$

This distribution models values in a **bell curve** that are **likely to be near** [[1_Expectation#Expected value|the mean]] ($\mu$), with probabilities decreasing symmetrically as we go farther away.

| Property                                                                   | Formula                                                                                                             |
| -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| PDF [[3_Distribution Functions#Probability Density Function (PDF)\|→]]     | $f(x)=\dfrac{1}{\sqrt{ 2\pi\sigma }}e^{-(x-\mu)^{2}/2\sigma^{2}}$                                                   |

The PDF:
- has a **maximum value** of $\dfrac{1}{\sqrt{ 2\pi\sigma }}\approx \dfrac{0.4}{\mu}$ at the centre ($x=\mu$).
- has **two inflection points** at $x=\mu\pm \sigma$

The normal distribution is also a good approximation for [[1_Binomial Distribution#Binomial Random Variable|binomial distribution]] with $n$ large:
$$
X\sim \text{Bin}(n,p) \approx \text{N}[\mu,\sigma^{2}]=\text{N}[np,np(1-p)]
$$

A **linear transformation** of a normal variable is **also** a normal variable.
Let $Y=a+bX$ where $X\sim \text{N}[\mu,\sigma^{2}]$, then:
$$
Y\sim \text{N}[a+b\mu,b^{2}\sigma^{2}]
$$

### Standard Normal Distribution
A normal distribution is **standard** when $\mu=0$ and $\sigma=1$. Let $Z$ be a standard normal random variable, then $Z\sim \text{N}[0,1]$.

| Property                                                                   | Formula                                                                                                             |
| -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| PDF [[3_Distribution Functions#Probability Density Function (PDF)\|→]]     | $f(z)=\dfrac{1}{\sqrt{ 2\pi }}e^{-z^{2}/2}$                                                                         |
| CDF [[3_Distribution Functions#Cumulative Distribution Function (CDF)\|→]] | $\displaystyle\Phi(z)=\dfrac{1}{\sqrt{ 2\pi }}\int_{-\infty}^{z}e^{-y^{2}/2}\,dy$<br><br>Note: $\Phi(-z)=1-\Phi(z)$ |
| Mean [[1_Expectation#Expected value\|→]]                                   | $E[Z]=0$                                                                                                            |
| Variance [[2_Variance#Variance\|→]]                                        | $\text{Var}[Z]=1$                                                                                                   |
| MGF [[3_Moment Generating Functions#Moment Generating Function (MGF)\|→]]  | $\phi(t)=e^{t^{2}/2}$                                                                                               |

If $X$ is a **linear transformation** of $Z$, that is $X=\mu+\sigma Z$, then:

| Property                                                                  | Formula                               |
| ------------------------------------------------------------------------- | ------------------------------------- |
| Mean [[1_Expectation#Expected value\|→]]                                  | $E[X]=\mu$                            |
| Variance [[2_Variance#Variance\|→]]                                       | $\text{Var}[X]=\sigma^{2}$            |
| MGF [[3_Moment Generating Functions#Moment Generating Function (MGF)\|→]] | $\phi(t)=e^{\mu t+\sigma^{2}t^{2}/2}$ |

### Percentile of Standard Normal
The $100(1-\alpha)$<sup>th</sup> [[2_Common Statistics#Percentiles|percentile]] is $z_{\alpha}$ where:
$$
\alpha = 1-\Phi(z_{\alpha})
$$

For example, the 75<sup>th</sup> percentile, $\alpha=0.25$, is:
$$
\begin{align}
0.25 & =1-\Phi(z_{0.25}) \\
\Phi(z_{0.25}) & =0.75 \\
z_{0.25} & = 0.674
\end{align}
$$

### Standard Normal Table
The standard normal table provides the CDF $\Phi(x)$ value based on the $x$ input.

![[Screenshot 2026-07-01 at 2.51.48 PM.png|500]]

This table takes $x$ to 2 decimal places. For example, if we want to find $\Phi(2.93)$, we need to locate $2.9$ on the left, and $+0.05$ on the top, then we get the value $\Phi(2.93)=0.9983$.

![[chart03.png|400]]

### Sum of Independent Normal Variables
The sum of [[2_Random Variables#Independence|independent]] normal variables **is also normal**.

Let $X_{i}\sim N(\mu_{i},\sigma_{i}^{2})$ where $i=1,2,\dots,n$, then the [[3_Moment Generating Functions#Properties of MGF|MGF of their sum]] is:
$$
\begin{align}
\phi(t) & =\prod_{i=1}^{n} \phi_{x_{i}}(t) \\
 & =\prod_{i=1}^{n} e^{\mu_{i}t+\sigma_{i}^{2}t^{2}/2} \\
 & = e^{t\sum_{i=1}^{n} \mu_{i}+\left( t^{2}/2 \right)\sum_{i=1}^{n} \sigma_{i}^{2} } \\
 & =e^{\mu t+\sigma^{2}t^{2}/2}
\end{align}
$$
where $\mu = \sum_{i=1}^{n}\mu_{i}$ and $\sigma^{2}=\sum_{i=1}^{n}\sigma_{i}^{2}$.

Therefore:
$$
\sum_{i=1}^{n} X_{i}\sim \text{N}\left[ \sum_{i=1}^{n} \mu_{i},\sum_{i=1}^{n} \sigma_{i}^{2} \right]
$$

