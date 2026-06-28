Lecture 11

## Uniform Random Variable
A uniform [[2_Random Variables#Types of Random Variables|continuous]] random variable takes parameters $\alpha$ and $\beta$. If $X$ is a uniform random variable, it is written as:
$$
X\sim \text{U}[\alpha,\beta]
$$

This distribution models a **value chosen randomly** from an interval, each subinterval equally likely, where $\alpha$ is the smallest possible value, and $\beta$ is the largest possible value.

| Property                                                                  | Formula                                                                                                               |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| PDF [[3_Distribution Functions#Probability Density Function (PDF)\|→]]    | $f(x)=\begin{cases}\dfrac{1}{\beta-\alpha} & \text{if }\alpha \leq x \leq \beta \\\\ 0 & \text{otherwise}\end{cases}$ |
| Mean [[1_Expectation#Expected value\|→]]                                  | $E[X]=\dfrac{\alpha+\beta}{2}$                                                                                        |
| Variance [[2_Variance#Variance\|→]]                                       | $\text{Var}[X]=\dfrac{(\beta-\alpha)^{2}}{12}$                                                                        |
| MGF [[3_Moment Generating Functions#Moment Generating Function (MGF)\|→]] | $\phi(t)=\begin{cases}\dfrac{e^{t\beta}-e^{t\alpha}}{t(\beta-\alpha)}&t\neq 0\\\\1&t=0\end{cases}$                    |
