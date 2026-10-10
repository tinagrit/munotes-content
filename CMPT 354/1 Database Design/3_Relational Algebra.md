Lecture 3

## Relational Algebra
Language for querying [[2_Relational Data Model#Relational Data Model|relational data]] based on **operators**.

Every **safe relational calculus** (set builder notation) is expressible as a relational algebra query.

Core operators include:
- [[#Selection|Selection]]
- [[#Projection|Projection]]
- [[#Cross Product|Cross Product]]
- [[#Union|Union]]
- [[#Difference|Difference]] (the only non-[[#Monotonicity|monotonic]] operator)
- [[#Renaming|Renaming]]

Additional derived operators include:
- [[#Join|Join]]
- [[#Natural join|Natural join]]
- [[#Intersection|Intersection]]

Relational algebra is limited by it having **no recursion**, so it is not as powerful as general-purpose languages (not Turing-complete). 

### Selection
$$
\sigma_{p}R
$$
- Input: A table $R$  and a selection condition (predicate) $p$
- Purpose: **filter** rows according to the condition
- Output: same columns as $R$, only with rows satisfying $p$

The selection condition $p$ can include any column of $R$, constants, comparison ($=$, $\leq$, etc) and Boolean connectives ($\land$, $\lor$, $\lnot$).

For example, we can select:
$$
\sigma_{pop\geq 0.9 \,\land\, (age<10\, \lor\, age>12)}User
$$

### Projection
$$
\pi_{L}R
$$
- Input: A table $R$ and a list of columns $L$
- Purpose: output chosen columns
- Output: same rows as $R$, only with columns in $L$

Projection removes duplicate output rows by definition.

For example, if the table $User$ contains $uid$, $name$, and $age$, we can do:
$$
\pi_{name,age}User
$$

Selection and Projection can be **composed**. For example, selecting names of users older than 19:
$$
\pi_{name}(\sigma_{age>19}User)
$$

### Cross Product
$$
R\times S
$$
- Input: two tables $R$ and $S$
- Purpose: pair rows from two tables
- Output: for each row $r$ in $R$ and $s$ in $S$, output row $rs$

The number of rows in result is $|R| \cdot |S|$. Schema compatibility is **not needed**.

Cross Product is **commutative**, for any $R$ and $S$, $R\times S = S \times R$.

### Join
$$
R\bowtie_{p}S
$$
- Input: two tables $R$ and $S$, and a selection condition $p$
- Purpose: relate rows from tow tables according to some criteria
- Output: for each row $r$ in $R$ and $s$ in $S$, output row $rs$ if $r$ and $s$ satisfy $p$

Joining $R\bowtie_{p}S$ is a shorthand for [[#Cross Product]] [[#Selection]] $\sigma_{p}(R\times S)$

For example, in the [[2_Relational Data Model#Relational Data Model|bank example]], we can join the two tables:
$$
Users\bowtie_{Users.branch=Branches.id}Branches
$$
This will add the branch location to each user.

### Natural join
$$
R \bowtie S
$$
- Input: two tables $R$ and $S$ containing **identically named column**(s)
- Purpose: relate rows from two tables and eliminate one copy of identically named columns
- Output: columns from both $R$ and $S$, [[#Join|joining]] identically named columns

Natural joining $R \bowtie S$ is a shorthand for [[#Join]] [[#Projection]] $\pi_{L}(R\bowtie_{p} S)$ where:
- $L$ is the union of column names from $R$ and $S$
- $p$ equates each pair of columns common to $R$ and $S$

### Union
$$
R\cup S
$$
- Input: two tables $R$ and $S$ with **identical schema**
- Output: same schema as $R$ and $S$ containing all rows of $R$ and all rows of $S$

Duplicate rows are removed after union by definition

### Difference
$$
R-S
$$
- Input: two tables $R$ and $S$ with **identical schema**
- Output: same schema as $R$ and $S$ containing **all rows of** $R$ **that are not in** $S$

### Intersection
$$
R\cap S
$$
- Input: two tables $R$ and $S$ with **identical schema**
- Output: same schema as $R$ and $S$ containing all rows in **both** $R$ **and** $S$ 

Intersection is a shorthand for [[#Difference]] $R-(R-S)$. It can also be written using [[#Natural join]] $R \bowtie S$.

### Renaming
$$
\rho_{S(A_{1},A_{2},\dots)}R
$$
- Input: A table $R$, a new table name $S$ (optional), and new column names $(A_{1},A_{2},\dots)$ (optional)
- Purpose: 
	- avoid confusion caused by identical column names but means different things
	- create identical column names to use in [[#Natural join]]

The renamed table is a **copy of the original**, it does not modify the database.


---
## Monotonicity
For an arbitrary operator $X$ that operates on $R$ and $S$, let $A$ be the result of this operation.
$$
R\,X\,S = A
$$

When we add **new rows** to $R$ and $S$, if our initial $A$ remains **"correct"** (new $A$ can have more rows but no rows from initial $A$ are removed), then the operator $X$ is **monotonic**.

The [[#Difference]] operator is **monotonic** with respect to $R$, but **non-monotonic** with respect to $S$. It is the only non-monotonic operator. 

