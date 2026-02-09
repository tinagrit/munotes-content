Lecture 8

## Multiplication rule

If we have 3 events $X,Y,Z \subseteq S$, the joint probability is given by [[1_Conditional Probability#Conditional Probability|conditional probabilities]]:
$$
\text{Pr}[X\cap Y\cap Z]=\text{Pr}[X]\cdot\text{Pr}[Y\mid X]\cdot \text{Pr}[Z\mid X\cap Y]
$$

### Proof
Using the standard definition of conditional probability $\text{Pr}[X\mid Y]$:
$$
\text{Pr}[A\mid B]=\dfrac{\text{Pr}[A\cap B]}{\text{Pr}[B]}
$$

We can rewrite these two terms using the definition:
$$
\text{Pr}[X\cap Y\cap Z]=\text{Pr}[X]\cdot\underbrace{ \text{Pr}[Y\mid X] }\cdot \underbrace{ \text{Pr}[Z\mid X\cap Y] }
$$
$$
\begin{align}
\text{Pr}[Y\mid X]=\dfrac{\text{Pr}[X\cap Y]}{\text{Pr}[X]} &  & \text{Pr}[Z\mid X\cap Y]=\dfrac{\text{Pr}[X\cap Y\cap Z]}{\text{Pr}[X\cap Y]}
\end{align}
$$

Substituting back in:
$$
\text{Pr}[X\cap Y\cap Z]=\cancel{ \text{Pr}[X] }\cdot\dfrac{\cancel{ \text{Pr}[X\cap Y] }}{\cancel{ \text{Pr}[X] }}\cdot \dfrac{\text{Pr}[X\cap Y\cap Z]}{\cancel{ \text{Pr}[X\cap Y] }}
$$
$$
\text{Pr}[X\cap Y\cap Z]=\text{Pr}[X\cap Y\cap Z]
$$

### Generalizing
For $n$ events $E_{1},E_{2},\dots,E_{n} \subseteq S$, their joint probability is given by:
$$
\text{Pr}\left[\bigcap_{i=1}^{n}E_{i}\right]=\text{Pr}[E_{1}]\cdot \text{Pr}[E_{2}\mid E_{1}]\cdot \text{Pr}[E_{3}\mid E_{1}\cap E_{2}]\dots\text{Pr}[E_{n}\mid E_{1}\cap E_{2}\cap \dots E_{n-1}]
$$

The joint probability considers the event that **all events** occur. Therefore, we consider:
- The probability of $E_{1}$
- The probability that $E_{2}$ occurs given that $E_{1}$ occurs
- The probability that $E_{3}$ occurs given that $E_{1}$ and $E_{2}$ occurs
- and so on

