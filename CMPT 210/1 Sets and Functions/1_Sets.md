Lecture 1

## Sets
*Read more at* [MACM 101 > Sets and Subsets](https://munotes.tinagrit.com/MACM101/unit-3-set-theory/week-6-sets-and-subsets/sets-and-subsets.html)
- **unordered**, well-defined collection of objects (***elements***, *members of a set*)
- represented with a **capital** letter ($A$, $B$, $C$, $D$)
- elements represented with a **lowercase** letter ($a$, $b$, $c$, $d$)

For example, given a set $A=\left\{ a,b,c,d,e,f \right\}$
- The **elements** of $A$ include: $a$, $b$, $c$, $d$, $e$, and $f$
- Each element is a **member** of $A$. For example, $a \in A$ but $g \not\in A$
	- $\in$: *is an element of*
- The **cardinality** of $A$ is the number of elements (size). $\lvert A \rvert=6$

### Set builder notation
A set can be written as:
- a **list of elements**, such as $\left\{ a,b,c,d \right\}$, $\left\{ 5,6,7 \right\}$, $\left\{ 1,2,3,\dots,15 \right\}$
- a **rule for its elements**, such as $\left\{ x \mid x \text{ is an integer in }[5,10] \right\}$

### Finiteness
A set can be:
- **finite**, the cardinality is not infinite, such as $\left\{ 1,2,3 \right\}$, $\left\{ x \mid x>0, x\leq 10, x \text{ is even}\right\}$
- **infinite**, the cardinality is infinite, such as $\left\{ 1,2,3,\dots \right\}$, $\left\{ x \mid x>0, x \text{ is even} \right\}$

### Empty set
- an empty set or a *null set*
- contains **no (0) elements**
- denoted by $\varnothing$ or $\{\}$
- The cardinality $\lvert \varnothing \rvert=0$


---
## Common sets

- $\mathbb{Z}$  = the set of **integers**
	- $\mathbb{N}$  = the set of *non-negative* integers or natural numbers
	- $\mathbb{Z}^+$  = the set of *positive* integers (zero not included)
- $\mathbb{Q}$  = the set of **rational** numbers ($\frac{a}{b}$ where $a,b$ is integer and $b \neq 0$)
- $\mathbb{R}$  = the set of **real** numbers
- $\mathbb{C}$  = the set of **complex** numbers

For real numbers $a,b$ with $a<b$, 
- $[a,b]=\{x\in\mathbb{R}|a\leq x \leq b\}$    closed interval
- $(a,b)=\{x\in\mathbb{R}|a< x< b\}$   open interval
- $[a,b)=\{x\in\mathbb{R}|a\leq x < b\}$    half-open intervals
- $(a,b]=\{x\in\mathbb{R}|a < x \leq b\}$


---
## Subsets

$A$ is a **subset** ($\subseteq$) of $B$ *if and only if* every element of $A$ is an element of $B$

![[chart01.png|200]]

Note that if $A \equiv B$, every element of $A$ is still in $B$, and therefore $A$ would still be a subset of $B$.

$C$ is a **proper subset** ($\subset$) of $D$ *if and only if* $C \subseteq D$ and $C \neq D$.

In general,
- $C\subset D \implies C \subseteq D$
- $C\subseteq D \centernot\implies C\subset D$

With common sets
- $\mathbb{Z} \subset \mathbb{Q}$
- $\mathbb{Q} \subset \mathbb{R}$
- $\mathbb{R} \subset \mathbb{C}$


> Consider:
> $A=\{1,3,5,7,9\}$
> $B=\{1,3,5,7,9\}$

- $A\subseteq B$  but  $A \not \subset B$


> Consider:
> $A=\{1,3,5,7,9\}$
> $C=\{1,3,5,7,9,11,13,15\}$

- $A\subseteq C$  and  $A \subset C$


### Power set
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

In general, for any finite set $A$ with $|A| = n \geq 0$,
- $A$ has $2^n$ subsets
- $|P(A)| = 2^n$


---
## Set operations
*Read more at* [MACM 101 > Operations of Set](https://munotes.tinagrit.com/MACM101/unit-3-set-theory/week-8-operations-of-set/1_operations-of-set.html)

The **union** ($A \cup B$) of $A$ and $B$ consists of elements in $A$ **OR** $B$ (both sets)
- $\{x\mid x\in A \lor x\in B\}$
- Consider $A=\left\{ 1,2,3 \right\}$, $B=\left\{ 3,4,5 \right\}$, then $A \cup B = \left\{ 1,2,3,4,5 \right\}$

![[chart02.png|300]]

The **intersection** ($A \cap B$) of $A$ and $B$ consists of elements in $A$ **AND** $B$ (what they share)
- $\{x\vert x\in A \land x\in B\}$
- Consider $A=\left\{ 1,2,3 \right\}$, $B=\left\{ 3,4,5 \right\}$, then $A \cap B = \left\{ 3 \right\}$
- $C$ and $D$ are **disjoint** if $C \cap D = \varnothing$ (nothing shares)

![[chart03.png|300]]

The **set difference** ($A \backslash B$) of $A$ and $B$ consists of elements in $A$ **but not in** $B$
- $\{x\vert x\in A \land x\not\in B\}$
- Consider $A=\left\{ 1,2,3 \right\}$, $B=\left\{ 3,4,5 \right\}$, then $A \backslash B = \left\{ 1,2 \right\}$

![[chart04.png|300]]


The **symmetric difference** ($A \Delta B$) consists of all elements in either $A$ or $B$, but not in both (in the $\cup$ but not in $\cap$)
- $\{x\vert x\in A\cup B \land x\not\in A\cap B\}$ 
- Consider $A=\left\{ 1,2,3 \right\}$, $B=\left\{ 3,4,5 \right\}$, then $A \Delta B = \left\{ 1,2,4,5 \right\}$

![[chart06.png|300]]

The **complement** ($\overline A$ or $U-A$) consists of all elements in the **universe** that is **not in** $A$ (everything else)
- $\{x|x\in U \land x \not \in A\}$
- Consider $U=\mathbb{N}$, $A=\left\{ 1,2,3 \right\}$, then $\overline A=\left\{ 0,4,5,6,7,\dots \right\}$

![[chart05.png|300]]


---
## Cartesian product
*Read more at* [MACM 101 > Relations](https://munotes.tinagrit.com/MACM101/unit-5-functions-and-relations/week-11-functions/1_relations.html)

For sets $A,B \in U$, the **Cartesian product**, or cross product of $A$ and $B$ 
- is denoted by $A\times B$ 
- equals $\{(a,b)\mid a\in A, b\in B\}$

Take the elements of $A$ and pair them with elements of $B$

**Order matters.** $A\times B \not = B \times A$.


> Consider $A=\{2,3,4\}$ and $B=\{4,5\}$
- $A\times B=\{ (2,4),(2,5),(3,4),(3,5),(4,4),(4,5) \}$
- $B \times A=\{(4,2),(4,3),(4,4),(5,2),(5,3),(5,4)\}$
- $B\times B=B^2=\{ (4,4),(4,5),(5,4),(5,5) \}$


---
## Distributive law
*Read more at* [MACM 101 > The Laws of Set Theory](https://munotes.tinagrit.com/MACM101/unit-3-set-theory/week-8-operations-of-set/2_the-laws-of-set-theory.html)

For sets $A,B,C$
- $A\cup (B \cap C) = (A\cup B)\cap(A \cup C)$
- $A\cap (B \cup C) = (A\cap B)\cup(A \cap C)$

### Proof

> Let $z \in A\cap (B \cup C)$. Show that $z \in (A\cap B)\cup(A \cap C)$
> $$z \in A\cap (B \cup C) \iff z \in (A\cap B)\cup(A \cap C)$$

 $z \in A\cap (B \cup C)$
- $\implies z\in A$ `and` $z \in (B \cup C)$
- $\implies z \in A$ `and` $( z \in B$ `or` $z \in C)$
- $\implies (z\in A$ `and` $z \in B)$ `or` $(z\in A$ `and` $z \in C)$ by the distributivity of `and` and `or`
- $\implies z \in (A\cap B)\cup(A \cap C)$

