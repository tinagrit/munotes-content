Lecture 4

## Pigeonhole Principle
*Read more at* [MACM 101 > Pigeonhole Principle](https://munotes.tinagrit.com/MACM101/unit-5-functions-and-relations/week-13-operations/2_pigeonhole-principle.html)

For [[1_Sets#Sets|sets]] $A$, $B$, if $|A| >|B|$, then for every [[2_Functions#Partial functions|total function]] $f:A\to B$, then there exists two different elements $a\in A$ that are mapped to the same element of $B$.

If there are **more pigeons** than there are holes, and every pigeon is in a hole, then there is **at least one hole** with more than one pigeon.


> A drawer contains red socks, green socks, and blue socks.
> If we pick a sock at random, how many socks do we take until we are guaranteed a matching pair?

We can let $A$ be the set of socks that we pick.
Let $B$ be the set of colours. In this case, $|B|=3$ for red, green, blue.

We can map each pick ($a \in A$) to a colour ($b \in B$) with a [[2_Functions#Functions|function]].

![[chart17.png|300]]

Using the Pigeonhole principle, to ensure that at least one colour is picked more than once (and therefore has a pair), we need $|A|>|B|$.

Since $|B|=3$, the smallest integer $>|B|$ is $3+1=4$.

Therefore, if we pick 4 socks, we are guaranteed a pair.


> Consider the set of integers:$$A=\left\{ 1,2,\dots, 100 \right\} $$
> Prove that there exists two numbers $a,b \in A$ such that $$(a-b) \text{ mod }41=0$$
> That is, there exists two numbers in the set whose difference is a multiple of 41.

Since $(a-b)\text{ mod }41=0$, we know that $(a-b)$ is a multiple of 41, and therefore:
$$
a-b=41k
$$
where $k\in \mathbb{Z}$. Moving $b$ to the right side, we get:
$$
a=b+41k
$$
This means that $a$ and $b$ are different by multiples of $41$. Therefore, if we divide $a$ and $b$ by $41$, they will have the same remainder. It follows that:
$$
a\text{ mod }41=b \text{ mod }41
$$

Now, if we divide an integer by $41$, the remainder can be anywhere from $\left\{ 0,1,\dots,40 \right\}$. We let $B$ be this set of integers.

Since $|A|=100$ (the original set), and we take out 2 elements $a,b \in A$, dividing each one by $41$, we can map each of the 100 elements to each possible remainder in $B$.

Since $|A|>|B|$, there must exist two numbers in $A$ that have the same remainder after dividing by $41$. 

Therefore, the theorem is true by the Pigeonhole Principle.

