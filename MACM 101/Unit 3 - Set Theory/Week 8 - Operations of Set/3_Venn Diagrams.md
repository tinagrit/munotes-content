Section 3.3

A **Venn diagram** gives a graphic way of thinking about sets, for example:

See [[1_Operations of Set|Operations of Set]]

| Diagram     | Meaning    |
| ----------- | ---------- |
| ![[P1.png]] | $A$        |
| ![[E2.png]] | $A\cup B$  |
| ![[E3.png]] | $A \cap B$ |
| ![[E4.png]] | $A-B$      |


### DeMorgan's law proof
See [[2_The Laws of Set Theory#Proving DeMorgan's Law|DeMorgan's law]]

|                                |               |
| ------------------------------ | ------------- |
| $\overline{A\cap B}$           | ![[R1.png]]   |
| $\overline A$                  | ![[R2.png]]   |
| $\overline B$                  | ![[R3.png]]   |
| $\overline A \cup \overline B$ | ![[R1 1.png]] |


---

## Counting problem

> In a class of 50 college freshmen, 30 are studying Java, 25 are studying C++, 10 are studying both. How many freshmen are studying either computer languages?

$|A|=30$
$|B|=25$
$|A\cap B|=10$

Find $|A\cup B|$



Do with diagram:

![[U3.png]]

$|A\cup B| = 20+10+15 = 45$

Or do manually:
$|A\cup B| = |A| + |B| -$ overcounted (both $A$ and $B$)
$|A\cup B|=30+25-10=45$


### Principle of Inclusion-Exclusion

In general:
If $A$ and $B$ are finite sets, then $|A\cup B|=|A|+|B|-|A\cap B|$
- Finite sets $A,B$ are mutually disjoint if and only if $|A\cup B|=|A|+|B|$
- When $U$ is finite, from DeMorgan's law we have
	- $|\overline A \cap \overline B|$
		$= |\overline{A \cup B}|$
		$=|U|-|A\cup B|$
		$=|U|-|A|-|B|+|A\cap B|$


If $A,B,C$ are finite sets, then
$|A\cup B\cup C|$
$=|A|+|B|+|C|-|A\cap B|-|A\cap C|-|B\cap C|+|A\cap B\cap C|$

Also, $|\overline A \cap \overline B \cap \overline C|$
$=|\overline{A\cup B\cup C}|$
$=U-|A\cup B\cup C|$$=U-|A|-|B|-|C|+|A\cap B|+|A\cap C|+|B\cap C|-|A\cap B\cap C|$


> A manufacturer builds 100 sprockets. The sprockets can have one of three possible defects when built.
> Let $A,B,C$ be the subsets of the 100 sprockets with the first, second, and third types of defects. We are given that:
> $|A|=23$     $|B|=26$     $|C|=30$
> $|A\cap B|=7$     $|A\cap C|=8$     $|B\cap C|=10$
> $|A\cap B \cap C|=3$
> How many sprockets have at least one of the defects?

Find $A\cup B\cup C$

Do with diagram:

![[U2.png]]

$A\cup B\cup C=11+4+12+5+3+7+15=57$ sprockets

Or do manually:

$|A\cup B\cup C|$
$=|A|+|B|+|C|-|A\cap B|-|A\cap C|-|B\cap C|+|A\cap B\cap C|$
$=23+26+30-7-8-10+3$
$=57$ sprockets