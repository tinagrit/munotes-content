Lecture 7

## Aggregates
SQL supports these aggregate functions over a column:
- `COUNT(⋅)`
- `SUM(⋅)`
- `AVG(⋅)`
- `MIN(⋅)`
- `MAX(⋅)`

For example, this returns the number of users and their average age
```sql
SELECT COUNT(uid), AVG(age) 
FROM Users;
```

> [!tip] By default, if no `GROUP BY` is used, everything is aggregated as one group.

### Using DISTINCT
We can use the [[2_Set and Bag operations#Bag Semantics|distinct for set semantics]] directly in the aggregate function. 

For example, if we want to count unique names, these two queries are identical:

```sql
SELECT COUNT(DISTINCT name) 
FROM Users;
```

```sql
SELECT COUNT(name)
FROM (SELECT DISTINCT name FROM Users);
```


## Grouping
After doing [[1_SQL Basics#Select-From-Where statement|Select-From-Where]], we can **group results** that have the same attribute. For example, grouping people with the same age.

`GROUP BY column_name` is placed after Select-From-Where.

For each group, we need to use one of the [[#Aggregates|aggregate functions]] to show results based on the whole group. There can only be **one row per group**.

For example, we can do:
```sql
SELECT age, COUNT(age) 
FROM Users 
GROUP BY age;
```
This returns the number of people of each age.

### HAVING condition
`HAVING` is similar to `WHERE`, it filters the results using a condition, but it is done **after grouping** instead of before.

For example, in the query above, we can filter results with only ages with $\geq 100$ people:
```sql
SELECT age, COUNT(age)
FROM Users
GROUP BY age
HAVING COUNT(age) >= 100;
```

The aggregate `COUNT(age)` would not have been available during the `WHERE` step, since `WHERE` filters the table *before* the grouping.

### Evaluation steps
When SQL evaluates a query with `SELECT .. FROM .. WHERE .. GROUP BY .. HAVING`, it follows these steps:
1. Compute `FROM` ($\times$, [[3_Relational Algebra#Cross Product|cross product]])
2. Compute `WHERE` ($\sigma$, [[3_Relational Algebra#Selection|selection]])
3. Compute `GROUP BY`
4. Compute `HAVING` ($\sigma$ over the groups)
5. Compute `SELECT` ($\pi$, [[3_Relational Algebra#Projection|projection]])


## Ordering
Once we get the result, SQL supports **sorting** those results. At the end of the query, we can put 
- `ORDER BY column_name ASC` for **ascending**
- `ORDER BY column_name DESC` for **descending**

SQL computes the sorting at **the very end**, after projecting on `SELECT`. Therefore, only **output columns** (those in `SELECT`) can be sorted.

For example, using the query from above, this will sort the results by age:
```sql
SELECT age, COUNT(age)
FROM Users
GROUP BY age
HAVING COUNT(age) >= 100
ORDER BY age ASC;
```

### LIMIT
We can place an **upper limit** on how many rows to output. For example, if we sort descending and limiting the output to 1, we will get the most popular age:

```sql
SELECT age, COUNT(age)
FROM Users
GROUP BY age
ORDER BY age DESC
LIMIT 1;
```

