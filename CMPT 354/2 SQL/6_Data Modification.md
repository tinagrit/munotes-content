Lecture 8

## Data Modification
Apart from using the [[1_SQL Basics#Select-From-Where statement|Select-From-Where]] statement, SQL can also **modify** the data in the database.

### INSERT
The `INSERT` statement **adds a row** to the table. It takes the form:

```sql
INSERT INTO Users VALUE (123, 'Alpha', 20);
```

where the values inside the `()` are in the **order of the attributes**.  In this case, the table takes *Users* (uid, name, age).

SQL also allows the **result of a query** to use in the `INSERT` statement.

```sql
INSERT INTO Member (
	SELECT uid, 25 
	FROM Users
	WHERE uid NOT IN (
		SELECT uid
		FROM Member
		WHERE gid = 25
	)
)
```

This `SELECT` statement returns every user who's not already in group 25. The `INSERT` statement adds these users to the group 25.

### DELETE
The `DELETE` statement **deletes rows** from the table.

If we simply put the table name, it deletes **every row** from the table.
```sql
DELETE FROM Members;
```

If we want to delete **specific rows**, we need to specify the `WHERE` condition.

For example,
```sql
DELETE FROM Members WHERE uid=10 AND gid=25;
```

This statement removes the user 10 from the group 25.

```sql
DELETE FROM Members WHERE gid=25 AND uid IN (
	SELECT uid FROM Users WHERE age < 19
);
```

This statement removes everyone under 19 from group 25.

### UPDATE
The `UPDATE` statement **updates the values of rows** in the table. It takes the form:

```sql
UPDATE Users SET name = 'Amy' WHERE uid = 30;
```

The statement changes the name of user 30 to Amy.

If we use an [[4_Aggregation and Grouping#Aggregates|aggregate function]] to compute a value from the table, and we update many rows, the aggregate is computed **before the update** and is not recomputed after each row.

For example, if we do:
```sql
UPDATE Users SET popularity = (SELECT AVG(popularity) FROM Users);
```

This changes everyone's popularity to the average popularity **before the update**. 

