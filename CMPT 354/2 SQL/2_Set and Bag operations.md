Lecture 7

## Bag Semantics
While the [[2_Relational Data Model#Relational Data Model|relational model]] and [[3_Relational Algebra#Relational Algebra|algebra]] use **set semantics** (no duplicates), SQL uses **bag semantics** by default. This improves efficiency since it saves time of eliminating duplicates.

Bag semantics **allow duplicates**. If we simply do:
```sql
SELECT age FROM User;
```
We may get many entries of `19`, `19`, `19`, `20`, `20`, ...

This is why the SQL statement is different from:
$$
\pi_{age}User
$$
which would return only *unique* entires.

### DISTINCT
SQL provides the option to use *set semantics* and remove duplicates from the results using the `DISTINCT` keyword **after** `SELECT`.

For example, selecting all *unique* age, equivalent to $\pi_{age}User$:
```sql
SELECT DISTINCT age FROM User;
```

### Set operations
Using set semantics (no duplicates), SQL supports
- `UNION`: $A\cup B$
- `EXCEPT`: $A-B$
- `INTERSECT`: $A\cap B$

When using set semantics, the $A$ and $B$ tables will have their **duplicates removed** *before and after* the operation.

For example, we may do:
```sql
(SELECT fruit FROM Bag1)
UNION
(SELECT fruit FROM Bag2);
```
This will return the *unique* fruits that appear in either Bag1, Bag2, or both. 

![[chart22.png|400]]

### Bag operations
Using bag semantics (allowed duplicates). Each row has a **count** (how many times it appears in the table). SQL supports
- `UNION ALL`: sum the counts from two tables
- `EXCEPT ALL`: subtract the two counts
- `INTERSECT ALL`: minimum of the two counts

For example, we may do:
```sql
(SELECT fruit FROM Bag1)
UNION ALL
(SELECT fruit FROM Bag2);
```
This will return the all rows of fruits that appear in either Bag1, Bag2, or both. 

![[chart23.png|400]]

Here:
- The table Bag1 has 3 apples and 1 orange
- The table Bag2 has 1 apple and 2 oranges

When we do:
- `UNION ALL`, we take the total count: $3+1=4$ apples and $1+2=3$ oranges
- `EXCEPT ALL`, we take the subtraction $3-1=2$ apples and $1-2$ (ignore negative) $=0$ oranges
- `INTERSECT ALL`, we take the minimum $\min (3,1)=1$ apple and $\min(1,2)=1$ orange

