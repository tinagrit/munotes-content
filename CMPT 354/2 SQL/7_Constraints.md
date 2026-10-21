Lecture 8

## Constraints
The [[2_Relational Data Model#Data Model|data model]] requires **constraints** defined as part of the schema. It adds certain **restrictions** of allowable data on the database.

Constraints can prevent errors by enforcing data integrity, and can allow [[1_Database and DBMS#DBMS|DBMS]] to better optimize by knowing what data belongs here.

When we [[1_SQL Basics#Data-definition language|create a table]], there are 5 types of SQL constraints:
- [[#NOT NULL|NOT NULL]]
- [[#Key declaration|Key declaration]]
- [[#Referential integrity|Referential integrity]]
- [[#General assertion|General assertion]]
- [[#Tuple and attribute checks|Tuple and attribute checks]]

### NOT NULL
 We can put the keyword `NOT NULL` on an attribute to specify that this value cannot be [[5_NULL and Outer Joins#The NULL|NULL]].

For example,
```sql
CREATE TABLE Users (
	uid INTEGER NOT NULL,
	name VARCHAR(30) NOT NULL
);
```

This table strictly disallows uid and name to be `NULL`.

If we try to [[6_Data Modification#INSERT|insert]] `NULL` values, the `INSERT` statement will result in an error.

### Key declaration
We can specify a [[2_Relational Data Model#Keys|key]] to the table using the keyword `PRIMARY KEY`.

To specify **one attribute key**, we can put `PRIMARY KEY` on the attribute. For example,
```sql
CREATE TABLE Users (
	uid INTEGER NOT NULL PRIMARY KEY,
	name VARCHAR(30) NOT NULL
);
```

To specify **multiple attribute key**, we put all the key attributes in `PRIMARY KEY(⋅)` after declaring all the attributes. For example,
```sql
CREATE TABLE Member (
	uid INTEGER NOT NULL,
	gid INTEGER NOT NULL,
	PRIMARY KEY(uid, gid)
);
```

We can also add the `UNIQUE` keyword to specify that **no rows can share** the same value of this attribute. `NULL` values are all **distinct**. For example,
```sql
CREATE TABLE Users (
	uid INTEGER NOT NULL PRIMARY KEY,
	name VARCHAR(30) NOT NULL,
	email VARCHAR(30) UNIQUE
);
```

In this table, all users with an email must have unique emails. The value of email can be null.

### Referential integrity
If a value of an attribute is a **primary key of another table**, we can enforce a `REFERENCES` rule where the value cannot exist without existing in the primary key table.

For example, in the *Users*, *Member*, and *Groups* case, we should set:
- *Member*.uid to reference *Users*.uid so that **if a user does not exist** in *Users*, **it cannot join a group** in *Member*.
- *Member*.gid to reference *Groups*.gid so that **if a group does not exist** in *Groups*, **no one can join** it in *Member*.

```sql
CREATE TABLE Member (
    uid INTEGER NOT NULL REFERENCES Users(uid),
    gid INTEGER NOT NULL REFERENCES Groups(gid),
    PRIMARY KEY (uid, gid)
);
```

References can also be added below all the attribute declarations using the keyword `FOREIGN KEY`. This is equivalent to the above:
```sql
CREATE TABLE Member (
    uid INTEGER NOT NULL,
    gid INTEGER NOT NULL,
    PRIMARY KEY (uid, gid),

    FOREIGN KEY (uid) REFERENCES Users(uid),
    FOREIGN KEY (gid) REFERENCES Groups(gid)
);
```

If we [[6_Data Modification#DELETE|delete]] a row from the primary key table, we can also **automatically delete** rows referencing it. Use the keyword `ON DELETE CASCADE`. For example:
```sql
CREATE TABLE Member (
    uid INTEGER NOT NULL REFERENCES Users(uid) ON DELETE CASCADE,
    gid INTEGER NOT NULL REFERENCES Groups(gid) ON DELETE CASCADE,
    PRIMARY KEY (uid, gid)
);
```

In this table, rows that have the uid referencing a deleted user in *Users* will be automatically deleted. That is, if a user is deleted, it leaves all groups that it joined.

### General assertion
An **assertion** can be made to ensure all values follow the constraints. It takes the form:
```sql
CREATE ASSERTION name CHECK condition;
```

where name is the name of the assertion, and condition is a **boolean value**.

A *violation* is when the boolean returns **False**, which will cause a rejection.

### Tuple and attribute checks
We can also place `CHECK`s on a specific attribute when we declare it. This assertion is:
- only associated with a **single table**
- only checked on `INSERT` or `UPDATE`

For example,
```sql
CREATE TABLE Users (
	uid INTEGER NOT NULL PRIMARY KEY,
	name VARCHAR(30) NOT NULL,
	age INTEGER NOT NULL CHECK(age >= 19)
);
```

This table will reject any entry where age is less than 19.

Attribute checks can also be added below all the attribute declarations using the keyword `CONSTRAINT`. This is equivalent to the above:
```sql
CREATE TABLE Users (
	uid INTEGER NOT NULL PRIMARY KEY,
	name VARCHAR(30) NOT NULL,
	age INTEGER NOT NULL,
	CONSTRAINT no_minor CHECH(age >= 19)
);
```


---
## Modifying schema
We can add a column, remove a column, change a column name, change a column data type, or add/remove constraints **after the table is created** using the `ALTER TABLE` statement.

To **add a column**, do:
```sql
ALTER TABLE table_name ADD COLUMN column_name;
```

To **remove a column**, do:
```sql
ALTER TABLE table_name DROP COLUMN column_name;
```

To **change a column name**, do:
```sql
ALTER TABLE table_name RENAME COLUMN old_name TO new_name;
```

To **change a column datatype**, do:
```sql
ALTER TABLE table_name ALTER COLUMN column_name datatype;
```

To **set a column to** `NOT NULL`, do:
```sql
ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL;
```

To **add a** `CONSTRAINT`, including primary key, foreign key, or attribute checks, do:
```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name constraint_condition;
```

To **remove a** `CONSTRAINT`, do:
```sql
ALTER TABLE table_name DROP CONSTRAINT constraint_name;
```

