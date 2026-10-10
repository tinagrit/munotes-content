Lecture 6

## Functional dependencies
A function dependency (***FD***) has the form:
$$
X\to Y
$$
where $X$ and $Y$ are [[4_ER Model#Entities and Attributes|attributes]] in a relation $R$.

$X$ **functionally determines** $Y$ if:
$$
t_{1}[X]=t_{2}[X] \implies t_{1}[Y]=t_{2}[Y]
$$
for any tuples $t_{1}$, $t_{2}$ in $R$.

For example, in this [[2_Relational Data Model#Relational Data Model|relation]]:
![[chart19.png|400]]
All fields with the *uid* of *1* have the *username* of *Alpha*. Therefore *uid* **functionally determines** *username*.

When we define a [[2_Relational Data Model#Keys|key]] for the relation $R$, we want:
- $K\to$ all other attributes of $R$
- No proper subset of $K$ satisfies the above condition

### Trivial FD
A functional dependency is **trivial** if:
$$
\text{RHS} \subseteq \text{LHS}
$$
For example, we can say $\text{uid},\text{username}\to \text{uid}$.

A non-trivial FD *might not* be completely non-trivial. An FD is **completely non-trivial** if:
$$
\text{RHS}\cap \text{LHS} = \emptyset
$$

### Attribute closure
The **closure of** $Z$ (denoted $Z^{+}$) is the set of **all attributes** $A_{1},A_{2},\dots$ **functionally determined** by $Z$
$$
Z\to A_{1}A_{2}\dots
$$

To compute the closure,
- start with closure $= Z$
- for each functional dependency $X\to Y$, if $X$ is already in the closure, also add $Y$ to the closure

### Rules of FD
The *Armstrong's axioms* include:
1. **Reflexivity**: if $Y \subseteq X$, then $X\to Y$
2. **Augmentation**: if $X\to Y$, then $XZ\to YZ$ for any $Z$
3. **Transitivity**: if $X\to Y$ and $Y\to Z$, then $X\to Z$

Rules derived from axioms include:
1. **Splitting**: if $X\to YZ$, then $X\to Y$ and $X\to Z$
2. **Combining**: if $X\to Y$ and $X\to Z$, then $X\to YZ$

### Proving a rule by Chase
For example, if we have a list of dependencies:
$$
D=\{ A\to B, B\to C \}
$$
and we need to prove: **Does** $A\to C$ **follow from** $D$ **?**

This is true due to [[#Rules of FD|Transitivity]], but we will prove it by Chase.

We start with the **if-part** of the claim. In $A\to C$, the if-part is: "*If two rows have the same* $A$ *value*". We create a table with the same $A$ but different $B$ and $C$:

| $A$ | $B$     | $C$     |
| --- | ------- | ------- |
| $a$ | $b_{1}$ | $c_{1}$ |
| $a$ | $b_{2}$ | $c_{2}$ |

Then, we **apply the given dependencies** in $D$. For $A\to B$, it means for rows with the same $A$, they must have the same $B$. We modify the table:

| $A$ | $B$     | $C$     |
| --- | ------- | ------- |
| $a$ | $b_{1}$ | $c_{1}$ |
| $a$ | $b_{1}$ | $c_{2}$ |

For $B\to C$, it means for rows with the same $B$, they must have the same $C$. We modify the table:

| $A$ | $B$     | $C$     |
| --- | ------- | ------- |
| $a$ | $b_{1}$ | $c_{1}$ |
| $a$ | $b_{1}$ | $c_{1}$ |

Then, we **check the then-part** of the claim. In $A\to C$, the then-part is: "*they must have the same* $C$", which it does now in the table.

$A\to B$, $B\to C$  $\implies A\to C$ is proven by Chase.


---
## Multivalued dependencies

A multivalued dependencies (***MVD***) has the form:
$$
X\twoheadrightarrow  Y
$$
where $X$ and $Y$ are [[4_ER Model#Entities and Attributes|attributes]] in a relation $R$.

If $X\twoheadrightarrow Y$, the same $X$ can have many $Y$s, but if they appear with different $Z$ values, **all cross combinations** must exist.

Whenever two rows in $R$ agree on all attributes of $X$, we can swap their $Y$ components and get rows that are also in $R$.

For example, in this relation, hobbies and languages are completely unrelated.
![[chart21.png|350]]
Suppose that $\text{name}\twoheadrightarrow \text{hobby}$. 

Finding two rows in $R$ that have the same $X$ (name):
- (Alice, Tennis, English)
- (Alice, Soccer, French)

Swap their $Y$ (happy):
- (Alice, Soccer, English)
- (Alice, Tennis, French)

These swapped rows **do exist** in the relation.

### Trivial MVD
A multivalued dependency is **trivial** if:
$$
\text{RHS} \subseteq \text{LHS}
$$
or
$$
\text{RHS} \cup \text{LHS}=\text{all attributes of }R
$$

### Rules of MVD
1. **Complementation**: if $X\twoheadrightarrow Y$, then $X\twoheadrightarrow attrs(R)-X-Y$
2. **Augmentation**: if $X\twoheadrightarrow Y$ and $V\subseteq W$, then $XW\twoheadrightarrow YV$
3. **Transitivity**: if $X\twoheadrightarrow Y$ and $Y\twoheadrightarrow Z$, then $X\twoheadrightarrow Z-Y$
4. **Replication**: if $X\to Y$, then $X\twoheadrightarrow Y$
5. **Coalescence**: if $X\twoheadrightarrow Y$ and $Z\subseteq Y$ and there is some $W$ disjoint from $Y$ such that $W\to Z$, then $X\to Z$


---
## Decomposition
A relation can be **decomposed** to eliminate redundancy. [[3_Relational Algebra#Join|Joining]] should return the original relation.

![[chart20.png|450]]

A decomposition can be **unnecessary** (no redundancy is lost) or **bad** (some association is lost, joining would return more rows than the original). 

### Lossless join decomposition
If we decompose a relation $R$ into relations $S$ and $T$, we need:
- $attrs(R)=attrs(S)\cup attrs(T)$
- $S=\pi_{attrs(S)}(R)$
- $T=\pi_{attrs(T)}(R)$

where $attrs(X)$ is the attributes of $X$.

The decomposition is **lossless join decomposition** if we can guarantee that 
$$R=S\bowtie T$$

>[!tip] Note
>Any decomposition gives $R\subseteq S\bowtie T$ because a lossy decomposition is one with $R \subset S\bowtie T$.

### Boyce-Codd Normal Form
A relation $R$ is in **BCNF** if for **every non-trivial FD** $X\to Y$ in $R$, $X$ is a super key.

Decompose when a relation is not in BCNF. To decompose:
1. Find a **BCNF Violation**: a non-trivial FD $X\to Y$ in $R$ where $X$ is **not** a super key
2. **Decompose** $R$ into $R_{1}$ and $R_{2}$ where
	- $R_{1}$ has attributes $X\cup Y$
	- $R_{2}$ has attributes $X\cup Z$ where $Z$ contains all attributes of $R$ that are neither in $X$ nor $Y$
3. Repeat until all relations are in BCNF

This process of decomposition is **guaranteed** to be **lossless**.
BCNF **does not** guarantee no redundancy. 

### Fourth Normal Form
A relation $R$ is in **4NF** if for **every non-trivial MVD** $X\twoheadrightarrow Y$ in $R$, $X$ is a super key.

4NF is **stronger** than BCNF because every FD is also an MVD.

Decompose when a relation is not in 4NF. To decompose:
1. Find a **4NF Violation**: a non-trivial MVD $X\twoheadrightarrow Y$ where $X$ is **not** a super key
2. **Decompose** $R$ into $R_{1}$ and $R_{2}$ where
	- $R_{1}$ has attributes $X\cup Y$
	- $R_{2}$ has attributes $X\cup Z$ where $Z$ contains all attributes of $R$ that are neither in $X$ nor $Y$
3. Repeat until all relations are in 4NF

This process of decomposition is **guaranteed** to be **lossless**.
4NF **does not** guarantee no redundancy, but removes redundancies caused by MVD.

### Other normal form - Third Normal Form
A relation $R$ with FDs $F$ is in **3NF** if for **all** $X\to Y$ **in** $F^{+}$, then $Y\subseteq X$, or $X$ is a super key of $R$, or $Y$ is part of some key for $R$.

3NF is weaker than both BCNF and 4NF, is used when BCNF is not achievable.

