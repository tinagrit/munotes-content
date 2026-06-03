Lectures 3 & 5

## Random Variables
See more: [CMPT 210 > Random Variables](https://munotes.tinagrit.com/CMPT210/5-random-variables/2_random-variables.html)

A random variable is a **real number numerical quantity** of interest determined by the [[1_Probability#Events|outcome]].

A random variable $R$ is a total function that:
- takes an element of $S$ (a sample space $S$ domain)
- returns a **real number** (a subset of real number codomain)

### Indicator variable
The indicator random variable $I_{E}$ **flags the occurrence** of a specific event $E$ in the sample space $S$
- takes an element of $S$ (a sample space $S$ domain)
- returns either $1$ for yes, and $0$ for no

$$
I_{E}(w)=\begin{cases}
1 & \text{if }w\in  E \\
0 & \text{if }w \not\in E
\end{cases}
$$

### Types of Random Variables
1. **Discrete** random variables take values from **countable sets** (finite or 1-1 with natural numbers)
2. **Continuous** random variables take values from **uncountable sets** (real numbers)

### Independence
If we have two [[1_Probability#Independence|independent]] random variables, then for any $A$, $B$,
$$
P\left\{ X\in A, Y \in B \right\}=P\left\{ X \in A \right\}P\left\{ Y \in B \right\}   
$$

If we have $n$ independent random variables $X_{1},X_{2},\dots,X_{n}$, then for any sets $A_{1},A_{2},\dots,A_{n}$,
$$
P\left\{ X_{1}\in A_{1},X_{2}\in A_{2},\dots,X_{n}\in A_{n} \right\}=\prod_{i=1}^{n}P\left\{ X_{i}\in A_{i} \right\}   
$$
