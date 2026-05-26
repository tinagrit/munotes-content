Lecture 3

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

