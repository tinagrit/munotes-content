Lecture 2

## Division Rule Counting

Consider a ***k-to-1*** [[2_Functions#Functions|function]] $f:A\to B$, where for each element in the codomain ($B$), there are exactly $k$ elements of the domain ($A$) being mapped to.

The following image is an example of a ***k-to-1*** function with $k=3$. Notice that we can find the [[1_Sets#Sets|cardinality]] of the domain ($|A|$) by multiplying $3$ to the cardinality of the codomain ($3 \times |B|$).

![[chart12.png|300]]

Therefore, generalizing this to all ***k-to-1*** functions, we have:
$$
|A|=k|B|
$$
It follows that:
$$
|B|=\dfrac{|A|}{k}
$$


> Consider a round table problem. Arrange $n$ people around a round table, and find how many possible arrangements.
> 
> Two seatings are **the same arrangement** if each person sits next to the same people.
> ![[chart13.png|300]]
> In this example, the following arrangements are the same:
> - $\left\{ \text{A}, \text{B},\text{C},\text{D},\text{E},\text{F},\text{G},\text{H}\right\}$
> - $\left\{  \text{B},\text{C},\text{D},\text{E},\text{F},\text{G},\text{H},\text{A}\right\}$
> - $\left\{ \text{C},\text{D},\text{E},\text{F},\text{G},\text{H},\text{A}, \text{B}\right\}$
> - *and 5 more*

Let:
- $S$ be the set of all possible seatings (permutations)
- $A$ be the set of circular arrangements

In the example above, notice that for one arrangement, there are 8 ways to write.
If we have $n$ seats, there would be $n$ ways to write.

Therefore, $n$ of the elements in $S$ map to one arrangement in $A$.
We have an $n$-to-1 function.

By the division rule, we have:
$$|A|=\dfrac{|S|}{n}$$
Using [[3_Product Rule#Permutation|permutation]], we know that:
$$
|S|=n!
$$
Therefore,
$$
|A|=\dfrac{n!}{n}=(n-1)!
$$
