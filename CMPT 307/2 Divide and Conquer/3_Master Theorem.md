Lectures 7-8

## Master Theorem for Recurrence Relations
In a [[1_Divide and Conquer#Divide and Conquer Algorithms|Divide and Conquer algorithm]], we break a problem into subproblems, solve those subproblems, and combine the answers.

**Specifically**, we break one problem of size $n$ into $a$ subproblems (*branching factor*), each has the size $\dfrac{n}{b}$, and combine the answers in $O(n^{d})$ time. ($a,b,n >0$ and $d\geq 0$)

In the [[2_Multiplication#Using Gauss|multiplication example]], we had $a=3$, $b=2$, and $d=1$ (linear time to add and left shift).

The running time in recurrence relation is:
$$
\boxed{ T(n)=a\cdot T\left( \left\lceil \dfrac{n}{b} \right\rceil  \right)+O(n^{d})  }
$$

The **Master Theorem** defines a big-O solution for these recurrence relations based on the values of $a,b,d$.

$$
T(n)=\begin{cases}
O(n^{d}) & \text{if }d>\log_{b}a \\
O(n^{d}\log n) & \text{if }d=\log_{b}a \\
O(n^{\log_{b}a}) & \text{if }d<\log_{b}a 
\end{cases}
$$

This theorem tells us the running time of *most* divide and conquer algorithms. It can be further generalized, but this is the basic form of it.

### Example: Binary Search
In [binary search](https://www.geeksforgeeks.org/dsa/binary-search/), we search for the index in a sorted array using a value. 

In each iteration, the array is split in half ($b=2$), and the other half is dismissed ($a=1$, a problem turns into only one subproblem of smaller size). Calculating the *mid* index and comparing it with the target can be done in constant time $O(1) \implies d=0$.

The running time of binary search is:
$$
T(n)=T\left( \dfrac{n}{2} \right)+O(1) 
$$
Applying the Master Theorem, $\log_{b}a=\log_{2}1=0$, then $d=\log_{b}a$. Therefore,
$$
\boxed{ T(n)=O(\log n) }
$$

