Lectures 3-4

## Data Model
Mathematical, conceptual way for **describing data**. Consists of:
- **Structure**: schema (table names, attribute names, etc)
- **Operations**: retrieve (query) and change (update)
- **Constraints**: domain (*where balance > 0*) and integrity (*user ID is unique*)

There are 3 commonly used data models:
- **Relational** data model (see [[1_Database and DBMS#Relational Databases|Relational Databases]]), table structure
- **Key-value** data model (see [[1_Database and DBMS#NoSQL|NoSQL]]), key mapped to object values
- **Semi-structured** data model (see [[1_Database and DBMS#NoSQL|NoSQL]] on JSON), tree structure

### Relational Data Model
A database is a collection of **tables** (relations)
![[chart4.png|500]]

A table has a set of **columns** (attributes), and each column has a **name** and a **domain**. This is called the **schema** (metadata), which specifies the structure of data and rarely changes.
![[chart5.png|600]]

Each table contains a set of **rows** (tuples). Each row has a value for each attribute, duplicate rows are not allowed. This is called the **instance**, which represents the data content. Instances change rapidly, but always conform to the schema.
![[chart6.png|600]]

### Keys
A set of columns $K$ is a **key** for a table $R$ if:
- No instance of $R$ will two different rows agree on all attributes of $K$ (each row must have unique $K$)
- No proper subset of $K$ satisfies the above

For example, in the [[#Relational Data Model|bank example]] above, <span style="text-decoration: underline;">id</span> (of Users) is a key of Users, and <span style="text-decoration: underline;">id</span> (of Branches) is a key of Branches.

Keys are used to:
- add **more constraints** on data, leading to fewer mistakes
- **select** specific rows
- **pointers** to other rows across tables

