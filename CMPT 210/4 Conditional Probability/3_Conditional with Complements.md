Lecture 9

## Conditional with complements

For two events $A,B \subseteq S$, then the [[1_Conditional Probability#Conditional Probability|Conditional Probability]] is:
$$
\text{Pr}[\overline{A} \mid B]=1-\text{Pr}[A\mid B]
$$

### Proof
For any events $A,B \subseteq S$,
$$
\begin{align}
\begin{cases}
S=A \cup \overline{A} \\
B=S\cap B
\end{cases} &  &
\implies B=(A\cup \overline{A})\cap B
\end{align}

$$

By [[1_Sets#Distributive law|Distributive law]], we have that:
$$
B=(A\cap B)\cup (\overline{A}\cap B)
$$
$$
\implies \text{Pr}[B]=\text{Pr}[\underbrace{ (A\cap B) }\cup \underbrace{ (\overline{A}\cap B) }]
$$
Since $(A\cap B)$ and $(\overline{A}\cap B)$ are mutually exclusive,
$$
\implies \text{Pr}[B]=\text{Pr}[A\cap B]+\text{Pr}[\overline{A}\cap B]
$$
Dividing both sides by $\text{Pr}[B]$, it follows that
$$
1=\dfrac{\text{Pr}[A\cap B]}{\text{Pr}[B]}+\dfrac{\text{Pr}[\overline{A}\cap B]}{\text{Pr}[B]}
$$
Substituting with the conditional probability form:
$$
1=\text{Pr}[A\mid B]+\text{Pr}[\overline{A}\mid B]
$$
Rearranging:
$$
\text{Pr}[\overline{A}\mid B]=1-\text{Pr}[A\mid B]
$$

