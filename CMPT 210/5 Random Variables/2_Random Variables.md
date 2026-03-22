Lecture 12

## Random Variable

A random variable $R$ on a [[2_Axioms#Probability Function|probability space]] is a [[2_Functions#Partial functions|total function]] that:
- takes an element of $S$ (a sample space $S$ domain)
- returns a **real number** (a subset of real number codomain)

For example, tossing 2 coins, the outcome can either be $H$ for head, or $T$ for tail. The random variable $R$ is the number of heads. We have:
- $S=\left\{ HH,HT,TH,TT \right\}$
- $R:S\to \left\{ 0,1,2 \right\}$ where
	- $R(HH)=2$
	- $R(HT)=1$
	- $R(TH)=1$
	- $R(TT)=0$

In this case, $R$ is also a [[3_Distribution Functions#Bernoulli distribution|Bernoulli random variable]] since it only takes in binary values (2 choices)
$$
R=\begin{cases}
0 & \text{if the outcome is }H \\
1 & \text{if the outcome is }T
\end{cases}
$$


### Indicator Random Variable

The indicator random variable $I_{E}$ **flags the occurrence** of a specific event $E$ in the sample space $S$
- takes an element of $S$ (a sample space $S$ domain)
- returns either $1$ for yes, and $0$ for no

$$
I_{E}(w)=\begin{cases}
1 & \text{if }w\in  E \\
0 & \text{if }w \not\in E
\end{cases}
$$

Using the coin example above, let $E$ be the event that we tossed two of the same faces.
- $I_{E}(w)=1$ for outcomes $HH$ and $TT$ (yes)
- $I_{E}(w)=0$ for outcomes $HT$ and $TH$ (no)

