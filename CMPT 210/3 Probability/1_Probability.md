Lecture 5

## Sample Space

A sample space (or *outcome space*; $S$) is a non-empty [[1_Sets#Sets|set]] of **all possible outcomes**
- An element $w \in S$ is called an **outcome**.
- A [[1_Sets#Subsets|subset]] $E \subseteq S$ is called an **event**.

For example, rolling a 6-sided die, we have:
- Sample space: $S=\left\{ 1,2,3,4,5,6 \right\}$
- An example outcome: $w=5$
- An example event: $E=\left\{ 3,4 \right\}$

*Also see* [[1_Sets#Set operations|Set operations]]

### Union of Events
Let $E_{1}$, $E_{2}$ be events in the sample space $S$. The union ($\cup$) of $E_{1}$ and $E_{2}$ is:
$$
E_{1}\cup E_{2}=\left\{ w\in S \mid w  \in E_{1} \lor w \in E_{2}\right\} 
$$
(Note: $\lor$ denotes the **OR** operator)

The union is the event that occurs when **either event** occurs.

The union of $n$ events can be expressed as:
$$
\bigcup_{i=1}^{n}E_{i}=E_{1} \cup E_{2} \cup \dots\cup E_{n}
$$
, which occurs when **any of** $E_{i}$ occurs

![[chart02.png|300]]


### Intersection of Events
Let $E_{1}$, $E_{2}$ be events in the sample space $S$. The intersection ($\cap$) of $E_{1}$ and $E_{2}$ is:
$$
E_{1}\cap E_{2}=\left\{ w \in S \mid w \in E_{1} \land w\in E_{2} \right\} 
$$
(Note: $\land$ denotes the **AND** operator)

The intersection is the event that occurs when **both events** occur.

The intersection of $n$ events can be expressed as:
$$
\bigcap_{i=1}^{n}E_{i}=E_{1}\cap E_{2}\cap\dots\cap E_{n}
$$
, which occurs when **all of** $E_{i}$ occur

![[chart03.png|300]]


### Mutual Exclusiveness
Two events $E_{1}$, $E_{2}$ are mutually exclusive *if and only if* $E_{1}\cap E_{2}=\varnothing$.

This happens when two events **cannot occur simultaneously**. For example, rolling a 6-sided die, we cannot get a $3$ and a $4$ at the same time.


### Complement
Let $E$ be an event in the sample space $S$. The complement $\overline{E}$ is every outcome in $S$ that is not in $E$.

Complements must satisfy:
- $E\cap \overline{E}=\varnothing$
- $E\cup \overline{E} = S$

For example, rolling a 6-sided die, if an event $E=\left\{ 5 \right\}$, then the complement (not 5) is $\overline{E}=\left\{ 1,2,3,4,6 \right\}$

![[chart05.png|300]]


### Subset of Events
Let $E_{1}$, $E_{2}$ be events in the sample space $S$. Event $E_{1}$ can be a subset of another event $E_{2}$ ($E_{1}\subseteq E_{2}$) if $E_{1}$ implies $E_{2}$ ($E_{1} \implies E_{2}$)

![[chart01.png|200]]
(Let $A=E_{1}$ and $B=E_{2}$ in the illustration.)

If event $A$ occurs, then event $B$ must also occur, since $A \subset B$. 