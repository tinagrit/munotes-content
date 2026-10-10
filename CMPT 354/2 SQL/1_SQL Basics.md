Lecture 7

## SQL
The **Structured Query Language** (*pronounced* S-Q-L or Sequel) is the standard query language supported by most [[1_Database and DBMS#DBMS|DBMS]].

### Data-definition language
SQL can define/modify schemas, and delete relations.

Example 1

```sql
CREATE TABLE User(uid integer, name varchar(30), age integer);
```
This creates *User* (uid, name, age). No keys are specified. `varchar(x)` means a string with maximum `x` characters.

Example 2
```sql
DROP TABLE User
```
This deletes the *User* relation.

### Select-From-Where statement
SQL's `SELECT` statement takes the form:
```sql
SELECT A1, A2, ..., An
FROM R1, R2, ..., Rn
WHERE condition;
```

Corresponds to:
$$
\pi_{A_{1},A_{2},\dots,A_{n}}(\sigma_{condition}(R_{1}\times R_{2} \times \dots \times R_{m}))
$$

- The `WHERE` clause is **optional**.
- If there are string literals, use **single quotes**. They are **case sensitive**.
- SQL commands are case **insensitive**, `SELECT` = `Select` = `select`

SQL uses Select-From-Where because many queries can be **written using only** [[3_Relational Algebra#Selection|selection]], [[3_Relational Algebra#Projection|projection]], and [[3_Relational Algebra#Cross Product|cross product]].

Example 1: Using `*`. 
Listing all rows in the *User* table:
```sql
SELECT * FROM User;
```
Here, we only select from a single table, so no cross product. `*` means all columns.

Example 2: Using condition.
Selecting names of users under 18:
```sql
SELECT name FROM User WHERE age<18;
```

Example 3: Using expression.
Finding Lisa's age:
```sql
SELECT 2026-year FROM User WHERE name = 'Lisa';
```
The `SELECT` can contain **expressions**. Here, we subtract the birth year from 2026 to get Lisa's age.

Example 4: Using [[3_Relational Algebra#Join|cross product join]].
Finding the name of the group with a user named "Simpson":
```sql
SELECT Group.name
FROM User, Member, Group
WHERE User.uid = Member.uid
AND Member.gid = Group.gid
AND User.name LIKE '%Simpson%';
```
Here, `LIKE` matches a string against a pattern. `%` matches any sequence of zero or more characters.

Example 5: [[3_Relational Algebra#Renaming|Renaming]] column.
Returning the *first_name* column as "First Name":
```sql
SELECT first_name AS 'First Name' FROM User
```

