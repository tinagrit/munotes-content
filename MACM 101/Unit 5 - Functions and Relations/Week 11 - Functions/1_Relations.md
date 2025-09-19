Section 5.1

## Cartesian product

For [[Sets and Subsets#Sets|sets]] $A,B \in U$, the **Cartesian product**, or cross product of $A$ and $B$ 
- is denoted by $A\times B$ 
- equals $\{(a,b)\mid a\in A, b\in B\}$

Take the elements of $A$ and pair them with elements of $B$

We say that the elements of $A\times B$ are **ordered pairs**
Notice: $|A\times B|= |B\times A| = |A| \cdot |B|$

But, in general, $A\times B \not = B \times A$.

We can extend the operator to $n$ sets:
$A_1 \times A_2 \times \ldots \times A_n = \{ (a_1,a_2,\ldots,a_n) \mid a_i \in A_i,1\leq i \leq n \}$

**Order matters**.

### Example

> Let $A=\{2,3,4\}$ and $B=\{4,5\}$

- $A\times B=\{ (2,4),(2,5),(3,4),(3,5),(4,4),(4,5) \}$
- $B \times A=\{(4,2),(4,3),(4,4),(5,2),(5,3),(5,4)\}$
- $B\times B=B^2=\{ (4,4),(4,5),(5,4),(5,5) \}$

> Consider the set $R\times R=\{(x,y)\mid x,y\in R \}$

This is the 2D plane of geometry.


## Relations

### Binary relations

For sets $A,B \in U$, a **binary relation** from $A$ to $B$
- is any subset of $A\times B$

A **binary relation** on $A$
- is any subset of $A\times A$

> Let $A=\{2,3,4\}$ and $B=\{4,5\}$.
> The following are some relations from $A$ to $B$

- $\varnothing$
- $\{(2,4)\}$
- $\{(2,4),(2,5)\}$
- $\{(2,4),(2,5),(3,4)\}$
- $A\times B$

In general, for finite sets $A,B$ with $|A|=m$ and $|B|=n$,
- The number of relations is $2^{|A\times B|}$ (See [[Sets and Subsets#Power set|power sets]])
- there are $2^{mn}$ relations from $A$ to $B$ including:
	- the empty relation
	- the relation $A\times B$ itself
- there are also $2^{mn}$ relations from $B$ to $A$
	- since $|A\times B|=|B\times A|$
	- any relation $R_1$ from $B$ to $A$ can be obtained from a unique relation $R_2$ from $A$ to $B$ by reversing the components of each ordered pair in $R_2$


### Example

> Let $T$ be the subset of $N\times N$ where $T=\{(m,n)\mid n=7m\}$.
> Examples of elements of $T$:

$(0,0),(1,7),(2,14),(11,77)$ 

$(1,1)$ is not in the set $T$ but is a cross-product of $N\times N$

> Define the relation $T$ recursively

- $(0,0)\in T$
- If $(s,t)\in T$ then $(s+1,t+7)\in T$


> Prove that for any set $A$,
> $A\times \varnothing=\varnothing$

**Prove by contradiction**
Suppose $A\times \varnothing \not = \varnothing$

Let $(a,b)\in A\times \varnothing$
Then $a \in A$ and $b \in \varnothing$, a contradiction

Therefore, the original conclusion, that $A\times \varnothing=\varnothing$ is true.


### Theorem

For any set $A,B,C \subseteq U$:
- **a)** $A\times (B\cap C)=(A\times B)\cap (A\times C)$
- **b)** $A\times(B\cup C)=(A\times B) \cup (A\times C)$
- **c)** $(A \cap B) \times C=(A\times C)\cap (B\times C)$
- **d)** $(A\cup B)\times C=(A\times C)\cup(B\times C)$

#### Proof of theorem (a)

For all $a,b\in U$,
- $(a,b)\in A\times (B \cap C) \iff (a \in A) \land (b \in B \cap C)$
	- $\iff (a\in A) \land (b\in B \land b \in C)$
	- $\iff (a \in A \land b \in B) \land (a \in A \land b \in C)$
	- $\iff ((a,b)\in A\times B) \land ((a,b) \in A\times C)$
	- $\iff (a,b)\in (A\times B)\cap (A\times C)$
