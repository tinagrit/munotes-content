Lecture 10

## Law of Total Probability

For two events $A,B \subseteq S$, the probability $\text{Pr}[A]$ can be written as [[1_Conditional Probability#Conditional Probability|conditional probabilities]]:
$$
\text{Pr}[A]=\text{Pr}[A\mid B]\text{Pr}[B]+\text{Pr}[A\mid \overline{B}]\text{Pr}[\overline{B}]
$$

### Simpson's Paradox
A statistical phenomenon where a trend appears in different groups of data, but **reverses or disappears** when these groups are combined.

![[Screenshot 2026-02-08 at 11.22.21 PM.png|400]]

For example, two increasing groups of data appear to be decreasing when combined.


### Proof
For any events $A,B \subseteq S$:
$$
\begin{align}
\begin{cases}
S=B \cup \overline{B} \\
A=S\cap A
\end{cases} &  &
\implies A=(B\cup \overline{B})\cap A
\end{align}

$$

By [[1_Sets#Distributive law|Distributive law]], we have that:
$$
A=(B\cap A)\cup (\overline{B}\cap A)
$$
$$
\implies \text{Pr}[A]=\text{Pr}[\underbrace{ (B\cap A) }\cup \underbrace{ (\overline{B}\cap A) }]
$$
Since $(B\cap A)$ and $(\overline{B}\cap A)$ are mutually exclusive,
$$
\begin{align}
\implies \text{Pr}[A]=\text{Pr}[B\cap A]+\text{Pr}[\overline{B}\cap A] &  & (1)
\end{align}
$$
---
By the definition of conditional probabilities:
$$
\text{Pr}[A\mid B]=\dfrac{\text{Pr}[A\cap B]}{\text{Pr}[B]}
$$
Rearranging:
$$
\begin{align}
\text{Pr}[B\cap A]=\text{Pr}[A\mid B]\text{Pr}[B] &  & (2)
\end{align}
$$

---
By the definition of conditional probabilities:
$$
\text{Pr}[A\mid \overline{B}]=\dfrac{\text{Pr}[A\cap \overline{B}]}{\text{Pr}[\overline{B}]}
$$
Rearranging:
$$
\begin{align}
\text{Pr}[\overline{B}\cap A]=\text{Pr}[A\mid \overline{B}]\text{Pr}[\overline{B}] &  & (3)
\end{align}
$$

---
Substituting $(2)$ and $(3)$ into $(1)$, we get:
$$
\text{Pr}[A]=\text{Pr}[A\mid B]\text{Pr}[B]+\text{Pr}[A\mid \overline{B}]\text{Pr}[\overline{B}]
$$
