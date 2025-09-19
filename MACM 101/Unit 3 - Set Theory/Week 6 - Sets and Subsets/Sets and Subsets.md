Section 3.1
## Sets
- **well-defined** collection of objects (*elements*, *members of a set*)
- **Capital** letters ($A$, $B$, $C$, $D$) to represent sets and **lowercase** letters ($a$, $b$, $c$ , $d$) to represent elements
- $x\in A$  means  $x$ is an element of $A$

- **Finite set**: $A=\{1,3,5,7,9\}$ 
- **Infinite set**: $B=\{ x| x\in \mathbb{Z} ^{+},x$ is odd$\}$

### Empty set
or the *null set* is the set containing ***no (0) elements***, denoted by $\varnothing$ or $\{\}$. The size of this set is 0. $|\varnothing|=0$


---
## Subset

$C$, $D$ are sets from a universe. $C$ is a **subset** of $D$.
- $C \subseteq D$:  every element of $C$ is an element of $D$
- $C\subset D$:  ($C$ is a *proper subset* of $D$) additionally $D$ also contains at least one more element that $C$ doesn't ($D$ is bigger than $C$)

For all sets $C$, $D$, 
- $C \subseteq D$ if and only if 
	$\forall x[x\in C \implies x \in D]$

In general,
- $C\subset D \implies C \subseteq D$
- $C\subseteq D \centernot\implies C\subset D$


> Consider:
> $A=\{1,3,5,7,9\}$
> $C=\{1,3,5,7,9\}$

- $A\subseteq C$  but  $A \not \subset C$

> Consider:
> $C=\{1,2\}$
> $D=\{1,2\}$

- $C\subseteq D$  but  $C \not \subset D$


### Set sizes

Size or cardinality is the number of elements in the set, for example, if $A = \{1,3,5,7,9\}$, then $|A| = 5$

For finite sets,
- $C\subseteq D \implies |C| \leq |D|$
- $C\subset D\implies |C| < |D|$


### Set Equality

$C=D$ when $C\subseteq D$ and $D \subseteq C$

- Order and repetition **do not** matter
- $\{1,2,3\}=\{3,1,2\}=\{2,2,1,3\}$


---
## Theorem

For a given universe (see [[Quantifiers]]) containing the sets $A$, $B$, $C$
- If $A\subseteq B$ and $B \subseteq C$
	- then $A \subseteq C$
	- Proof:
		- Consider element $x \in A$
		- Since $A \subseteq B$,   $x \in A \implies x \in B$
		- Also, since $B \subseteq C$,   $x \in B \implies x \in C$
		- $\therefore x\in A \implies x \in C$, and $x \subseteq C$

- If $A\subset B$ and $B\subseteq C$
	- then $A \subset C$
	- Proof:
		- Since $A \subset B$,   $x\in A \implies x\in B$
		- With $B \subseteq C$, it follows that $x\in C$, so $A\subseteq C$.
			- We still need to prove that $A\subset C$, not just $A\subseteq C$
		- 
		- However, $A\subset B$ means $\exists b,b\in B, b\not \in A$
			- There exists an element $b$ that is in $B$ but not in $A$
		- Since $B \subseteq C$,   $b\in B \implies b \in C$
		- Thus, $A\subseteq C$ and there exists $b\in C$ with $b \not \in A$
		- $\therefore A \subset C$

- If $A \subseteq B$ and $B \subset C$
	- then $A \subset C$

- If $A \subset B$ and $B \subset C$
	- then $A\subset C$


> $A=\{1,2,3\}$
> $B=\{3,4\}$
> $C=\{1,2,3,4\}$

The following relations hold:
- $A\subseteq C$
- $A \subset C$
- $B \subset C$
- $A \subseteq A$
- $A \not \subset A$
- $B \not \subseteq A$


---
## Power set
The power set of $A$, denoted $P(A)$ is the set of all subsets of $A$

> If $C=\{1,2,3\}$
> Then $P(C)=\{$
> 	$\varnothing$,
> 	$\{1\}$,
> 	$\{2\}$,
> 	$\{3\}$,
> 	$\{1,2\}$,
> 	$\{2,3\}$,
> 	$\{1,3\}$,
> 	$\{1,2,3\}$
> $\}$

### Number of subsets

To count the subsets for a set $D$ with $n$ elements:
- number of subsets of size 0: $1$ = $\binom{n}{0}$
- number of subsets of size 1: $n$ = $\binom{n}{1}$
- number of subsets of size 2: $\binom{n}{2}$
- number of subsets of size 3: $\binom{n}{3}$
- number of subsets of size $n$: $\binom{n}{n}$

$\displaystyle|P(D)|=\dbinom{n}{0}+\dbinom{n}{1}+\ldots+\dbinom{n}{n}=\sum_{i=0}^{n}\dbinom{n}{i}=2^n$ 
by the corollary to the [[Combinations with no repetition#The Binomial Theorem|Binomial Theorem]]

In general, for any finite set $A$ with $|A| = n \geq 0$, then $A$ has $2^n$ subsets and that $|P(A)| = 2^n$


---
## Common infinite sets

- $\mathbb{Z}$  = the set of **integers**
	- $\mathbb{N}$  = the set of *non-negative* integers or natural numbers
	- $\mathbb{Z}^+$  = the set of *positive* integers (zero not included)
	- $\mathbb{Z}_n$  = $\{0,1,2,3,\ldots,n-1\}$ for any $n\in\mathbb{Z}^+$ 

- $\mathbb{Q}$  = the set of **rational** numbers ($\frac{a}{b}$ where $a,b$ is integer and $b \neq 0$)
	- $\mathbb{Q}^+$  = the set of *positive* rational numbers
	- $\mathbb{Q}^{*}$  = the set of *non-zero* rational numbers

- $\mathbb{R}$  = the set of **real** numbers
	- $\mathbb{R}^+$  = the set of *positive* real numbers
	- $\mathbb{R}^{*}$  = the set of *non-zero* real numbers

- $\mathbb{C}$  = the set of **complex** numbers
	- $\mathbb{C}^{*}$  = the set of *non-zero* complex numbers

- for real numbers $a,b$ with $a<b$, 
	- $[a,b]=\{x\in\mathbb{R}|a\leq x \leq b\}$    closed interval
	- $(a,b)=\{x\in\mathbb{R}|a< x< b\}$   open interval
	- $[a,b)=\{x\in\mathbb{R}|a\leq x < b\}$    half-open intervals
	- $(a,b]=\{x\in\mathbb{R}|a < x \leq b\}$

