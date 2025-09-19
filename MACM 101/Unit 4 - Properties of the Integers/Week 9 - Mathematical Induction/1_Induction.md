Section 4.1

## Definition

For the [[Sets and Subsets#Subset|subset]] $Z^+$ of [[Sets and Subsets#Sets|set]] $Z$:
- $Z^+= \{ x \in Z | x > 0 \}=\{  x \in Z | x \geq 1  \}$ 
	- both sets mean the same thing but saying $x \geq 1$ shows the smallest value
For the subsets $Q^+$ and $R^+$:
- $Q^+=\{x\in Q | x > 0\}$
- $R^+=\{x\in R | x>0\}$
	- For these sets, it is impossible to find the smallest value of each set

### The Well-Ordering Principle
Any *non-empty* subset of $Z^+$ contains a smallest element.

> [!info] We can always find the smallest value of a well ordered set

- $Z^+$ is well ordered
- $Q^+$ and $R^+$ are **not** well ordered


---
## Principle of Mathematical Induction
- Useful tool for proving that a certain predicate is true for ***all positive integers***.
	- [[The Proof of Theorems#Proof by Method of Exhaustion|Method of exhaustion]] doesn't work since it is impossible to exhaust all of the positive integers
- *Cannot* be used to **discover** theorems, only to **prove**
- If we have a propositional function $P(n)$, and we want to prove that $P(n)$ is true for any positive integer $n$, we do the following:
	- Show that $P(1)$ is true (**basis**)
		- *Use the smallest possible value, in some case it can be something else*
	- Show that if $P(n)$ then $P(n+1)$ for any $n \in Z^+$ (**inductive**)
	- Then $P(n)$ must be true for any $n \in Z^+$ (**conclusion**)

### Examples

> Prove that for all $n \in Z^+$,
> $1+2+3+\ldots+n=\dfrac{n(n+1)}{2}$

$S(n):$      $\displaystyle\sum_{i=1}^{n}i=\frac{n(n+1)}{2}$

- **Basis**
	- Prove that this relationship holds when $n=1$
	- $\displaystyle\sum_{i=1}^{1}i=1$
	- $\dfrac{1(1+1)}{2}=1$
	- So $S(1)$ is ***true***
- **Induction**
	- Assume $S(k)$ is true, i.e., $\displaystyle\sum_{i=1}^{k}i=\dfrac{k(k+1)}{2}$ for $k\in Z^+$
	- Must show $S(k+1)=$ $\displaystyle\sum_{i=1}^{k+1}i=\frac{(k+1)(k+2)}{2}$
		- $\displaystyle\sum_{i=1}^{k+1}i=1+2+3+\ldots+k+(k+1)$
				$\displaystyle=\sum_{i=1}^{k}i+(k+1)$
				$=\dfrac{k(k+1)}{2}+(k+1)$
				$=\dfrac{k(k+1)+2(k+1)}{2}$
				$=\dfrac{(k+1)(k+2)}{2}$
	- $S(k)$ being true leads to $S(k+1)$ being true
- **Conclusion**
	- By the Principle of Mathematical Induction, $S(n)$ **is true** for $n\in Z^+$


> Prove that for each $n \in Z^+$,
> $1^2+2^2+\ldots+n^2=\dfrac{n(n+1)(2n+1)}{6}$

$S(n):$      $\displaystyle\sum_{i=1}^{n}i^2$

- **Basis**
	- $S(1):$
	- $\displaystyle\sum_{i=1}^{1}i^2=1$
	- $\dfrac{1(1+1)[2(1)+1]}{6}=\dfrac{6}{6}=1$
	- $S(1)$ is ***true***
- **Induction**
	- $S(k)$ is true for $k\in Z^+$
	- Show that:
		- $S(k+1)=\displaystyle\sum_{i=1}^{k+1}i^2=\dfrac{(k+1)(k+1+1)(2(k+1)+1)}{6}$
							$=\dfrac{(k+1)(k+2)(2k+1)}{6}$
	- $S(k+1)=\displaystyle\sum_{i=1}^{k+1}i^2=1^2+2^2+3^2+\ldots+k^2+(k+1)^2$
						$=\displaystyle\sum_{i=1}^{k}i^2+(k+1)^2$
						$=\dfrac{k(k+1)(2k+1)}{6}+(k+1)^2$
						$=(k+1)\left[\dfrac{k(2k+1)}{6}+(k+1)\right]$
						$=(k+1)\left[\dfrac{2k^2+7k+6}{6}\right]$
						$=(k+1)\left[\dfrac{(k+2)(2k+1)}{6}\right]$
						$=\dfrac{(k+1)(k+2)(2k+1)}{6}$
- **Conclusion**
	- By the Principle of Mathematical Induction, $S(n)$ **is true** for $n\in Z^+$ 


### Proof

Let $S(n)$ be an open statement **satisfying** $(a)$ and $(b)$ of the Principle of Mathematical Induction

Let $F=\{t\in Z^+|S(t)$ is false$\}$
Show that $F$ is $\varnothing$
- Prove that the set of all integers that **don't** **satisfy** the Principle be empty

**[[The Proof of Theorems#Prove by contradiction|Prove by contradiction]]**: Assume $F\not = \varnothing$

- $F$ is a subset of $Z^+$, so by the well-ordering principle, $F$ has a least element $m$
	- If $F$ is not empty, it has a smallest element

- $m\not = 1$  because part $(a)$ of the Principle requires that $S(1)$ is true
	- Then $m>1$.

- While $m-1\in Z^+$,
	- Since $m$ is the smallest element in the set $F$, then  $m-1\not\in F$

- Since $F$ contains all integers that make $S(n)$ false, then $S(m-1)$ is true

- By part $(b)$ of the Principle, $S(m-1)$ being true,
	- also leads to $S((m-1)+1)=S(m)$ being true.

- If $S(m)$ is true, then $m\not \in F$

- $m\in F$ and $m\not \in F$: **contradiction**.
- $\therefore F=\varnothing$


### Importance of the Basis step

The Basis step might be obvious, but ***don't skip it***. For example:

> If $n \in Z^+$, establish the validity of the open statement:
> $S(n):$           $1+2+3+\ldots+n=\dfrac{n^2+n+2}{2}$

By skipping the basis step:
- **Induction**
	- Assume $S(k)$ is true
	- Must show that $S(k+1)=\displaystyle\sum_{i=1}^{k+1}i=\frac{(k+1)^2+(k+1)+2}{2}$
									$=\dfrac{k^2+3k+4}{2}$
	- $S(k+1)=\displaystyle\sum_{i=1}^{k+1}i=1+2+3+\ldots+k+(k+1)$
						$=\displaystyle\sum_{i=1}^{k}i+(k+1)$
						$=\dfrac{k^2+k+2}{2}+(k+1)$
						$=\dfrac{k^2+3k+4}{2}$
	- For each $k\in Z^+$ it follows that $S(k)\implies S(k+1)$
- **BUT**: $S(1):$
	- $\displaystyle\sum_{i=1}^{1}i=1$
	- $\dfrac{1^2+1+2}{2}=2$


### Finding a formula

> Consider the following:
> $n=1:$      $1$                                      $1$             $1^2$
> $n=2:$      $1+3$                             $4$             $2^2$
> $n=3:$      $1+3+5$                    $9$             $3^2$
> $n=4:$      $1+3+5+7$           $16$          $4^2$

- While the Principle can't be used to come up with a new formula, it can be used to prove a formula that we create.

It looks like the value of $S(n)$ for each $n$ is the square of $n$. Prove that $S(n)=n^2$

- $2i+1$ denotes odd integers, but since 1 is included
	- $2(i-1)+1=2i-1$

$S(n):\displaystyle\sum_{i=1}^{n}(2i-1)=n^2$

- **Basis**
	- $S(1)$ is true
- **Induction**
	- Assume $S(k)$ is true
	- Must show $S(k+1)$ is true:  $\displaystyle\sum_{i=1}^{k+1}(2i-1)=(k+1)^2$
	- $\displaystyle\sum_{i=1}^{k+1}(2i-1)=\displaystyle\sum_{i=1}^{k}(2i-1)+[2(k+1)-1]$
				$=k^2+[2(k+1)-1]$
				$=k^2+2k+1$
				$=(k+1)^2$
- **Conclusion**
	- $S(n)$ is true for $n \in Z^+$


### Where the basis: $n\not =1$

> Consider the table:

| $n$ | $4n$ | $n^2-7$ |
| --- | ---- | ------- |
| $1$ | $4$  | $-6$    |
| $2$ | $8$  | $-3$    |
| $3$ | $12$ | $2$     |
| $4$ | $16$ | $9$     |
| $5$ | $20$ | $18$    |
| $6$ | $24$ | $29$    |
| $7$ | $28$ | $42$    |
| $8$ | $32$ | $57$    |
> When $n\geq 6$, it seems like $4n<(n^2-7)$
> Is it the case that for all $n\geq 6$, $4n<(n^2-7)$

$S(n):$      $4n<(n^2-7),n\geq 6$

- **Basis**
	- Starts from $6$
	- $S(6)$ is true from the chart above
- **Induction**
	- Assume $S(k)$ is true
	- Must show $S(k+1)$ is true: 
		- $4(k+1)<[(k+1)^2-7]$
			$\iff 4k+4<(k^2+2k+1-7)$
	- $S(k)$ being true gives us: 
		-  $4k < (k^2-7)$
			$\iff4k+4<(k^2-7)+4$ 
	- The right side of $S(k+1)$ and $S(k)$ are now very similar
		- We need the $2k+1$
		- Note that when $k\geq 6$,  $2k+1>4$
	- If we replace the $4$ with $2k+1$, this will make the expression bigger than before. It is still going to be bigger than the left side.
		- This will not work if it was an equality
		- So: $4k+4<(k^2-7)+(2k+1)$
			$\iff4k+4<(k^2+2k+1-7)$
- **Conclusion**
	- $\therefore S(n)$ is true for $n\geq6$


### Compositions

See [[Combinations with repetition#Compositions|Combinations with repetition]]

> For a given $n\in Z^+$, a composition of $n$ is an ordered sum of positive integers summing to $n$.
> All the different ways to write the integer $n$ as a sum of positive integers

| $n$   | $n=1$ | $n=2$        | $n=3$                            | $n=4$                                                                        |
| ----- | ----- | ------------ | -------------------------------- | ---------------------------------------------------------------------------- |
| Comp  | $1$   | $2$<br>$1+1$ | $3$<br>$1+2$<br>$2+1$<br>$1+1+1$ | $4$<br>$1+3$<br>$2+2$<br>$1+1+2$<br>$3+1$<br>$1+2+1$<br>$2+1+1$<br>$1+1+1+1$ |
| Total | $1$   | $2$          | $4$                              | $8$                                                                          |

> Prove that  $S(n)$:      $n$ has $2^{n-1}$ compositions for $n\in Z^+$.

- **Basis**
	- $S(1)$ is true by above
- **Induction**
	- Assume $S(k)$ is true: $k$ has $2^{k-1}$ compositions
	- Must show: $S(k+1)$: $k+1$ has $2^k$ compositions
	- We need to get a correspondence between the compositions of $k$ and $k+1$

Notice:

| $n=3$                            | $n=4$  $(3+1)$                           |
| -------------------------------- | ---------------------------------------- |
|                                  | $4$<br>$1+3$<br>$2+2$<br>$1+1+2$         |
| $3$<br>$1+2$<br>$2+1$<br>$1+1+1$ | $3+1$<br>$1+2+1$<br>$2+1+1$<br>$1+1+1+1$ |
Find a way to take the compositions of $3$ and build the compositions of $4$
- The 4 compositions of $3$:
	- adding 1 to the last integer of each one becomes the first 4 compositions of $4$
	- adding the "$+1$" to each one becomes the last 4 compositions of $4$

Compositions of $k+1$ fall into two categories:
- Where the last summand is an integer $t>1$ (i.e. the first 4 compositions of $4$):
	- replace the last summand with $t-1$ to get a correspondence to the compositions of $k$
- Where the last summand is a $1$ (i.e. the last 4 compositions of $4$):
	- remove the $+1$ to get a correspondence to the compositions of $k$

- The number of compositions of $k+1$ is twice the compositions for $k$
$\implies$ The number of compositions of $k+1=2(2^{k-1})=2^k$ 

- **Conclusion**
	- $\therefore S (n)$ is true for all $n\in Z^+$


> Notice that $14=3+3+8$. 
> This means $14$ can be written using only $3$'s and $8$'s as summands.
> 
> Prove that for all $n\geq 14$,
> $S(n):$      $n$ can be written as a sum of $3$'s and/or $8$'s (with no regard to order)

- **Basis**
	- $S(14)$ is true by the example
- **Induction**
	- Assume $S(k)$ is true for $k\geq 14$
	- Must show $S(k+1)$ 
	- Cases
		- **Case 1**: there is at least one $8$ in the sum for $k$
			- i.e. $k=\ldots+8+\ldots$
			- Replace the $8$ with $3\times 3$ to get $k+1$
			- i.e. $k+1 = \ldots+3+3+3+\ldots$
		- **Case 2**: there is no $8$ in the sum for $k$
			- i.e. $k=3+\ldots+3$
			- Since $k\geq 14$ there must be at least 5 $3$'s in the sum. 
				- The smallest number with only $3$'s above $14$ is $15$
			- Replace $5\times 3$ with $2\times 8$ to get $k+1$
	- We have shown $S(k)\implies S(k+1)$
- **Conclusion**
	- $S(k)$ is true for $n\geq 14$


---
## Alternate form (strong induction)

Let $n,n_0,n_1$ $\in Z^+$ with $n_0\leq n_1$

- If $S(n_0),S(n_0+1),S(n_0+2),\ldots,S(n_1)$ are true; and
- If whenever $S(n_0),S(n_0+1),\ldots,S(k-1)$, and $S(k)$ are true for some (particular but arbitrarily chosen) $k\in Z^+$, where $k \geq n_1$, then the statement $S(k+1)$ is also true;
- Then $S(n)$ is true for all $n\geq n_0$

### Example

> Using the alternate form, prove that for all $n\geq 14$,
> $S(n):$      $n$ can be written as a sum of $3$'s and/or $8$'s (with no regard to order)

- **Basis**
	- $S(14)$:      $14=3+3+8$
	- $S(15)$:      $15=3+3+3$
	- $S(16)$:      $16=8+8$
- **Induction**
	- Assume $S(14)$, $S(15)$, $S(16)$, $\ldots$, $S(k-2)$, $S(k-1)$, $S(k)$
	- From these assumptions, show that $S(k+1)$ is true
	- $k+1=(k-2)+3$
	- From the induction hypothesis, we know $S(k-2)$ is true, i.e., $k-2$ can be written only with $3$'s and $8$'s
	- Adding $3$ at the end, $k+1$ can be written using using $3$'s and $8$'s
- **Conclusion**
	- $S(n)$ is true for $n\geq14$


> [!info] Strong induction can sometimes be an easier proof. 


See more Strong induction examples in proving the [[1_Integer division#Lemma|Lemma]] and [[1_Integer division#Euclid's theorem|Euclid's theorem]]

