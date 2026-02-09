Lecture 9

## Bayes rule

For two events $A,B \subseteq S$, the [[1_Conditional Probability#Conditional Probability|Conditional Probability]] is:
$$
\text{Pr}[B\mid A]=\dfrac{\text{Pr}[A\mid B]\cdot \text{Pr}[B]}{\text{Pr}[A]}
$$
if $\text{Pr}[A]\neq 0$ and $\text{Pr}[B]\neq 0$.

### Generalizing
The Bayes rule implies that:
$$
\text{posterior}=\dfrac{\text{likelihood}\cdot \text{prior}}{\text{evidence}}
$$
where:
- **Prior** ($\text{Pr}[B]$) is the initial belief about $B$
- **Likelihood** ($\text{Pr}[A \mid B]$) is the probability of observing $A$ given $B$
- **Evidence** ($\text{Pr}[A]$) is the total probability of $A$ under all possible cases (normalizing constant)
- **Posterior** ($\text{Pr}[B\mid A]$) is the probability of the hypothesis

### Proof
By the definition of conditional probabilities:
$$
\text{Pr}[A\mid B]=\dfrac{\text{Pr}[A\cap B]}{\text{Pr}[B]}
$$
Since $\text{Pr}[A\cap B]=\text{Pr}[B\cap A]$,
$$
\text{Pr}[A\mid B]=\dfrac{\text{Pr}[B\cap A]}{\text{Pr}[B]}
$$
Rearranging, we get:
$$
\begin{align}
\text{Pr}[B\cap A]=\text{Pr}[A\mid B]\cdot \text{Pr}[B] &  & (1)
\end{align}

$$

---
Also, by the definition of conditional probabilities
$$
\text{Pr}[B\mid A]=\dfrac{\overbrace{ \text{Pr}[B\cap A] }}{\text{Pr}[A]}
$$
Replacing $\text{Pr}[B\cap A]$ with the derived expression from $(1)$,
$$
\text{Pr}[B\mid A]=\dfrac{\text{Pr}[A\mid B]\cdot \text{Pr}[B]}{\text{Pr}[A]}
$$
