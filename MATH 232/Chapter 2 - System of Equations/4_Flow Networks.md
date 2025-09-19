Chapter 2.4


## Flow Networks
- flows through **branches**, can be traffic through roads, water through pipes, electricity through wires, etc.
- meet at **nodes** (intersections)

![[IMG_6971238DD2D7-1.jpeg|400]]

### Network Properties
- each branch is in **one direction** only
- in any **node**, rate of flow **in** is equal to rate of flow **out**
- in the **entire network**, rate of flow **in** is equal to rate of flow **out**

### Network Diagram

![[IMG_5B0EBC73792B-1.jpeg|400]]

- **dots** for nodes
- **lines** for branches (with an arrow indicating its direction)
- **flow rates** on the branches

### Finding unknown flow rates
- use [[#Network Properties|property]] (2) - "in any node, rate of flow **in** is equal to rate of flow **out**"
- for each node, equate all branches pointing **in** to all branches pointing **out**
- set up an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]] and reduce it to **solve for unknowns**

### Flow rates Examples

> In the following network, find the flow rates for $x_{1},x_{2},x_{3},x_{4}$

![[IMG_952F20E36D4E-1.jpeg|300]]

- At node $A$,
	- branch pointing **in** is $x_{4}$
	- branches pointing **out** are $100$ and $x_{1}$
	- Therefore, $x_{4}=100+x_{1}$
	- $\implies -x_{1}+x_{4}=100$
- At node $B$,
	- branches pointing **in** are $x_{1}$ and $500$
	- branch pointing **out** is $x_{2}$
	- Therefore, $x_{2}=x_{1}+500$
	- $\implies-x_{1}+x_{2}=500$
- At node $C$,
	- branch pointing **in** is $x_{3}$
	- branches pointing **out** are $x_{4}$ and $300$
	- Therefore, $x_{3}=x_{4}+300$
	- $\implies x_{3}-x_{4}=300$
- At node $D$,
	- branch pointing **in** is $x_{2}$
	- branches pointing **out** are $x_{3}$ and $100$
	- Therefore, $x_{2}=x_{3}+100$
	- $\implies x_{2}-x_{3}=100$

From the four equations, we are able to form an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]].
$$
M=\begin{bmatrix}
-1 & 0 & 0 & 1 & 100 \\
-1 & 1 & 0 & 0 & 500 \\
0 & 0 & 1 & -1 & 300 \\
0 & 1 & -1 & 0 & 100
\end{bmatrix}
$$
Using [[2_Row Echelon#Converting to REF (Gaussian)|Gaussian Elimination]] and [[3_Reduced REF#Converting to RREF (Gauss-Jordan)|Gauss-Jordan Elimination]], the RREF is as follows.
$$
\text{rref}(M)=\begin{bmatrix}
1 & 0 & 0 & -1 & -100 \\
0 & 1 & 0 & -1 & 400 \\
0 & 0 & 1 & -1 & 300 \\
0 & 0 & 0 & 0 & 0
\end{bmatrix}
$$
Use the RREF to find the [[3_Reduced REF#Solution Set|Solution Set]]
$$
\vec{x}=t\begin{bmatrix}
1\\1\\1\\1
\end{bmatrix}+\begin{bmatrix}
-100\\400\\300\\0
\end{bmatrix}\mid t \in \mathbb{R}
$$
This means that there is **not one value** that works but with any $t \in \mathbb{R}$.


> In the following network, find the flow rates and directions for $x_{1},x_{2},x_{3}$

![[IMG_33F6C49E4509-1.jpeg|300]]

Since the flow directions are unknown, **assume a direction** for each unknown branch. If the resulting value is negative, then it is the opposite direction. 
Assume that:
- $x_{1}$ flows out of node $A$ into node $B$
- $x_{2}$ flows out of node $C$ into node $A$
- $x_{3}$ flows out of node $B$ into node $D$

Solve normally:
- At node $A$,
	- branches pointing **in** are $50$ and $x_{2}$
	- branch pointing **out** is $x_{1}$
	- Therefore, $x_{1}=50+x_{2}$
	- $\implies x_{1}-x_{2}=50$
- At node $B$,
	- branch pointing **in** is $x_{1}$
	- branches pointing **out** are $30$ and $x_{3}$
	- Therefore $x_{1}=30+x_{3}$
	- $\implies x_{1}-x_{3}=30$
- At node $C$,
	- branch pointing **in** is $50$
	- branches pointing **out** are $x_{2}$ and $60$
	- Therefore, $50=x_{2}+60$
	- $\implies x_{2}=-10$
- At node $D$,
	- branches pointing **in** are $x_{3}$ and $40$
	- branch pointing **out** is $50$
	- Therefore, $x_{3}+40=50$
	- $\implies x_{3}=10$

From the four equations, we are able to form an [[1_Augmented Matrix#Augmented Matrix|augmented matrix]].
$$
M=\begin{bmatrix}
1 & -1 & 0 & 50 \\
1 & 0 & -1 & 30 \\
0 & 1 & 0 & -10 \\
0 & 0 & 1 & 10
\end{bmatrix}
$$
Using [[2_Row Echelon#Converting to REF (Gaussian)|Gaussian Elimination]] and [[3_Reduced REF#Converting to RREF (Gauss-Jordan)|Gauss-Jordan Elimination]], the RREF is as follows.
$$
\text{rref}(M)=\begin{bmatrix}
1 & 0 & 0 & 40 \\
0 & 1 & 0 & -10 \\
0 & 0 & 1 & 10 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$
Use the RREF to find the [[3_Reduced REF#Solution Set|Solution Set]]
$$
\vec{x}=\begin{bmatrix}
40 \\
-10 \\
10
\end{bmatrix}
$$
Notice that there is **only one solution** to this.

The negative quantity in $x_{2}$ implies that $x_{2}$ is in the **wrong direction** in our assumption. Simply have it point to the other side and **keep the scalar** magnitude.

Therefore, the complete diagram is as shown:

![[IMG_0FDB4B48FA72-1.jpeg|300]]
