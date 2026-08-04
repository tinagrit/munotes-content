Lectures 18-19

## Test for mean with known variance
Let $X_{i}$ be a [[4_Normal Distribution#Normal Random Variable|normal variable]] $\sim N(\mu,\sigma^{2})$, where $\mu$ is unknown but $\sigma^{2}$ is known.

### Two-sided test
To test the [[1_Hypothesis Testing#Hypothesis Testing|null hypothesis]] $H_{0}:\mu=\mu_{0}$ against $H_{1}:\mu\neq \mu_{0}$, we use the [[2_Sample Mean Distribution#Sample Mean Distribution|sample mean]] as the point estimator of $\mu$ to determine the [[1_Hypothesis Testing#Critical region|critical region]].

We will reject $H_{0}$ if the sample mean $\overline X$ is too far from $\mu_{0}$ by $c$, that is:
$$
|\overline X -\mu_{0}|>c\implies \text{reject}
$$
In this case, we let $c$ be $z_{\alpha / 2}\frac{\sigma}{n}$. Therefore,
$$
\boxed{ \dfrac{|\overline X-\mu_{0}|}{\sigma / \sqrt{ n }}>z_{\alpha / 2} } \implies \text{reject}
$$
The value on the left is called the **test statistic** (TS).

The p-value is calculated using $\boxed{ 2P(Z>TS) }$. If the p-value is $\leq \alpha$, reject the hypothesis.

### One-sided test
To test the null hypothesis $H_{0}:\mu=\mu_{0}$ against $H_{1}:\mu <\mu_{0}$, we **only reject** cases where $\overline X$ is **significantly smaller** than $\mu_{0}$.

We will reject:
$$
\boxed{ \dfrac{\overline X-\mu_{0}}{\sigma / \sqrt{ n }}<-z_{\alpha} } \implies \text{reject}
$$

Similarly, to test the null hypothesis $H_{0}:\mu=\mu_{0}$ against $H_{1}:\mu>\mu_{0}$, we **only reject** cases where $\overline X$ is **significantly larger** than $\mu_{0}$.

We will reject:
$$
\boxed{ \dfrac{\overline X-\mu_{0}}{\sigma / \sqrt{ n }}>z_{\alpha} } \implies \text{reject}
$$

---
## Test for mean with unknown variance
Let $X_{i}$ be a normal variable $\sim N(\mu,\sigma^{2})$, where both $\mu$ and $\sigma^{2}$ are unknown.

### Two-sided test
To test the null hypothesis $H_{0}:\mu=\mu_{0}$ against $H_{1}:\mu\neq \mu_{0}$, we use the [[2_Sample Mean Distribution#Sample Mean Distribution|sample mean]] as the point estimator of $\mu$, and the [[3_Sample Variance Distribution#Sample Variance Distribution|sample variance]] as the point estimator of $\sigma^{2}$ to determine the [[1_Hypothesis Testing#Critical region|critical region]].

We will reject:
$$
\boxed{ \dfrac{|\overline X-\mu_{0}|}{S / \sqrt{ n }}>t_{\alpha / 2,n-1} } \implies \text{reject}
$$

### One-sided test
To test the null hypothesis $H_{0}:\mu=\mu_{0}$ against $H_{1}:\mu <\mu_{0}$, we **only reject** cases where $\overline X$ is **significantly smaller** than $\mu_{0}$.

We will reject:
$$
\boxed{ \dfrac{\overline X-\mu_{0}}{S / \sqrt{ n }}<-t_{\alpha,n-1} } \implies \text{reject}
$$

Similarly, to test the null hypothesis $H_{0}:\mu=\mu_{0}$ against $H_{1}:\mu>\mu_{0}$, we **only reject** cases where $\overline X$ is **significantly larger** than $\mu_{0}$.

We will reject:
$$
\boxed{ \dfrac{\overline X-\mu_{0}}{S / \sqrt{ n }}>t_{\alpha,n-1} } \implies \text{reject}
$$

---
## Using Confidence Interval
Hypothesis tests and [[2_Confidence Intervals#Interval estimate|confidence intervals]] rely on the probability distribution of a test statistic.

A hypothesis test at significance level $\alpha$ can be done **using confidence interval** at the $1-\alpha$ confidence level.

A level $\alpha$ hypothesis will reject $H_{0}:\mu=\mu_{0}$ if $\mu_{0}$ is **outside** the $1-\alpha$ confidence level two-sided confidence interval.