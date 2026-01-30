Lecture 6

## Complement rules
For an [[1_Probability#Sample Space|event]] $E$, the probability of the [[1_Probability#Complement|complement]] of $E$ is defined as:
$$
\text{Pr}[E]=1-\text{Pr}[\overline{E}]
$$

### Complement rules proof
Using the [[1_Probability#Complement|conditions]] of a complement, we know that:
- $E\cap \overline{E}=\varnothing$ ($E$ and $\overline{E}$ are mutually exclusive)
- $E\cup \overline{E} = S$

Since $E$ and $\overline{E}$ are mutually exclusive, we can write:
$$
\text{Pr}[E\cup \overline{E}]=\text{Pr}[E]+\text{Pr}[\overline{E}]
$$

On the left side, we can replace $E\cup \overline{E}$ with $S$ (due to the condition above).
$$
\text{Pr}[S]=\text{Pr}[E]+\text{Pr}[\overline{E}]
$$

We also know that $\text{Pr}[S]=1$ since it is [[2_Axioms#Probability Function|all possible outcomes]] of a probability function. It follows that:
$$
1=\text{Pr}[E]+\text{Pr}[\overline{E}]
$$

Rearranging, we get:
$$
\text{Pr}[E]=1-\text{Pr}[\overline{E}]
$$


---
## Inclusion-Exclusion

Recall the [[7_Inclusion-Exclusion Principle|Inclusion-Exclusion Principle]] for sets.
$$
|A\cup B|=|A|+|B|-|A\cap B|
$$

In probability, for any two events $E_{1},E_{2} \subseteq S$, the probability of their union is given by:
$$
\text{Pr}[E_{1}\cup E_{2}]=\text{Pr}[E_{1}]+\text{Pr}[E_{2}]-\text{Pr}[E_{1}\cap E_{2}]
$$

### Inclusion-Exclusion proof
From the union $E_{1}\cup E_{2}$, we can rewrite the expression as:
$$
(E_{1}-E_{2})\cup (E_{2}-E_{1})\cup (E_{1}\cap E_{2})
$$


---
## Union Bound
For any two events $E_{1},E_{2} \subseteq S$, then:
$$
\text{Pr}[E_{1} \cup E_{2}] \leq \text{Pr}[E_{1}]+\text{Pr}[E_{2}]
$$
Generally:
$$
\text{Pr}\left[ \bigcup_{i=1}^{n}E_{i}\right] \leq \sum_{i=1}^{n}\text{Pr}[E_{i}] 
$$

### Union Bound proof
Proving the two-event Union Bound using the [[#Inclusion-Exclusion|Inclusion-Exclusion rule]],

For $E_{1},E_{2} \subseteq S$ and we have $\text{Pr}[E_{1}\cup E_{2}]$, it follows that:
$$
\text{Pr}[E_{1}\cup E_{2}]=\text{Pr}[E_{1}]+\text{Pr}[E_{2}]-\underbrace{ \text{Pr}[E_{1}\cap E_{2}] }
$$
Focusing on the last term, we have:
$$
 \text{Pr}[E_{1}\cap E_{2}] \geq 0
$$
Since the [[2_Axioms#Probability Function|Probability Function]] must be **non-negative**.

Therefore, substituting:
$$
\text{Pr}[E_{1}\cup E_{2}]=\text{Pr}[E_{1}]+\text{Pr}[E_{2}]-(\text{number}\geq 0)
$$
It follows that:
$$
\text{Pr}[E_{1}\cup E_{2}]\leq\text{Pr}[E_{1}]+\text{Pr}[E_{2}]
$$


---
## Monotonicity
For any two events $E_{1},E_{2} \in S$,
$$
E_{1}\subseteq E_{2} \implies \text{Pr}[E_{1}] \leq \text{Pr}[E_{2}]
$$

### Monotonicity proof
For $E_{1} \subseteq E_{2}$, we have:
$$
E_{1}=E_{2}-(E_{2}-E_{1})
$$
(All of the elements in $E_{1}$ are shared with $E_{2}$)

This proof relies on the same concept as above, that probability must be **non-negative**.

Since $\text{Pr}[E_{2}-E_{1}]\geq 0$, we can conclude that:
$$
\text{Pr}[E_{1}]=\text{Pr}[E_{2}]-(\text{number}\geq 0)
$$
It follows that:
$$
\text{Pr}[E_{1}]\leq \text{Pr}[E_{2}]
$$
