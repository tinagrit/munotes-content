Lectures 11-12

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

**Backward proof**:
$$
\text{graph is cyclic}\Leftarrow \text{DFS reveals a back edge}
$$
If the edge $(u,v)$ is a back edge, then there is a cycle consisting of this edge together with the path from $v$ to $u$ in the search tree.

**Forward proof**:
$$
\text{graph is cyclic}\Rightarrow \text{DFS reveals a back edge}
$$
If the graph has a cycle $\boxed{ v_{0} }\to \boxed{ v_{1} }\to\dots\to\boxed{ v_{k} }\to\boxed{ v_{0} }$, 

For the first node to be found by DFS (lowest $\text{pre}$ number), all other nodes in the cycle **can be reached** and will therefore be its **descendants** in the search tree.

Therefore, the edge that connects to that first node (e.g. $(v_{k},v_{0})$) leads from a node to its **ancestor**, and is a **back edge** by definition.


### Directed Acyclic Graphs
A **DAG** (*Directed Acyclic Graph*) is a directed graph with no cycles. It can be used to **model relations** like causalities, hierarchies, and temporal dependencies (some tasks have to be completed before others can start, such as cutting before cooking). 

If a graph is a DAG, we want to **linearize / topologically sort** it.

This is an example of a DAG:
![[Screenshot 2026-10-26 at 12.00.47 PM.png|400]]

We say that:
- $B$ is the **source**. No other nodes point to it.
- $E$ and $F$ are **sinks**. They do not point to any nodes.

A **topological sort** arranges the vertices in a possible ordering such that all nodes are visited. Some topological sorts in this example:
- $B\,\,A\,\,D\,\,C\,\,E\,\,F$
- $B\,\,D\,\,A\,\,C\,\,F\,\,E$

### Topological sorting algorithm
In a DAG, every edge leads to a vertex with **a lower** $\text{post}$ **number**. Therefore, this algorithm has linear time $O(n)$. 

Determining whether the graph is cyclic, is linearizable, and has a back edge in DFS **are the same thing**.

Since DAGs have decreasing $\text{post}$ numbers:
- the vertex with the **lowest** $\text{post}$ must be a **sink**
- the vertex with the **highest** $\text{post}$ must be a **source**

Sinks and sources are **guaranteed** to exist in every DAG, the linear algorithm to topologically sort is:
1. **Find a source**. Output it to the result. Delete it from the graph.
2. **Repeat** until the graph is empty.


