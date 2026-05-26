Lecture 3

## Probability
See more: [CMPT 210 > Axioms](https://munotes.tinagrit.com/CMPT210/3-probability/2_axioms.html)

> [!warning] Note
> In [CMPT 210 Notes](https://munotes.tinagrit.com/CMPT210/3-probability/2_axioms.html), we use $\text{Pr}[E]$ to denote the probability for the event $E$, and $\text{Pr}[\overline{E}]$ for the complement.
> 
> In STAT 271, we use $P(E)$ for the probability and $P(E^{c})$ for the complement. They mean the same thing.

There are two interpretations of the probability:
1. **Frequency**: proportion of **repeated experiments** that result in the outcome, such as 50% of coin tosses are heads
2. **Subjective**: statement of **beliefs** of the chance of an outcome, such as 1% chance of getting into a car accident

### Events
The **sample space** is the set of all possible outcomes, while an **event** is a set of outcomes.

The rules for event operations, including but not limited to:

| Rule             | Meaning                                                                                |
| ---------------- | -------------------------------------------------------------------------------------- |
| Commutative law  | $A\cup B = B\cup A$<br>$A\cap B = B\cap A$                                             |
| Associative law  | $(A\cup B)\cup C=A\cup (B\cup C)$<br>$(A\cap B)\cap C=A\cap (B\cap C)$                 |
| Distributive law | $(A\cup B)\cap C=(A\cap C)\cup (B\cap C)$<br>$(A\cap B)\cup C=(A\cup C)\cap (B\cup C)$ |

### Axioms and Propositions

| #                                                                                                                               | Meaning                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Axiom 1                                                                                                                         | $0 \leq P(E) \leq 1$                                                                                                     |
| Axiom 2                                                                                                                         | $P(S)=1$                                                                                                                 |
| Axiom 3                                                                                                                         | For disjoint ($E_{i}\cap E_{j} = \varnothing$), then <br>$P\left( \bigcup_{i=1}^{n}E_{i} \right)=\sum_{i=1}^{n}P(E_{i})$ |
| Proposition 1<br>[Complement](https://munotes.tinagrit.com/CMPT210/3-probability/3_probability-rules.html#Complement_rules)     | $P(E^{c})=1-P(E)$                                                                                                        |
| Proposition 2<br>[Inclusion-Exclusion](https://munotes.tinagrit.com/CMPT210/3-probability/3_probability-rules.html#Union_Bound) | $P(E\cup F)=P(E)+P(F)-P(E\cap F)$                                                                                        |

### Conditional Probability
See more: [CMPT 210 > Conditional Probability](https://munotes.tinagrit.com/CMPT210/4-conditional-probability/1_conditional-probability.html)

**Conditioning** is the process of **updating** [probability](https://munotes.tinagrit.com/CMPT210/3-probability/2_axioms.html#Probability_Function) as new information or evidence arises.

We can write this conditioning as:
$$
P(A\mid B)
$$
, which means the probability of Event $A$ occurring, such that Event $B$ has **already** occurred.

We can calculate the probability by:
$$
P(A\mid B)=\dfrac{P(A\cap B)}{P(B)}
$$

### Law of Total Probability
See more: [CMPT 210 > Total Probability](https://munotes.tinagrit.com/CMPT210/4-conditional-probability/6_total-probability.html)

For two events $A,B \subseteq S$, the probability $P(A)$ can be written as conditional probabilities.

$$
P(A)=P(A\mid B)P(B)+P(A\mid B^{c})P(B^{c})
$$

### Bayes' formula
See more: [CMPT 210 > Bayes' Rule](https://munotes.tinagrit.com/CMPT210/4-conditional-probability/5_bayes-rule.html)

For mutually exclusive events $F_{1},F_{2},\dots,F_{n}$, such that $\bigcup_{i=1}^{n}F_{i}=S$ (all of $F_{i}$s combined to make $S$), then:
$$
P(F_{j}\mid E)=\dfrac{P(E\mid F_{j})P(F_{j})}{P(E)}
$$
and
$$
P(F_{j}\mid E)=\dfrac{P(E\mid F_{j})P(F_{j})}{\sum_{i=1}^{n} P(E\mid F_{j})P(F_{j})}
$$
due to law of total probability.

### Independence
See more: [CMPT 210 > Conditional Probability](https://munotes.tinagrit.com/CMPT210/4-conditional-probability/1_conditional-probability.html#Independence)

When two events are **independent**, they are **not connected**. Event $A$ occurring does not make event $B$ more or less likely to occur.

If $A$ and $B$ are independent **if and only if**:
$$
P(A\mid B)=P(A)
$$
, then,
$$
P(A\cap B)=P(A)P(B)
$$
