Lecture 5

## Probability Function

The probability function on a [[1_Probability#Sample Space|sample space]] $S$ is a [[2_Functions#Partial functions|total function]] $\text{Pr}:S\to[0,1]$ such that $\displaystyle\sum_{w \in S}\text{Pr}[w]=1$.

The function maps $S$ to any number $r\in R$ within $[0,1]$. If we add up all the outcomes in $S$ ($w \in S$), we should get $1$ (100%).

This function can be extended to take [[1_Probability#Sample Space|an event]] $E \subseteq S$ as its argument:
$$
\text{Pr}[E]=\sum_{w\in E}\text{Pr}[w] 
$$

For example, rolling a 6-sided die, if the event is getting a $5$, we have:
- $S=\left\{ 1,2,3,4,5,6 \right\}$
- $E=\left\{ 5 \right\}$
- $\text{Pr}[E]=\dfrac{1}{6}\approx 0.167$

The **event space** ($F$) is a [[1_Sets#Sets|set]] of all possible events from a sample space $S$. This is the [[1_Sets#Power set|power set]] of $S$.

The **probability space** is a model that consists of:
- The sample space $S$
- The probability function $\text{Pr}$
- The event space $F$

