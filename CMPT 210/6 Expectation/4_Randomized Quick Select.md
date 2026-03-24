Lecture 17

## Randomized Quick Select
Given an array $A$ of $n$ distinct numbers, return the $k^{\text{th}}$ smallest element in $A$

Algorithm:
**Quick Select** $(A,k)$:
- If $|A|=1$ then return the only element
- Let $p=$ random element in $A$
- Let:
	- $\text{Left}=\left\{ x \in A \mid x<p \right\}$
	- $\text{Right}=\left\{ x \in A \mid x > p \right\}$
	- $r=|\text{Left}| + 1$
- If $k=r$ then return $p$
	- Else if $k < r$ then do **Quick Select** $(\text{Left},k)$
	- Else if $k>r$ then do **Quick Select** $(\text{Right},k-r)$

### Analysis
The naive approach to this problem is to sort the array, then return the $k^{\text{th}}$ element. Using a standard sorting algorithm like merge sort, the runtime is $O(n \log n)$.

Using randomized quick select, the absolute worst case is $O(n^{2})$, which is worse than sorting, but the average case is $O(n)$, making less than $8n$ comparisons.

### Example
Using the algorithm, find the $2^{\text{nd}}$ smallest ($k=2$) element from $A=\left\{ 2,7,0,1,3 \right\}$ 

**Quick Select** $(A,2)$:
- $|A|$ is not $1$, continue
- Let $p=3$ (random element)
- Let:
	- $\text{Left}=\left\{ 2,0,1 \right\}$
	- $\text{Right}=\left\{ 7 \right\}$
	- $r=3+1=4$
- $k<r$, we recurse **Quick Select** $(\text{Left},2)$

**Quick Select** $(\text{Left}=\left\{ 2,0,1 \right\},2)$:
- $|\text{Left}|$ is not $1$, continue
- Let $p=1$ (random element)
- Let:
	- $\text{Left}=\left\{ 0 \right\}$
	- $\text{Right}=\left\{ 2 \right\}$
	- $r=1+1=2$
- $k=r$, we return $p=1$

The select smallest element in $A$ is $1$.

