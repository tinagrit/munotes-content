Lecture 11

## Depth First Search for Directed Graphs
The [[2_Undirected DFS#Traversing entire graph|DFS algorithm]] can be used in [[1_Graphs#Graphs|directed graphs]], called *DGraphs*, only travelling in the **direction of the arrows**.

By using the same algorithm to construct the DFS tree, for example in this graph:
![[Screenshot 2026-10-21 at 10.51.33 AM.png|550]]

Note that the **arrows** are present in the graph and the DFS tree.

We say that:
- $A$ is the **root** of the tree, everything else is its **descendants**
- $E$ is the **ancestor** of $F$, $G$, and $H$ (anything above)
- $F$, $G$, and $H$ are **descendants** of $E$ (anything below)
- $C$ is the **parent** of $D$ (directly above)
- $D$ is a **child** of $D$ (directly below)

While [[2_Undirected DFS#Traversing entire graph|undirected DFS]] has tree edges and non-tree edges, directed DFS has more terms:
- **Tree edges**, the solid lines
- **Non-tree edges**, the dotted lines
- **Forward edges**, non-tree edges from a node to its non-child descendant (points below but not directly below), like the edge $A\to F$ and $E\to G$
- **Back edges**, non-tree edges from a node to its ancestor, like the edge $D\to A$ and $F\to B$ 
- **Cross edges**, non-tree edges from a node to *neither* ancestor nor descendant, like the edge $H\to G$ and $D\to H$. The node it leads to, therefore, must be **completely explored**.

The ancestor, descendant relationships can be **read off directly** from $\text{pre}$ and $\text{post}$ numbers.

The previsit of $u$, $\text{pre}(u)$, can be written as $\underset{ u }{ [ }$ , and the postvisit of $u$, $\text{post}(u)$, can be written as $\underset{ u }{ ] }$ .

If the pre- and post- visits of $v$ are completely **contained** within $u$, that is:
$$
\underset{ u }{ [ }\,\,\,\underset{ v }{ [ }\,\,\,\underset{ v }{ ] }\,\,\,\underset{ u }{ ] }
$$
then $v$ is a **descandant** of $u$.

These are the possibilities for an edge $u\to v$:

| Pre-,post- ordering                                                                              | Edge type                  |
| ------------------------------------------------------------------------------------------------ | -------------------------- |
| $\underset{ u }{ [ }\,\,\,\underset{ v }{ [ }\,\,\,\underset{ v }{ ] }\,\,\,\underset{ u }{ ] }$ | Tree edge, or forward edge |
| $\underset{ v }{ [ }\,\,\,\underset{ u }{ [ }\,\,\,\underset{ u }{ ] }\,\,\,\underset{ v }{ ] }$ | Back edge                  |
| $\underset{ v }{ [ }\,\,\,\underset{ v }{ ] }\,\,\,\underset{ u }{ [ }\,\,\,\underset{ u }{ ] }$ | Cross edge                 |

### Cycles
A **cycle** in a directed graph is a **circular path**:
$$
\boxed{ v_{0} }\to \boxed{ v_{1} }\to\dots\to\boxed{ v_{k} }\to\boxed{ v_{0} }
$$
A graph with a cycle is called a **cyclic graph**.

In the example graph above, an example of a cycle is $B\to E\to F\to B$, and therefore the graph is cyclic.

DFS can determine whether there are cycles in a graph **in linear time** $O(n)$ where $n$ is the number of vertices. A directed graph has a cycle ***if and only if*** it has a **back edge**.
$$
\text{graph is cyclic}\iff \text{DFS reveals a back edge}
$$

