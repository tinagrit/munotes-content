Lecture 10

## Graphs
Graphs can be used to present information in a **clear, uncluttered** way. It gives a good representation for many problems.

>[!tip] Use case: Map colouring
>If we want to colour a map, where bordering countries do not share the same colour. 
>
>We can represent countries with **nodes**, and borders of neighbouring countries with **edges**. We want to assign a colour to each node such that **no edges** have endpoints of the same colour.

A graph is a set of **vertices** (*nodes*) $V$, and a set of **edges** $E$ between the members of $V$.

An edge can be **directed** (has an arrow, asymmetric) or **undirected** (no arrow, symmetric).
![[chart01.png|450]]

### Adjacency matrix
Graphs can be represented using **adjacency matrix**. 

Let $n$ be the number of vertices, $n=|V|$. The adjacency matrix is an $n\times n$ matrix with:
$$
a_{ij}=\begin{cases}
1 & \text{if there is an edge from }v_{i}\text{ to }v_{j} \\
0 & \text{otherwise}
\end{cases}
$$

For this representation:
- **Advantage**: it is $O(1)$ lookup time for a particular edge
- **Disadvantage**: it is $O(n^{2})$ in space, so it is bad especially for sparse graphs

### Adjacency list
An alternative representation of graphs.

An **adjacency list** consists of $n=|V|$ linked lists, one per $v\in V$. The linked list for vertex $v$ holds **all vertices** $v$ that $(v,u) \in E$.

For this representation:
- **Advantage**: it is $O(|E|)$ in space. It is very easy to visit all neighbours of a particular vertex.
- **Disadvantage**: looking up a particular edge is no longer constant

