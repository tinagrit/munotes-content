Lectures 10-11

## Depth First Search for Undirected Graphs
*Depth First Search* traverses a [[1_Graphs#Graphs|graph]] **in linear time**. It answers questions like
1. What part of graph is reachable from a given vertex?
2. What are the connected components of a graph?

### Traversing from a starting point
While traversing, we only have the [[1_Graphs#Adjacency list|adjacency list]] to go with. 
- We place a **boolean** on each vertex $v$ to mark that it has **been visited**. 
- We use a **stack** to remember the path we've taken, *pushing* means visiting a new vertex, and *popping* means backtracking. The stack is maintained implicitly using [[1_Divide and Conquer#Divide and Conquer Algorithms|recursion]].

This algorithm explores the reachable vertices from the starting vertex. 
- It takes input the graph $G=(V,E)$ and the starting vertex $v \in V$. 
- It returns a set `visited` where `visited(u)` is `true` if $u$ is reachable from $v$.
```
function explore(G, v):
	visited(v) = true
	
	for each edge (v, i) ∈ E:
		if not visited(i): explore(G, i)
```

### Traversing entire graph
*Depth First Search* explores **the entire graph** by repeatedly calling `explore()` until all vertices are explored.
```
function dfs(G)
	for all v ∈ V:
		visited(v) = false
	
	for all v ∈ V:
		if not visited(v): explore(v)
```

In DFS, each vertex is only explored **once** (due to having the `visited` array). During an exploration, we mark the spot as visited in constant time ($O(|V|)$ for all vertices), and loop through all the adjacent edges ($O(|E|)$ for all edges).

The running time of DFS is in $\boxed{ O(|V|+|E|) }$.

For example, if we have this graph:
![[Screenshot 2026-10-19 at 11.59.29 AM.png|400]]

By convention, we start the first node using **alphabetical order**. In this case, we start at $A$. We visit all nodes connected to $A$, starting from $B$. There is nothing deeper than $B$, we backtrack to $A$ and move on to $E$. In the DFS tree, we note down the ***timestamp*** of the ***previsit*** and ***postvisit*** of each vertex.

![[Screenshot 2026-10-19 at 12.00.49 PM.png|200]]

The dotted line is to acknowledge the existence of the edge $\left\{ E,J \right\}$, although vertices $E$ and $J$ have already been visited.
- The solid lines are called **tree edges**, edges that are part of the DFS forest
- The dotted lines are called **non-tree edges**

`dfs()` is not finished. The next node in alphabetical order that has not been visited is $C$. We visit all nodes connected to $C$, starting from $D$, then deeper into $H$. From $H$, the first alphabetical node is $G$, then deeper into $K$. There is nothing deeper than $K$, we backtrack to $H$ via $G$, then visit $L$. 

![[Screenshot 2026-10-19 at 12.06.31 PM.png|220]]

`dfs()` is still not finished. The node $F$ was never explored. We visit $F$, and since there is nothing deeper than $F$, we stop.

![[Screenshot 2026-10-19 at 12.10.08 PM.png|80]]

The entire search process consists of many trees, we call it the **DFS forest**.
![[Screenshot 2026-10-19 at 12.10.54 PM.png|520]]


### Connectivity
An undirected graph is **connected** if all pairs of vertices have a path to each other. 

For instance, the graph above is *not connected* since there is no path from $A$ to $K$. The graph has 3 **connected components**:
$$
\begin{align}
\left\{ A,B,E,I,J \right\} &  & \left\{ C,D,H,G,K,L \right\} &  & \left\{ F \right\}   
\end{align}
$$

When *Depth First Search* calls `explore()` on one of the vertices, all of the vertices in the same connected components are explored. The **outer loop** of the algorithm iterates through **each connected component**.

The algorithm can place a number `ccnum` (*Connected Component Number*) to all vertices in the same connected component. If all vertices have the same `ccnum`, the graph is **connected**.

### Timestamp Property
For any nodes $u$ and $v$, the 2 intervals $[\text{pre}(u),\text{post}(u)]$ and $[\text{pre}(v),\text{post}(v)]$ are either **disjoint** or **completely contained** within one another.

$[\text{pre}(u),\text{post}(u)]$ is the time where $u$ lives on the **stack**.