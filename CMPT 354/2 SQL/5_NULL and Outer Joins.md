Lecture 8

## The NULL
Sometimes, our tables may include a value that is **not applicable** or **unknown** to the row. For example, a free user will not have their credit card enrolled.

Out of many solutions, SQL chooses to use `NULL` as a **special value**.
- Operating ($+$, $-$, etc) on `NULL` and another value will return `NULL`
- Except for `COUNT(⋅)`, [[4_Aggregation and Grouping#Aggregates|Aggregate functions]] ignore `NULL` values
- Except for `COUNT(⋅)`, [[4_Aggregation and Grouping#Aggregates|Aggregate functions]] on empty groups return `NULL`

### Comparing with NULL
If we compare a value with `NULL` using $=$, $>$, etc, it will return **Unknown** instead of being **True** or **False**.

> [!tip] `NULL = NULL` will still return **Unknown**, not **True**.

SQL has a special predicate to tell if a value is null: `IS NULL` and `IS NOT NULL`.

For example, to return all users with no credit card enrolled:
```sql
SELECT * FROM Users WHERE credit_card IS NULL;
```

### COALESCE
This is a built-in SQL function for handling `NULL`s.

`COALESCE(⋅)` accepts any amount of arguments, and will return the **first value that is not null**. We can use this to provide a default/fallback value to avoid `NULL`.

For example, if we use this query to return the max age:
```sql
SELECT MAX(age)
FROM Users
```

If the table Users was **empty**, this would return `NULL`. If we want the fallback value to be something else, for example 0, we can use `COALESCE(⋅)`:
```sql
SELECT COALESCE(MAX(age), 0)
FROM Users
```

In `COALESCE(MAX(age), 0)`, if the first argument `MAX(age)` happens to be `NULL`, then it would return the next element `0` that is not `NULL`.

### NULLIF
This is a counterpart of `COALESCE(⋅)`.

`NULLIF(⋅)` accepts 2 arguments and returns `NULL` if **they are equal**. If we have default/fallback values in the table, we can convert them back to `NULL`.

For example: `NULLIF(name, 'N/A')` will return `NULL` if the name attribute is "N/A".


---
## Outer Join
Normally, when we do a [[3_Relational Algebra#Join|join]], it is an **inner join**. Inner joins only output rows that **exist on both tables**.

For example, this query shows the usernames and the group the user is a member of.
```sql
SELECT *
FROM Users u, Member m
WHERE u.uid = m.uid;
```

If there are users that are **not in any group**, or if a user has a membership, but **not listed in Users**, they won't appear here, since the `uid` must exist in both tables, as assigned in `WHERE`.

A user that is not in any group is a **dangling Users row** since it does not join with any Member rows.
A membership not listed in Users is a **dangling Member row** since it does not join with any Users rows.

**Outer joins** allow joining with missing information marked as `NULL`. There are 3 types of outer joins:
- **Full outer join** $R \text{ ⟗ } S$: includes all rows in $R\bowtie S$, and *dangling* $R$ rows, and *dangling* $S$ rows
- **Left outer join** $R \text{ ⟕ } S$: includes all rows in $R\bowtie S$, and *dangling* $R$ rows
- **Right outer join** $R \text{ ⟖ } S$: includes all rows in $R\bowtie S$, and *dangling* $S$ rows

In SQL, we can write:
```sql
SELECT *
FROM Users 
FULL OUTER JOIN Member
ON Users.uid = Member.uid;
```
and likewise for `LEFT OUTER JOIN` and `RIGHT OUTER JOIN`.

The condition after `ON` is how to match rows from the two tables.

