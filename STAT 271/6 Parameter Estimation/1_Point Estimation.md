Lecture 15

## Point Estimate
This type of parametric estimation returns **a single value** as an estimate of the parameter.

### Method of Moments (MoM)
Consider a distribution with $p$ parameters and a sample of size $n$.

The method of moments consists of matching the **sample moment** to the corresponding theoretical moments. The estimate is **any solution** of the $p$ equations:
$$
\boxed{ E[X^{k}]=\dfrac{1}{n}\sum_{i=1}^{n} x_{i}^{k} }
$$
where $E[X^{k}]$ is the $k$th moment of the distribution, and $x_{i}$ are the $n$ independent observations in the sample.

For example, if $\overline{X}=9$ and $\frac{1}{5}\sum_{i=1}^{5}x_{i}^{2}=88.2$, and $X\sim \text{Bin}(n,p)$, we can estimate $n$ and $p$ by:

$$
\begin{align}
E[X]=\overline X = 9 \implies 9=\hat{n}\hat{p} \implies  \hat{n}=\dfrac{9}{\hat{p}} &  & (1)
\end{align}
$$
$$
\begin{align}
E[X^{2}]=\dfrac{1}{n}\sum_{i=1}^{n} x_{i}^{2}=88.2\implies  \hat{n}\hat{p}(1-\hat{p})+(\hat{n}\hat{p})^{2}=88.2 &  & (2)
\end{align}
$$
$$
\begin{align}
(1)\to(2) &  & \left( \dfrac{9}{\hat{p}}\right)\hat{p}(1-\hat{p})+\left( \dfrac{9}{\hat{p}}\cdot  \hat{p} \right)^{2} & =88.2  \\
 &  &  \hat{p} & =0.2
\end{align}
$$
$$
\begin{align}
(1)&&\hat{n}=\dfrac{9}{\hat{p}}=\dfrac{9}{0.2}=45
\end{align}
$$

### Maximum Likelihood Estimators (MLE)
Let $\theta$ be the parameters of the population distribution. The MLE $\hat{\theta}$ is the value of $\theta$ that maximizes the **likelihood function** $L(\theta)$.

The likelihood function is the [[4_Joint Distribution#Joint and Marginal PDF|joint PDF]] or [[4_Joint Distribution#Joint and Marginal PMF|PMF]] of the $n$ observations as a function of $\theta$.
$$
L(\theta)=f(x_{1},x_{2},\dots,x_{n}\mid\theta)=\prod_{i=1}^{n}f(x_{i}\mid\theta)
$$

It is often easier to maximize the **log-likelihood** function instead:
$$
l(\theta)=\ln L(\theta)=\prod_{i=1}^{n}\ln f(x_{i}\mid\theta)
$$

Since the value of $\theta$ is unknown, but **fixed**, we:
- cannot ask *which of the* $\theta$ *is most likely true, based on the data* $P(\theta\mid\text{data})$
- can ask *for which value of* $\theta$ *is the data most likely to have occurred* $P(\text{data}\mid\theta)$

For [[2_Poisson Distribution#Poisson Random Variable|Poisson distribution]], the MLE is $\hat{\lambda}=\overline X$

For [[4_Normal Distribution#Normal Random Variable|Normal distribution]], the MLE is $\hat{\mu}=\overline X$ and $\hat{\sigma}=\sqrt{ \dfrac{1}{n}\sum_{i=1}^{n}(X_{i}-\overline X)^{2} }$

The steps to find the MLE is as follows:
1. Take the PDF of the distribution, substitute in $L(\theta)=\prod_{i=1}^{n}f(x_{i}\mid\theta)$
2. For each parameter of the distribution, **differentiate** $L(\theta)$ with respect to the parameter
3. For each derivative, set $L'(\theta)=0$ and solve for the parameter estimate
4. Verify that the point is the **maximum** (not the minimum)
5. Show that the estimator is [[#Properties of Estimators|unbiased and consistent]]


---
## Properties of Estimators
There are two desirable properties of estimators:
1. **Unbiasedness**
	- On average, the estimator should give us the ***true*** value of the parameter
	- An estimator is unbiased if $E[\hat{\theta}]=\theta$
	- The bias is defined as $E[\hat{\theta}]-\theta$

2. **Consistency**
	- The estimator should ***get better*** as the sample size increases
	- An estimator is consistent if $\displaystyle\lim_{ n \to \infty }P(|\hat{\theta}_{n}-\theta|>\epsilon)=0$
	- (Not necessary) an estimator is asymptotically unbiased when $\displaystyle\lim_{n\to\infty}\text{Var}\left[\hat{\theta}_n\right]=0$

To show that an estimator satisfies both properties, verify that:
$$
\begin{align}
E[\hat{\theta}]=\theta &  & \lim_{ n \to \infty } \text{Var}\left[ \hat\theta_{n} \right]=0 
\end{align}
$$
