Lecture 12

## Exponential Random Variable
An exponential random variable takes a parameter $\lambda$. If $X$ is an exponential random variable, it is written as:
$$
X\sim \text{Exp}(\lambda)
$$

This distribution approximates the **time until an event occurs**. For example, time until an earthquake, time until the next phone call, etc.

| Property                                                                   | Formula                                                              |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| PDF [[3_Distribution Functions#Probability Density Function (PDF)\|→]]     | $f(x)=\begin{cases}\lambda e^{-\lambda x}&x\geq 0\\0&x<0\end{cases}$ |
| CDF [[3_Distribution Functions#Cumulative Distribution Function (CDF)\|→]] | $F(x)=\int_{0}^{x}\lambda e^{-\lambda y}\,dy=1-e^{-\lambda x}$       |
| Mean [[1_Expectation#Expected value\|→]]                                   | $E[X]=\dfrac{1}{\lambda}$                                            |
| Variance [[2_Variance#Variance\|→]]                                        | $\text{Var}[X]=\dfrac{1}{\lambda^{2}}$                               |
| MGF [[3_Moment Generating Functions#Moment Generating Function (MGF)\|→]]  | $\phi(t)=\dfrac{\lambda}{\lambda -t}$, $t<\lambda$                   |

### Memoryless Property
Exponential variables are the **only** memoryless variables. The distribution of the length of time until the next event **is independent** of how long ago the last event occurred.

A random variable $X$ is memoryless if:
$$
P(X>s+t\mid X>t)=P(X>s)
$$
for all $s,t \geq 0$.

Also,
$$
E[X-t\mid X>t]=E[X]
$$
For example, if the time it takes to receive a call is $X\sim \text{Exp}(1/2)$, then the mean is $E[X]=2$. For someone who's already been waiting for 5 minutes, the average time to wait more is $E[X-5\mid X>5]=E[X]=2$ minutes, since it is memoryless.

### Minimum of Independent
Consider $n$ [[2_Random Variables#Independence|independent]] random variables distributed exponentially $X_{i}\sim \text{Exp}(\lambda_{i})$ where $i=1,2,\dots,n$.

The **minimum** of $X_{1},X_{2},\dots ,X_{n}$ is exponential with $\lambda=\sum_{i=1}^{n}\lambda_{i}$.

$$
\min(X_{1},X_{2},\dots,X_{n})\sim \text{Exp}\left( \sum_{i=1}^{n}\lambda_{i}  \right)
$$

### Scaling
If $X\sim \text{Exp}(\lambda)$, then:
$$
cX\sim \text{Exp}\left( \dfrac{\lambda}{c} \right) 
$$
for $c>0$.


---
## Poisson process
Recall that [[2_Poisson Distribution#Poisson Random Variable|Poisson distribution]] approximates the **number of events** happening in a fixed time.

Let $N(t)$ be the number of events occurred within the first $t$ seconds. $[0,t]$. $N(t)$ is a **Poisson process** with rate $\lambda >0$.

The time it takes for the first event of a Poisson process $T_{1}$ has an exponential distribution with mean $1/\lambda$.
The time between event $n-1$ and event $n$, $T_{n}$, has an exponential distribution with mean $1/\lambda$.

A Poisson process has these properties:

### Process begins
$$
N(0)=0
$$
At time 0, no event must have occurred.

### Independent increments
$$N(t_{2})-N(t_{1}) \text{ and } N(t_{4})-N(t_{3})\text{ independent}$$ for $t_{1}<t_{2}<t_{3}<t_{4}$. This means that knowing the number of events occurring during $t_{1}$ and $t_{2}$ tells us nothing about the number of events occurring during $t_{3}$ and $t_{4}$.

### Stationary increments
$$
\begin{align}
\lim_{ h \to 0 } \dfrac{P\left\{ N(h)=1 \right\} }{h}=\lambda &  & P\left\{ N(h)=1 \right\} \approx \lambda h 
\end{align}
$$
for small $h$. This means that for a very short interval $h$, the probability that only 1 event has occurred is relative to the interval length itself. 
For example, if an average of $3$ purchases occur per hour, for $0.01$ hour, the probability that $1$ purchase occurred is $\approx3\times 0.01=0.03$.

$$
\begin{align}
\lim_{ h \to 0 } \dfrac{P\left\{ N(h)\geq 2 \right\} }{h}=0  &  & P\left\{ N(h)\geq 2 \right\}\approx 0  
\end{align}
$$
for small $h$. This means that for a very short interval $h$, the probability that more than 2 events occurred approaches $0$ as $h$ gets small.

### Distribution
For a Poisson process $N(t)$ with rate $\lambda$,
$$
N(t)\sim \text{Po}(\lambda t)
$$
due to the [[2_Poisson Distribution#Reproductive Property|Reproductive Property]] of Poisson distribution.