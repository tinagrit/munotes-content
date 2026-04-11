Lecture 22
See [[3_Markovs Inequality#Tail Inequalities|Tail inequalities]]

> [!fail] This note is partially complete.


## Chernoff Bound
For $G_{1},G_{2},\dots,G_{n}$ independent random variables and their sum $S$, then for $c\geq 1$:
$$
\text{Pr}[S\geq c\mathbb{E}[S]]\leq \exp(-\beta(c)\mathbb{E}[S])
$$
where $\beta(c)=c\ln(c)-c+1$


### Moment generating function (MGF) bound
$$
\mathbb{E}[c^{S}]\leq \exp((c-1)\mathbb{E}[S])
$$

### Convexity bound
For any $G_{i}$,
$$
\mathbb{E}[c^{G_{i}}]\leq \exp((c-1)\mathbb{E}[G_{i}])
$$

