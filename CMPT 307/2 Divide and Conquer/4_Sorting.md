Lectures 8-9

## Merge Sort
In order to sort $n$ elements, sort 2 lists of $\frac{n}{2}$ elements, then **merge** the lists together.

Merge sort takes an unsorted array as the input, and will output the sorted array.

In pseudo code:
```
function mergeSort( a[1,2,...,n] ):
	if n > 1:
		return merge( 
			mergeSort(a[1,2,...,n/2]), 
			mergeSort(a[n/2+1,...,n])
		)
	else:
		return a
```

This requires a merging algorithm `merge()`. Trivially, it can be implemented in running time $O(n)$ by comparing the "current" smallest to each element and inserting the smaller into the new array.

Using the [[3_Master Theorem#Master Theorem for Recurrence Relations|Master Theorem]], merge sort has running time:
$$
T(n)=2T\left( \dfrac{n}{2} \right)+O(n)\implies \boxed{ T(n)=O(n\log n)  }
$$

Theoretically, $O(n\log n)$ is the **optimal** running time for sorting. Sorting algorithm relies on comparisons. For example, if we were sorting $a_{1},a_{2},a_{3}$, we can draw out the sorting tree as follows:

![[Screenshot 2026-10-18 at 12.59.38 AM.png|500]]

From this tree:
- each leaf is a **permutation** of the original array, the number of leaves is $6=n!$
- the depth of the tree (worst case) is $3$

This sorting tree is a **binary tree** (at most 2 children per node). Any binary tree with depth $d$ has at most $2^{d}$ leaves. 

In our example, the tree has $n!$ leaves. Working backwards to find the depth of the tree, it has to be **at least** $\log(n!)$.

Since:
$$
\log(n!) \geq c\cdot n\log n
$$
for some $c>0$, we can infer that:
$$
\log(n!)=\Omega(n \log n)
$$
which is the minimum running time for any comparison based sorting algorithm.

> [!tip] Sorting faster
> There *are* ways to sort faster, but requires certain conditions on the array. For example, integers that lie in a small range.

