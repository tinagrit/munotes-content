Lectures 7-8

## Table Subqueries
We can use a **result of a query**, wrapped in brackets $(\cdot)$, **as a table** for further use in the [[1_SQL Basics#Select-From-Where statement|FROM]] clause or in a [[2_Set and Bag operations|set and bag operation]].

For example, we can do:
```sql
SELECT name
FROM Users u,
	(SELECT uid, gid FROM Member) m
WHERE u.uid = m.uid;
```

The `(SELECT uid, gid FROM Member)` acts as a **table subquery**, and the outer query treats this as a table that we named `m`.

### Common Table Expression
The **CTE** (*Common Table Expression*) is the `WITH` clause in SQL. It allows us to define a temporary table that we can reference to in the actual query.

It has the form:
```sql
WITH table1(col1, col2, ...) AS (subquery),
	 table2(col1, col2, ...) AS (subquery)
SELECT ... FROM ..., table1, table2 WHERE ...
```

For example, using the same query from above, we can rewrite it using `WITH`:
```sql
WITH m(uid, gid) AS (SELECT uid, gid FROM Member)
SELECT name
FROM Users u, m
WHERE u.uid = m.uid;
```


---
## Scalar Subqueries
If a query returns **a single row**, this subquery can be **used as a value**.

For example, we can do:
```sql
SELECT * 
FROM Users 
WHERE age = (SELECT age FROM Users WHERE name = 'Alpha');
```

This query selects users who have the same age as Alpha.

This *will fail* if the query returns more than one row, or no rows.


---
## IN Subqueries
Similar to scalar subqueries, but will work for a query that returns **many rows**. It will match if the value is in the result of the subquery.

For example, we can do:
```sql
SELECT * 
FROM Users
WHERE age IN(SELECT age FROM Users WHERE nationality = 'Thai');
```

This query selects users with the same age as anyone with Thai nationality.


---
## EXISTS Subqueries
`EXISTS(⋅)` returns a boolean value **True** if the subquery has at least 1 row, or **False** if the subquery is empty.

For example, we can do:
```sql
SELECT * 
FROM Users
WHERE EXISTS(SELECT * FROM Users WHERE age = 50);
```

This query returns every users if there exists at least one user with age $50$.

### Correlated Subquery
The WHERE condition inside of the `EXISTS(⋅)` can relate to the table outside of it.

In this example:
```sql
SELECT * 
FROM Users u_out
WHERE EXISTS(
	SELECT * FROM Users u_in
	WHERE u_in.name = 'Alpha'
	AND u_in.age = u_out.age
);
```

This query returns users who have the same age as Alpha.

For each row in `u_out`, find a row in `u_in` that has the same age and is named Alpha. If such row exists in `u_in`, that row in `u_out` is added to the result.


---
## Quantified Subqueries
SQL supports **Universal quantification** (*for all*) and **Existential quantification** (*for some*) in the WHERE condition.

- **Universal**: `ALL(⋅)` will return **True** *if and only if* it is true for all of the results in the subquery
- **Existential**: `ANY(⋅)` or `SOME(⋅)` will return **True** *if* any result is true in the subquery

For example, we can do:
```sql
SELECT * 
FROM Users 
WHERE age >= ALL(SELECT age FROM Users);
```

This returns the user(s) with the highest age.