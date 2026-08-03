Lectures 16-17

## Interval estimate
This type of parametric estimation returns **an interval** in which the parameter lies with a certain **confidence**.

The interval uses the probability distribution of the [[1_Point Estimation#Point Estimate|point estimator]].

The confidence can be **one-sided**, $(a,\infty)$ $(-\infty,b)$, or **two-sided**, $(a,b)$.

We will be discussing the confidence intervals for the [[4_Normal Distribution#Normal Random Variable|normal distribution]], for $\mu$ and $\sigma^{2}$.

The **confidence level** is defined as $1-\alpha$. What this means is that by using an approach to determine many confidence intervals, $100(1-a)\%$ of them will contain the true mean $\mu$.

### For mean with known variance
Consider a sample of size $n$ from a normal population with parameters $\mu$ and $\sigma^{2}$. Suppose $\mu$ is unknown but $\sigma^{2}$ is known.

For the point estimator $\overline X$, we [[4_Sampling from Normal#Sampling from Normal Variables|know that]]:
$$
\dfrac{\overline X - \mu}{\sigma/\sqrt{ n }}\sim N(0,1)
$$
Therefore, the confidence level is:
$$
1-\alpha=P\left\{ -z_{\alpha/2} < \dfrac{\overline X - \mu}{\sigma/\sqrt{ n }} < z_{\alpha / 2} \right\} 
$$
Note: $z_{a}$ refers to the [[4_Normal Distribution#Percentile of Standard Normal|percentile of standard normal]].

The normal curve is divided into:
$$
\begin{align}
\dfrac{\alpha}{2} &  & 1-\alpha &  & \dfrac{\alpha}{2}
\end{align}
$$
where the middle $1-\alpha$ is the confident part.

By rearranging the equation, we get that using the estimate $\overline X=\overline x$, we get the $100(1-\alpha)\%$ **two-sided** confidence interval for $\mu$:
$$
\boxed{ \left( \overline x - z_{\alpha/2}\dfrac{\sigma}{\sqrt{ n }},\overline x + z_{\alpha / 2}\dfrac{\sigma}{\sqrt{ n }} \right)  }
$$

If we divide the normal curve into:
$$
\begin{align}
\alpha &  & 1-\alpha
\end{align}
$$
instead, we can construct one-sided confidence intervals:
$$
\begin{align}
\boxed{ \left( -\infty, x + z_{\alpha}\dfrac{\sigma}{\sqrt{ n }} \right) }  &  & \boxed{ \left( x - z_{\alpha}\dfrac{\sigma}{\sqrt{ n }},\infty \right) }
\end{align}
$$

### For mean with unknown variance
Consider a sample of size $n$ from a normal population with parameters $\mu$ and $\sigma^{2}$. Suppose that both $\mu$ and $\sigma^{2}$ are unknown.

For the point estimator $\overline X$, we [[4_Sampling from Normal#t-Distribution|know that]]:
$$
 \frac{\overline X - \mu}{S/\sqrt{ n }}\sim t_{n-1} 
$$
Therefore, the confidence level is:
$$
1-\alpha=P\left\{ -t_{\alpha / 2,n-1} < \sqrt{ n }\dfrac{\overline X -\mu}{S}<t_{\alpha /2,n-1} \right\} 
$$

By rearranging the equation, we get that using the estimate $\overline X=\overline x$ and $S=s$, we get the $100(1-\alpha)\%$ **two-sided** confidence interval for $\mu$:
$$
\boxed{ \left( \overline x -t_{\alpha /2,n-1} \dfrac{s}{\sqrt{ n }},\overline x +t_{\alpha /2,n-1}\dfrac{s}{\sqrt{ n }} \right)  }
$$

We can also construct one-sided confidence intervals:
$$
\begin{align}
\boxed{ \left( -\infty, \overline x +t_{\alpha ,n-1} \dfrac{s}{\sqrt{ n }}\right)  } &  & \boxed{ \left( \overline x -t_{\alpha ,n-1} \dfrac{s}{\sqrt{ n }},\infty\right) }
\end{align}
$$

### For variance
Consider a sample of size $n$ from a normal population with parameters $\mu$ and $\sigma^{2}$. Suppose that both $\mu$ and $\sigma^{2}$ are unknown.

We [[4_Sampling from Normal#Sampling from Normal Variables|know that]]:
$$
\dfrac{(n-1)S^{2}}{\sigma^{2}}\sim \chi_{n-1}^{2}
$$
Therefore, the confidence level is:
$$
1-\alpha =P\left\{ \chi_{1-\alpha /2,n-1}^{2} < \dfrac{(n-1)S^{2}}{\sigma^{2}} < \chi_{\alpha /2,n-1}^{2} \right\} 
$$

By rearranging the equation, we get that using the estimate $S^{2}=s^{2}$, we get the $100(1-\alpha)\%$ **two-sided** confidence interval for $\sigma^{2}$:
$$
\boxed{ \left( \dfrac{(n-1)s^{2}}{\chi_{\alpha /2,n-1}^{2}},\dfrac{(n-1)s^{2}}{\chi_{1-\alpha /2,n-1}^{2}} \right)  }
$$

