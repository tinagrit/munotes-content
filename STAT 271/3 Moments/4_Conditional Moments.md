Lecture 9

## Conditional Moments
The [[1_Expectation#Expected value|mean]] and [[2_Variance#Variance|variance]] can be **conditioned** on an event, in terms of the [[5_Conditional Distribution#Conditional Distribution Function|conditional distribution functions]].

### Conditional expectation
The conditional [[1_Expectation#Expected value|expected value]] of $X$ given that $Y=y$ is:
$$
E[X|Y=y]=\int_{-\infty}^{\infty}xf_{X|Y}(x|y)\,dx
$$
, or more generally:
$$
E[g(X,Y)|Y=y]=\int_{-\infty}^{\infty}g(x,y)f_{X|Y}(x|y)\,dx
$$
where $g(X,Y)$ can be any function involving $X$ and $Y$.

Note that by the **law of total expectation**:
$$
E[E[X|Y]]=E[X]
$$

### Conditional variance
The conditional [[2_Variance#Variance|variance]] of $X$ given $Y=y$ is defined similar to the conditional expectation as $\text{Var}[X|Y=y]$.

Note that by the **law of total variance**:
$$
\text{Var}[E[X|Y]]+E[\text{Var}[X|Y]]=\text{Var}[X]
$$

