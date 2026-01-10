Lecture 1 & 2

## Functions
*Read more at* [MACM 101 > Functions](https://munotes.tinagrit.com/MACM101/unit-5-functions-and-relations/week-11-functions/2_functions.html)

For [[1_Sets#Sets|sets]] $A$, $B$, the function or mapping $f:A\to B$,
- $A$ is called the **domain** of $f$
- $B$ is called the **codomain** of $f$

All elements of $A$ has to **point to somewhere** in $B$ at most once
- Two or more different elements of the codomain cannot be assigned to the same domain
- Passes the vertical line test
- If $f(a)=1$ and $f(a)=2$, then $f$ is not a function

For example, $f:\mathbb{R} \rightarrow \mathbb{R}$ such that $f(x)=x^{2}$
![[Screenshot 2026-01-08 at 9.29.45 PM.png|200]]
- This function passes the vertical line test
- Draw a vertical line and slide it along the x-axis, nowhere in the graph that the vertical line touches the function more than once

![[chart07rc.png|600]]

When $a \in A$, $b \in B$, $f(a)=b$,
- "Function $f$ maps $a$ to $b$"
- $b$ is the **value** of $f$ at **argument** $a$
- $b$ is the **image** of $a$
- $a$ is the **preimage** of $b$


### Set arguments
For a function $f:A\to B$, we can "plug in" $S \subseteq A$
- The value at argument $S$ is $\left\{ f(s) \mid s \in S \right\}$ 
- For example, for $f(x)=x^{2}$ and $S=\left\{ 1,2,3,4 \right\}$
- Then $f(S)=\left\{ 1,4,9,16 \right\}$


### Partial functions
- A **total function** assigns **all elements** in the domain to any codomain
- A **partial function** does not

![[chart08.png|420]]


### Range
For $f:A\to B$, all $f(A)$ is the **range** of $f$
- All possible values produced from $f$ as part of the *codomain*
- A **subset** of the codomain
- $f$ is a **total function** if $\text{range}=\text{codomain}$

> Consider $f:\mathbb{R} \to \mathbb{R}$ such that $f(x)=x^{2}$
- The domain is $\mathbb{R}$
- The codomain is $\mathbb{R}$
- The **range** is $\mathbb{R}_{\geq 0}$

> Consider $f:\mathbb{N} \to \mathbb{R}$ such that $f(x)=x^{2}$
- The domain is $\mathbb{N}$
- The codomain is $\mathbb{R}$
- The **range** is $\left\{ 0,1,4,9,\dots \right\}$


---
## Types of functions

### Surjective
A function is surjective (or **onto**) *if and only if*:
- for every codomain value $b \in B$
- there is **at least one** domain value $a \in A$ assigned to

This means that:
- $\text{range}=\text{codomain}$
- Domain $|A|$ is larger than or equal to the codomain $|B|$

![[chart09.png|500]]


### Injective
A function is *injective* (or **one-to-one**) *if and only if*:
- for every codomain value $b \in B$
- there is **at most one** domain value $a \in A$ assigned to

This means that:
- $f(x)=f(y) \implies x=y$
- Domain $|A|$ is less than or equal to the codomain $|B|$

![[chart10.png|500]]

### Bijective
A function is *bijective* if it is both **surjective and injective**

This means that domain $|A|$ is **equal to** the codomain $|B|$

![[chart11.png|275]]
