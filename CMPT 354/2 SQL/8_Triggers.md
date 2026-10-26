Lecture 9

## Triggers
A **trigger** is an *Event-Condition-Action* rule. When an **event** occurs, check for a **condition**, and if such condition is satisfied, execute an **action**.

For example:
```sql
CREATE TRIGGER ageCheck
AFTER UPDATE OF age ON Users
REFERENCING NEW ROW AS newUser
FOR EACH ROW
WHEN (newUser.age < 19) AND (newUser.uid IN (
	SELECT uid FROM Members WHERE gid=15
))
DELETE FROM Members WHERE uid=newUser.uid AND gid=15;
```

In this trigger:
- **Event**: when the age attribute is updated on the table *Users* (`AFTER UPDATE OF age ON Users`)
- **Condition**: if the user is under 19 and in group 15 (`WHEN (newUser.age...`)
- **Action**: remove the user from group 15 (`DELETE FROM Members...`)

A trigger *can* cause an infinite recursion loop. 

### Events
Triggers can be used on these events
```sql
CREATE TRIGGER ageCheck
AFTER [UPDATE OF age ON Users]
REFERENCING NEW ROW AS newUser
...
```

- `UPDATE ON table_name`
- `INSERT ON table_name`
- `DELETE ON table_name`

Optional: specific attribute can be added by `OF column_name` before the `ON`. For example, `UPDATE OF column_name ON table_name`.

### Timing
```sql
CREATE TRIGGER ageCheck
[AFTER] UPDATE OF age ON Users
REFERENCING NEW ROW AS newUser
...
```

- `BEFORE` check the condition and execute *before* executing the event
- `AFTER` check the condition and execute *after* executing the event

If [[7_Constraints#Constraints|constraints]] are involved, the constraint checks happen **after a** `BEFORE` **trigger** and **before an** `AFTER` **trigger**.

Another timing is `INSTEAD OF`. This is used to **execute a different action** instead of the triggering statement. The triggering statement **is not run**. This is particularly useful in [[9_Views#Use case for INSTEAD OF|Views]].

### Granularity
Level of activation can be per **rows affected** or **statement**. 

**Row-level activation**: when a table is modified, run a trigger on *each affected rows*. If one statement changes 20 rows (e.g. `UPDATE Users SET age=20;`), the trigger is run 20 times.

```sql
CREATE TRIGGER ageCheck
AFTER UPDATE OF age ON Users
REFERENCING [NEW ROW AS newUser,
            OLD ROW AS oldUser]
[FOR EACH ROW]
...
```

Use `FOR EACH ROW`. For referencing, use:
- `OLD ROW` to refer to the affected row **before** the event happened
- `NEW ROW` to refer to the affected row **after** the event happened

**Statement-level activation**: when a table is modified using a statement (`UPDATE`, `INSERT`, `DELETE`), run a trigger *once* per statement. If one statement changes 20 rows, the trigger is run 1 time.

```sql
CREATE TRIGGER ageCheck
AFTER UPDATE OF age ON Users
REFERENCING [NEW TABLE AS newUsers,
            OLD TABLE AS oldUsers]
[FOR EACH STATEMENT]
...
```

Use `FOR EACH TABLE`. For referencing, use:
- `OLD TABLE`, a read-only table with *only affected rows* **before** the event happened
- `NEW TABLE`, a table with *only affected rows* **after** the event happened



