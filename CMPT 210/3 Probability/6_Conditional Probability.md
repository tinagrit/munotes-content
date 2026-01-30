Lecture 7

## Conditional Probability

**Conditioning** is the process of **updating** [[2_Axioms#Probability Function|probability]] as new information or evidence arises.

For example, the probability of rolling a $6$ from a 6-sided die is $\dfrac{1}{6}$. Our sample space is $\left\{ 1,2,3,4,5,6 \right\}$.

However, if we now know that the roll was **an even number**, the probability of rolling a $6$ now increases to $\dfrac{1}{3}$. The set of all possible outcomes is now $\left\{ 2,4,6 \right\}$.

Our sample space did not change, but the probability increases since:
- Event $A$: getting a $6$
- Event $B$: getting an even number
- Event $A$ is **conditioned on** Event $B$

We can write this conditioning as:
$$
\text{Pr}[A\mid B]
$$
, which means the probability of Event $A$ occurring, such that Event $B$ has **already** occurred.

We can calculate the probability by:
$$
\text{Pr}[A\mid B]=\dfrac{\dfrac{|A\cap B|}{\cancel{ S }}}{\dfrac{|B|}{\cancel{ S }}}=\dfrac{|A\cap B|}{|B|}
$$

### Generalizing

For [[4_Uniform Probability#Uniform Probability Space|Uniform Probability Space]]:
$$
\text{Pr}[A\mid B]=\dfrac{|A\cap B|}{|B|}
$$
For any [[2_Axioms#Probability Function|probability space]]:
$$
\text{Pr}[A\mid B]=\dfrac{\text{Pr}[A\cap B]}{\text{Pr}[B]}
$$
