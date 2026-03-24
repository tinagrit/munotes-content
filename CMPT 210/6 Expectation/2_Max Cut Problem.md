Lecture 16

## Max Cut Problem

Given a **graph** $G=(V,E)$ with:
- $V$ be a set of vertices (nodes)
- $E$ be a set of edges

![[chart28.png|250]]

The max cut problem splits the vertices in $V$ into two groups: $S$, $T$ such that the number of edges between $S$ and $T$, labelled as $\delta(S)$ is maximized.

![[chart29.png|500]]

By definition, $\delta(S)$ is the set of edges with one endpoint in $S$, and the other in the [[1_Sets#Set operations|complement]] $T=V\backslash S$
$$
\delta(S)=\left\{ (v_{i},v_{j})\in E \mid v_{i} \in S \text{ and }v_{j} \in T \right\} 
$$

The max cut problem is ***NP-hard***, meaning that we seek an approximate solution such that:
$$
|\delta(S)|\geq \alpha \cdot \text{OPT}
$$
where
- $\alpha \in \left\{ 0,1 \right\}$ is the multiplicative approximation factor
- $\text{OPT}$ is the size of the optimal cut


### Erdos Algorithm
Select $S$ to be a random subset of $V$. 
For each node $v \in V$, independently assign $v$ to the set $S$ with probability $0.5$.

The [[1_Expectation#Expectation|expected]] size of the cut of $S$ satisfies:
$$
\mathbb{E}[|\delta(S)|] \geq 0.5 \cdot \text{OPT}
$$
A random assignment yields a cut that is **at least half as good** as the absolute best cut.

Proof:
Let $X_{v_{i},v_{j}}$ be an [[2_Random Variables#Indicator Random Variable|indicator random variable]] that:
- is $1$ if the edge $(v_{i},v_{j})$ is a "good edge" ($\in \delta(S)$)
- is $0$ if it is not

Finding the expectation using the [[1_Expectation#Indicator random variable|property]] of indicators:
$$
\begin{align}
\mathbb{E}[|\delta(S)|] & =\mathbb{E}\left[ \sum_{(v_{i},v_{j} )\in E} \displaystyle X_{v_{i},v_{j}}  \right] \\
 & =\sum_{(v_{i},v_{j}) \in E}^{} \mathbb{E}[X_{v_{i},v_{j}}] \\
 & =\sum_{(v_{i},v_{j}) \in E}^{}\text{Pr}[\delta(S)]   & (1)
\end{align}
$$

By definition, the edge $(v_{i},v_{j})$ is a good edge ($\in \delta(S)$) if:
$$
(v_{i} \in S \text{ and }v_{j} \in T)\text{ or }(v_{j} \in S\text{ and }v_{i}\in T)
$$
Since these two brackets are [[1_Probability#Mutual Exclusiveness|mutually exclusive]], the joint probability is the sum:
$$
\text{Pr}[\delta(S)]=\text{Pr}[(v_{i}\in S)\cap(v_{j} \in T)]+\text{Pr}[(v_{j} \in S)\cap (v_{i}\in T)]
$$
Since the two expressions inside of each probability function is [[1_Conditional Probability#Independence|independent]], we can split them:
$$
\begin{align}
\text{Pr}[\delta(S)] & =\text{Pr}[v_{i}\in S]\text{Pr}[v_{j}\in T]+\text{Pr}[v_{j}\in S]\text{Pr}[v_{i}\in T] \\
 & =(0.5)(0.5)+(0.5)(0.5) \\
 & = 0.5 & (2)
\end{align}
$$

Substituting the result of $(2)$ into $(1)$, we get:
$$
\begin{align}
\mathbb{E}[|\delta(S)|] & =\sum_{(v_{i},v_{j})\in E}0.5  \\
 & =0.5 \cdot |E|
\end{align}
$$

Since we know that the optimal cut size ($\text{OPT}$) can never be larger than $|E|$, we know that $|E| \geq \text{OPT}$, and:
$$
\mathbb{E}[|\delta(S)|]\geq 0.5 \cdot \text{OPT}
$$

