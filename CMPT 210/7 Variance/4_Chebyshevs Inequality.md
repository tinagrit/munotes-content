Lecture 21
See [[3_Markovs Inequality#Tail Inequalities|Tail Inequalities]]

## Chebyshev's Inequality
For a random variable $X$ and any constant $c>0$:
$$
\boxed{ \text{Pr}[|X-\mu|\geq c]\leq \dfrac{\text{Var}[X]}{c^{2}} }
$$

The measures the likeliness that a random variable value is off its mean by the addition of $c$.

If we take $c$ to be $=k\sigma$ with $k>0$ and $\sigma$ be the [[1_Variance and SD#Standard deviation|standard deviation]] of $X$, we can rewrite the formula as:
$$
\text{Pr}[|X-\mu|\geq k\sigma]\leq \dfrac{\text{Var}[X]}{(k\sigma)^{2}}
$$
Using the definition of variance and standard deviation, substituting $\text{Var}[X]$:
$$
\text{Pr}[|X-\mu|\geq k\sigma]\leq \dfrac{\sigma^{2}}{k^{2}\sigma^{2}}
$$
Then we have:
$$
\boxed{ \text{Pr}[|X-\mu|\geq k\sigma]\leq \dfrac{1}{k^{2}} }
$$


**Proof**:
We can use Markov's condition to prove this inequality. Let:
- $Y=|X-\mu|^{2}$
- threshold $c^{2}$ with $c>0$, strictly non-negative

Using the formula from Markov's inequality on $Y$, we get:
$$
\text{Pr}[Y\geq c^{2}] \leq \dfrac{\mathbb{E}[Y]}{c^{2}}
$$
Substituting $Y$:
$$
\text{Pr}[|X-\mu|^{2}\geq c^{2}]\leq \dfrac{\mathbb{E}[|X-\mu|^{2}]}{c^{2}}
$$
The numerator on the right side is the definition of variance:
$$
\text{Pr}[|X-\mu|^{2}\geq c^{2}]\leq \dfrac{\text{Var}[X]}{c^{2}}
$$
Since we know that $c>0$, then:
$$
\text{Pr}[|X-\mu|^{2}\geq c^{2}]=\text{Pr}[|X-\mu|\geq c]
$$
and:
$$
\text{Pr}[|X-\mu|\geq c]\leq \dfrac{\text{Var}[X]}{c^{2}}
$$

---
## Pairwise Independent Sampling

If we have $G_{1},G_{2},\dots,G_{n}$ independent random variables with the same mean and standard deviation, and their sum be $S$, then:
$$
\boxed{ \text{Pr}\left[ \left| \dfrac{S}{n}-\mu \right| \geq a \right] \leq \dfrac{1}{n}\left( \dfrac{\sigma}a \right)^{2}   }
$$

**Proof**:
Finding the expectation of $\dfrac{S}{n}$, we know that $\mathbb{E}[S]=n\mu$ since they all have the same mean and standard deviation, this implies that:
$$
\mathbb{E}[S]=n\mu \implies \dfrac{1}{n}\mathbb{E}[S]=\mu \implies \mathbb{E}\left[ \dfrac{S}{n} \right]=\mu 
$$

Finding the variance of $\dfrac{S}{n}$, we know that any variance is equal to $\sigma^{2}$, and the variance of the sum is then:
$$
\text{Var}[S]=n\sigma^{2}
$$
Using the [[1_Variance and SD#Linear Transformations|linear transformation]] property of variance, we can find:
$$
\begin{align}
\text{Var}\left[ \dfrac{S}{n} \right] & =\dfrac{1}{n^{2}}\text{Var}[S] \\
 & =\dfrac{n\sigma^{2}}{n} \\
 & =\dfrac{\sigma^{2}}{n}
\end{align} 
$$

Applying Chebyshev's inequality given $X=\dfrac{S}{n}$, we get:
$$
\text{Pr}\left[\left|\dfrac{S}{n}-\mu\right|\geq c\right]\leq \dfrac{\text{Var}\left[\dfrac{S}{n}\right]}{c^{2}}
$$
Substituting:
$$
\text{Pr}\left[\left|\dfrac{S}{n}-\mu\right|\geq c\right]\leq \dfrac{\sigma^{2}}{nc^{2}}
$$
Rearranging:
$$
\text{Pr}\left[\left| \dfrac{S}{n}-\mu \right| \geq c \right] \leq \dfrac{1}{n}\left( \dfrac{\sigma}c \right)^{2}
$$

### Weak Law of Large Numbers
As the number of samples ($n$) increases, it is more likely that the sample mean ($\frac{S}{n}$) is closer to the true mean of the sample ($\mu$)
$$
\begin{align}
\text{Pr}\left[ \left| \dfrac{S}{n}-\mu \right| \geq a \right] \to 0 &  & \text{as} &  & n\to \infty
\end{align}
$$
and conversely:
$$
\begin{align}
\text{Pr}\left[ \left| \dfrac{S}{n}-\mu \right| \lt a \right] \to 1 &  & \text{as} &  & n\to \infty
\end{align}
$$

**Proof**:
Using the formula for pairwise independent sampling:
$$
\text{Pr}\left[ \left| \dfrac{S}{n}-\mu \right| \geq a \right] \leq \dfrac{1}{n}\left( \dfrac{\sigma}a \right)^{2}
$$
Take the limit on both sides $n\to \infty$
$$
\begin{align}
\lim_{ n \to \infty } \text{Pr}\left[ \left| \dfrac{S}{n}-\mu \right|\right] & \leq \lim_{ n \to \infty } \dfrac{1}{n} \left( \dfrac{\sigma}a \right)^{2} \\
\lim_{ n \to \infty } \text{Pr}\left[ \left| \dfrac{S}{n}-\mu \right|\right] & \leq 0
\end{align}
$$
Any probability cannot be lower than $0$, then:
$$
\lim_{ n \to \infty } \text{Pr}\left[ \left| \dfrac{S}{n}-\mu \right|\right] = 0
$$
and therefore
$$
\begin{align}
\text{Pr}\left[ \left| \dfrac{S}{n}-\mu \right| \geq a \right] \to 0 &  & \text{as} &  & n\to \infty
\end{align}
$$
