Lectures 20 & 21

## Tail Inequalities
How likely it is that a [[2_Random Variables#Random Variable|random variable]] is **far off its mean** ([[1_Expectation#Expectation|expectation]])

For example, if we have the mean at $X=\mu$, then tail inequalities measure:
- $\text{Pr}[X>\mu+a]$
- $\text{Pr}[X<\mu-a]$

Tail inequalities include:
- [[#Markov's Inequality]]
- [[4_Chebyshevs Inequality#Chebyshev's Inequality|Chebyshev's Inequality]]
- [[5_Chernoff Bound#Chernoff Bound|Chernoff Bound]]

### Markov's Inequality
If $X$ is a **non-negative** random variable, then the tail inequality can be found through expectation:
$$
\boxed{ \text{Pr}[X\geq a]\leq \dfrac{\mathbb{E}[X]}{a} }
$$

**Proof**:
Let $I$ be the [[2_Random Variables#Indicator Random Variable|indicator random variable]] that $X\geq a$, then the following is true:
$$
aI \leq X
$$
since
- if $X\geq a$, then $I=1$, and $a\leq X$
- if $X<a$, then $I=0$, and $0\leq X$ (Markov condition)

Since expectation is a monotonic operator, we can put both sides in the expectation:
$$
\mathbb{E}[aI]\leq \mathbb{E}[X]
$$
Rearranging:
$$
a\mathbb{E}[I]\leq \mathbb{E}[X]
$$
Substituting the [[1_Expectation#Indicator random variable|expectation]] of the indicator random variable:
$$
a\text{Pr}[X\geq a]\leq \mathbb{E}[X]
$$
Dividing both sides by $a$, we get:
$$
\text{Pr}[X\geq a]\leq \dfrac{\mathbb{E}[X]}{a}
$$

