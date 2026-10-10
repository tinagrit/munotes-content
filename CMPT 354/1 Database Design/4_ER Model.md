Lectures 4-5

## Entity/Relationship model
A popular database **design model**, along with ODL (*Object Definition Language*) and UML (*Unified Modelling Language*). It is more intuitive and convenient for [[2_Relational Data Model#Relational Data Model|schema]] design.

### Design Process
1. **Requirements analysis**
	- What data will be stored?
	- What to do with the data?
	- Who should access the data?
2. **Conceptual  Design**
	- E/R model, high-level description
	- Sufficiently precise
3. **Logical, physical, security, etc.**

### Entities and Attributes
- An **entity** is a "thing", for example, a user
- An **entity set** (in rectangles) is a collection of things, a group of users
- **Attributes** (in ovals) are properties of entities

[[2_Relational Data Model#Keys|Keys]] are **underlined**.

![[chart8.png|300]]

### Relationships
- A **relationship** is an association among entities
- A **relationship set** (in diamonds) consists of relationships of the same type, such as "chair ***belongs to*** a room"

![[chart9.png|600]]

A relationship between *users* and *groups* is a **subset of all possible combinations** (see [[3_Relational Algebra#Join|Join]])

A relationship can have **attributes**, such as the date that the user joined the group.

![[chart10.png|600]]

### Roles
The edges of between an entity set and a relationship set can be **labelled** to distinguish **roles**, for example:

![[chart14.png|250]]

### Multiplicity
Relationship sets can have the numerical quantity specified.

For $E$ and $F$ entity sets,
- **Many-many**: each entity in $E$ is related to ≥0 entities in $F$, each entity in $F$ is related to ≥0 entities in $E$
![[chart11.png|300]]

- **Many-one**: each entity in $E$ is related to 0 or 1 entity in $F$, each entity in $F$ is related to ≥0 entities in $E$
![[chart12.png|600]]

Note: use the rounded arrow to indicate *exactly one*, instead of *0 or 1*.

- **One-one**: each entity in $E$ is related to 0 or 1 entity in $F$, each entity in $F$ is related to 0 or 1 entity in $E$
![[chart13.png|300]]

### n-ary relationships
A relationship set can have more than 2 arrows. For example:

![[chart15.png|400]]

This means that for each member in a group, there can be 0 or 1 initiator. The same user cannot be initiated by 2 people into the group.

### Weak entities
A **weak entity set**'s key comes from the keys of one or more other entity sets. Its identity **depends on others**.

A weak entity set (in double rectangle) is related to the key holder using a **supporting relationship set** (in double diamonds). This can only be [[#Multiplicity|many-one or one-one]], since the *one* side is the entity that we are using the key of.

For example,
![[chart16.png|700]]

Room "2026" can exist in both buildings "SUB" and "WMC", since the uniqueness of the 2026 depends on the building it is in.

### ISA relationships
An entity set can entirely be a **subclass** of another, **ISA relationships** (in triangles) point towards the parent.

![[chart17.png|350]]


---
## Translating to Relational Schema

An [[#Entities and Attributes|entity set]] is a table. 
- *User* (<span style="text-decoration: underline;">uid</span>, name, balance)
![[chart8.png|300]]

A [[#Weak entities|weak entity set]] is table, with the corresponding key as an extra column. The supporting relationship does not need a table, since it is already implicit in this table. 
- *Building* (<span style="text-decoration: underline;">name</span>)
- *Room* (<span style="text-decoration: underline;">building_name</span>, <span style="text-decoration: underline;">number</span>, capacity)
![[chart16.png|700]]

A [[#Relationships|relationship set]] is a table, with the keys of connected entity sets as columns. For [[#Multiplicity|many-one]] relationships, the table key is the edge with *no arrow*. Otherwise, the table key is all the edges.
- *User* (<span style="text-decoration: underline;">uid</span>, name)
- *Group* (<span style="text-decoration: underline;">gid</span>, name)
- *Member* (<span style="text-decoration: underline;">uid</span>, <span style="text-decoration: underline;">gid</span>)
![[chart11.png|300]]

- *Owner* (<span style="text-decoration: underline;">gid</span>, uid)
![[chart12.png|600]]

### Translating ISA
There are 3 approaches to translating an [[#ISA relationships|ISA relationship]]. 

Using this E/R model, and we have "Alpha", a student, and "Bravo", a non-student:
![[chart18.png|300]]


1. **Entity-in-all-superclasses** (*E/R style*), tables for both *Person* and *Students*. All *Students* are also stored in *Person*. 
	- *Person* (<span style="text-decoration: underline;">id</span>, name) →  (1234, Alpha) (5678, Bravo)
	- *Students* (<span style="text-decoration: underline;">id</span>, gpa) → (1234, 3.50)

2. **Entity-in-most-specific-class** (*OO style*), tables for both *Person* and *Students*. All *Students* are only stored in *Students*, with attributes from *Person*.
	- *Person* (<span style="text-decoration: underline;">id</span>, name) → (5678, Bravo)
	- *Students* (<span style="text-decoration: underline;">id</span>, name, gpa) → (1234, Alpha, 3.50)

3. **All-entities-in-one-table** (*NULL style*), only one table for the root (*Person*). The table has all attributes of the subclasses, use *NULL* on irrelevant cells.
	- *Person* (<span style="text-decoration: underline;">id</span>, name, gpa) → (1234, Alpha, 3.50) (5678, Bravo, NULL)

