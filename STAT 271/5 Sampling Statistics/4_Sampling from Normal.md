Lecture 15

## Sampling from Normal Variables
From [[2_Sample Mean Distribution#Central Limit Theorem|Central Limit Theorem]], we know that if the underlying population is [[4_Normal Distribution#Normal Random Variable|normally]] distributed, then the sample is **also normal**.

Consider independent $X_{i}\sim N(\mu, \sigma^{2})$ where $i=1,2,\dots,n$. Then, the [[2_Sample Mean Distribution#Sample Mean Distribution|sample mean]] $\overline X$ and the [[3_Sample Variance Distribution#Sample Variance Distribution|sample variance]] $S^{2}$ are **independent** random variables with:

$$
\overline X \sim N(\mu, \sigma^{2} / n)
$$
$$
\dfrac{\overline X - \mu}{\sigma/\sqrt{ n }}\sim N(0,1)
$$
, and,
$$
\dfrac{(n-1)S^{2}}{\sigma^{2}}\sim \chi_{n-1}^{2}
$$
(see [[7_Chi-Square Distribution|Chi-Square distribution]])


### t-Distribution
The $\frac{\overline X - \mu}{\sigma/\sqrt{ n }}\sim N(0,1)$ formula assumes that the population variance $\sigma^{2}$ is available. If it is not, we can estimate it by using the **sample variance** $S^{2}$ instead: $\frac{\overline X - \mu}{S/\sqrt{ n }}$. 

However, since $S$ is random, the distribution is **not normal**. The expression is using **t-Distribution** instead.
$$
\boxed{ \frac{\overline X - \mu}{S/\sqrt{ n }}\sim t_{n-1} }
$$
It is similar to $N(0,1)$, but with heavier tails.

Formally, the the distribution of
$$
\dfrac{z}{\sqrt{ \chi_{n}^{2} /n }}
$$
is called the **t-Distribution** or **Student Distribution** with $n$ degrees of freedom, $t_{n}$.

The t-Distribution table helps calculate $t_{\alpha,n}$ where $\alpha$ is the area to the right, and $n$ refers to the degree of freedom.
Note that $t_{\alpha,\infty}=z_{\alpha}$, refer to [[4_Normal Distribution#Percentile of Standard Normal|percentile of standard normal]].