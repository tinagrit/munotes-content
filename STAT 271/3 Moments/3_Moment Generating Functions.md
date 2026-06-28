Lectures 8 & 9

## Moment Generating Function (MGF)
The **MGF** of a random variable $X$, denoted $\phi(t)$, is defined as follows:

If $X$ is [[2_Random Variables#Types of Random Variables|discrete]], it is defined in terms of [[3_Distribution Functions#Probability Mass Function (PMF)|the PMF]]:
$$
\phi(t)=E[e^{tX}]=\sum_{x} e^{tx}p(x) 
$$
If $X$ is [[2_Random Variables#Types of Random Variables|continuous]], it is defined in terms of [[3_Distribution Functions#Probability Density Function (PDF)|the PDF]]:
$$
\phi(t)=E[e^{tX}]=\int_{-\infty}^{\infty}e^{tx}f(x)\,dx
$$

The [[1_Expectation#The nth moment|nth moment]] of $X$ is equal to the MGF's **nth derivative** with respect to $t$ at $t=0$:
$$
E[X^{n}]=\phi^{(n)}(0)
$$
Therefore, the first derivative of MGF at $t=0$ is equal to $E[X]$:
$$
\phi'(0)=E[X]
$$

### Properties of MGF
The MGF of a **sum of** [[2_Random Variables#Independence|independent]] random variables is the **product** of their MGFs:
$$
\phi_{X+Y}(t)=(\phi_{X}(t))(\phi_{Y}(t))
$$
if $X$ and $Y$ are independent, and more generally:
$$
\phi_{\sum_{i=1}^{n}X_{i} }(t)=\prod_{i=1}^{n} \phi_{X_{i}}(t)
$$

The MGF also **uniquely determines** the [[3_Distribution Functions#Cumulative Distribution Function (CDF)|CDF]] of a random variable, meaning that if two random variables have **the same MGF**, then:
- they also have **the same CDF**: $\phi_{X}(t)=\phi_{Y}(t) \implies F_{X}(t)=F_{Y}(t)$
- they have the same probability distribution