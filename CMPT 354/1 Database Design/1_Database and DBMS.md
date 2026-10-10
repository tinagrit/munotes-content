Lectures 1-2

## Database
A database is an **organized collection** of data, usually stored in multiple files and are accessed by many programs. 

A database is **not** a DBMS (*Database Management Systems*). MySQL, PostgreSQL, and Oracle are DBMS.

In a database, many programs access the data files **directly**. This *can* become a problem when these programs read or write the same data at the same time. It is also not efficient if we need to access one record out of millions, or if we need to access data stored in multiple files.

![[chart1.png|500]]

## DBMS
A DBMS (*Database Management Systems*) is a software that **stores**, **manages**, **centralizes**, and **facilitates** access to data.

All inputs and outputs go through the DBMS, rather than providing each program direct access.

![[chart2.png|500]]

This helps with:
- Access efficiency
- Data integrity and security
- Concurrent access
- Crash recovery
- Logical and physical data independence
- Reduced application development time

Standard features of a DBMS include:
- **Persistent** storage of data
- **Logical** data model, declarative queries and updates
- Multi-user **concurrent** access
- Safety from system **failures**
- High **performance**: amount of data, throughput, availability


### Navigational Databases
- Use **explicit paths** to tell the system how to reach a record
- Early efforts in 1960s-70s. 
- **CODASYL** (*Conference/Committee on Data Systems Languages*) defines navigational data model as standard database interface.
- Queries become **complex and hard to code**, programmers need to:
	- navigate the database
	- write efficient code
	- rewrite everything when the database changes

### Relational Databases
- Data stored **in tables** (relations), records reached using **declarative queries**
- Invented by Edgar Codd, 1970 - Now
- Programmer specifies **what answers** should the query return, not **how** the query is executed
- This provides physical **data independence**, where applications do not have to worry about how data is physically stored. Leave the implementation details to DBMS.
- Traditional **SQL** (Microsoft SQL, Oracle) has limitations:
	- It is not scalable
	- It has pre-defined schema

### NoSQL
- Emerged with the **internet boom** (Web 2.0, the Read-write web), 2000 - Now
- Used for OLTP (*Online Transaction Processing*), high frequency updates, small queries
- Commercial distributed database systems are expensive
- **Flexible** design, supports **horizontal scaling**
- NoSQL has limitations:
	- Low-level language, database-specific commands
	- Weak consistency, eventual consistency
	- Lack of standardization, 100+ systems of NoSQL

![[chart3.png|600]]

### NewSQL
- Modern solutions, 2010 - Now
- Used for OLTP
- Combines the **horizontal scalability** of NoSQL with the **consistency** of SQL
- NewSQL has limitations:
	- Scalable but not highly scalable
	- Available but not highly available
	- Flexible but not highly flexible

### MapReduce
- Used for OLAP (*Online Analytical Processing*), low frequency updates, big queries
- Many problems are processed in this pattern:
	- Unsorted data
	- **Map**: extra value of interest from each record
	- **Shuffle**: group intermediate results
	- **Reduce**: process each group and produce final results
- Advantages of MapReduce over parallel DBMS
	- No schema, no indexing
	- Fault tolerant
	- Higher scalability and elasticity
	- Complex analytics
	- Heterogeneous (mixed) storage systems