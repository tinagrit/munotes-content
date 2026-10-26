Lecture 9

## Views
A **view** is a *named* **virtual table** that is part of the schema and is accessible to any statement.

Views are similar to [[3_Subqueries#Common Table Expression|CTE]]'s `WITH`, but instead of being available for one statement, it stays permanently as part of the schema.

Views help **hide data and complexity** from users, and enforce **logical data independence** (see [[1_Database and DBMS#Relational Databases|Relational Databases]]).

### Creating a view
```sql
CREATE VIEW Adults AS
SELECT * FROM Users WHERE age >= 19;
```

This view *Adults* is a virtual table containing all adults.

### Dropping a view
```sql
DROP VIEW Adults;
```

### Using a view
Use the view as a table in any query.

```sql
SELECT AVG(age) FROM Adults;
```

[[1_Database and DBMS#DBMS|DBMS]] **do not store** the actual table produced by the view. It only stores the **definition** of the view. When we do a query like the above, the DBMS replaces the view name with:
```sql
SELECT AVG(age) FROM (
	SELECT * FROM Users WHERE age >= 19
) AS Adults;
```

> [!tip] Materialized views
> For a materialized view, DMBS store the **view content** as if it was a real table. It is recomputed every time the referred tables are updated.

Views can also be used in a [[6_Data Modification#Data Modification|data modification]] statement. For example:
```sql
DELETE FROM Adults;
```

This is translated to:
```sql
DELETE FROM Users WHERE age >= 19;
```

### Use case for INSTEAD OF
`INSTEAD OF` is a [[8_Triggers#Timing|timing trigger]] that allows the trigger's action to completely replace the triggering statement.

An example use case is this view:
```sql
CREATE VIEW AverageAge(age) AS SELECT AVG(age) FROM Users;
```

This view *AverageAge* looks like this:

| age |
| --- |
| 25  |

If we do modify from *AverageAge*, for example:
```sql
UPDATE AverageAge SET age = 20;
```

The [[1_Database and DBMS#DBMS|DBMS]] won't know how to change everyone's age so that the average age becomes 20.

We can create a trigger to make the update work:
```sql
CREATE TRIGGER AdjustAverageAge
INSTEAD OF UPDATE ON AverageAge
REFERENCING OLD ROW AS o,
			NEW ROW AS n
FOR EACH ROW
UPDATE Users SET age = age + (n.age - o.age);
```

Now, when the *AverageAge* value is updated directly, like the statement above, it adds the **difference** between the new average and the old average to everyone's age, effectively updating the average age.

