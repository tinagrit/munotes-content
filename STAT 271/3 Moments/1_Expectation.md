Lectures 6 & 9-10

## Expected value
The **expectation**, **mean**, or the **first moment**, denoted $E[X]$, is the weighted average of all possible values of a [[2_Random Variables#Random Variables|random variable]] $X$.

For a [[2_Random Variables#Types of Random Variables|discrete]] random variable $X$, the expectation is:
$$
{E}[X]=\sum_{i=1}^{\infty}x_{i}p(x_{i}) 
$$

For a [[2_Random Variables#Types of Random Variables|continuous]] random variable $X$, the expectation is:
$$
E[X]=\int_{-\infty}^{\infty}xf(x)\,dx
$$

While $E[X]$ is measured in the **same unit as** $X$, it does **not** have to be a possible value. For example, rolling a fair 6-sided die, the expectation is $3.5$.

The expectation is a **linear operator**, which means:
$$
E[aX+b]=aE[X]+b
$$
Also, the **expectation of a sum** of random variables is the sum of their expected values:
$$E[X+Y]=E[X]+E[Y]$$
$$
E[X_{1}+X_{2}+\dots +X_{n}]=E[X_{1}]+E[X_{2}]+\dots+E[{X_{n}}]
$$


### Law of the Unconscious Statistician
If we have a random variable $Y$ defined in terms of another random variable $X$, like:
$$
Y=g(X)
$$
Then, we can apply apply this law to find $E[Y]=E[g(X)]$:

For a discrete random variable $Y$, the expectation is:
$$
E[Y]=E[g(X)]=\sum_{i=1}^{\infty}g(x_{i})p(x_{i}) 
$$
For a continuous random variable $Y$, the expectation is:
$$
E[Y]=E[g(X)]=\int_{-\infty}^{\infty}g(x)f_{X}(x)\,dx
$$

### The nth moment
Since $E[X]$ is the **first moment** of $X$, the **nth moment** of $X$, denoted $E[X^{n}]$, using the Law of the Unconscious Statistician, is:

For a discrete random variable $X$, the nth moment is:
$$
E[X^{n}]=\sum_{i=1}^{\infty}x_{i}^{n}p(x_{i}) 
$$
For a continuous random variable $X$, the nth moment is:
$$
E[X^{n}]=\int_{-\infty}^{\infty}x^{n}f_{X}(x)\,dx
$$

### Non-negative random variable
If we have a non-negative random variable $X$, we can find the expected value using the **complement** of [[3_Distribution Functions#Cumulative Distribution Function (CDF)|the CDF]].
$$
E[X]=\int_{0}^{\infty}(1-F(x))\,dx
$$

The $(1-F(x))$ is called the **survival function**.

### Strong Law of Large Numbers
Consider a sequence of **independent** and **identically distributed** random variables $X_{1},X_{2},\dots,X_{n}$ with each one having mean $E[X_{i}]=\mu$.

The average of all $n$ random variables,
$$
\overline{X}_{n}=\dfrac{X_{1}+X_{2}+\dots+X_{n}}{n}
$$
**converge** to $\mu$.

Formally,
$$
P\left\{ \lim_{ n \to \infty } \overline{X}_{n}=\mu \right\}=1 
$$
The probability that the sample average converge to $\mu$ is $1$.

### Median
Like [[2_Common Statistics#Sample median|sample median]], median is a measure of [[2_Common Statistics#Central Tendency|Central Tendency]]. For a continuous random variable, the median, denoted $m$, is the **value where** [[3_Distribution Functions#Cumulative Distribution Function (CDF)|CDF]] $= 0.5$.

Essentially, we solve for
$$
F(m)=0.5
$$

For example:
> Find the median of $X$, given the PDF of $X$ is:
> $$f_{X}(x)=e^{-x}$$ for $x>0$

Finding $F_{X}(a)$:
$$
\begin{align}
F_{X}(a) & = \int_{-\infty}^{a}f_{X}(x)\,dx \\
 & =\int_{0}^{a}e^{-x}\,dx \\
 & = [-e^{-x}]_{0}^{a} \\
 & =-e^{-a}+1
\end{align}
$$

Finding $m$ where $F(m)=0.5$:
$$
\begin{align}
0.5 & = -e^{-m}+1 \\
0.5 & =e^{-m} \\
m & =-\log(0.5) \\
m & =0.6931
\end{align}
$$

---
## Best Predictor
As we predict the value of a random variable $X$, suppose we predict that the value is $c$.

### Squared Prediction Error
The squared prediction error is $(X-c)^{2}$, then the expected value of error is $E[(X-c)^{2}]$.

It turns out that:
$$
E[(X-c)^{2}]\geq E[(X-\mu)^{2}]
$$
, which means that the smallest error is achieved when:
$$
c=\mu
$$
, which is **the mean**.

### Absolute Prediction Error
The absolute prediction error is $|X-c|$, then the expected value of error is $E[|X-c|]$.

It turns out that if we differentiate $E{[|X-c|]}$ and set it to 0, we get:
$$
F(c)=0.5
$$
, which means that the smallest error is achieved when:
$$
c=m
$$
, which is **the median**.

