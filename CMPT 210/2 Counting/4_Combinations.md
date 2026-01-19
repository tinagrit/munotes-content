Lectures 2-4

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
Using [[3_Permutations#Permutation|permutation]], we know that:
$$
|S|=n!
$$
Therefore,
$$
|A|=\dfrac{n!}{n}=(n-1)!
$$


### Combinations
The $k$-combination of a [[1_Sets#Sets|set]] $A$ is a [[1_Sets#Subsets|subset]] of $A$ with $k$ elements. Since the combination is a set, the **order does not matter**.

For example, for $A=\left\{ a,b,c \right\}$, all $2$-combinations include:
- $\left\{ a,b \right\}$, $\left\{ a,c \right\}$, $\left\{ b,c \right\}$

The total number of $k$-combinations for a set of size $n$ ($n$ *choose* $k$) is:
$$
\dbinom{n}{k}=\dfrac{n!}{k!\times(n-k)!}
$$

Deriving $n$ choose $k$ ($\binom{n}{k}$):
- Consider set $S=\left\{ a_{1},a_{2},a_{3},\dots,a_{n} \right\}$ with $n$ elements
- We are choosing $k$ elements from $S$, in this case $k <n$
$$
\underbrace{ a_{1},\text{ }a_{2},\text{ }a_{3},\text{ }\dots,\text{ }a_{k} }_{ k\text{ elements} },\text{ }\underbrace{ a_{k+1,}\text{ }\dots,\text{ }a_{n} }_{ n-k\text{ elements} }
$$
- We take the first part as the **subset** (combination), and the second part as the **leftover**
- Note that total number of [[3_Permutations#Permutation|permutations]] is $n!$, and combination is a permutation where order does not matter
- Using [[#Division Rule Counting|Division Rule]] to correct overcounting, divide the first part by $n!$, and the second part $(n-k)!$
- Therefore, the total number of combinations is:
$$
\dbinom{n}{k}=\dfrac{\dfrac{n!}{k!}}{(n-k)!}=\dfrac{n!}{k!\times (n-k)!}
$$


> Count the number of 5-digit numbers with at least one zero, that doesn't start with a 0. ($01234$ is invalid)

As the number needs to have **at least** one zero, we can add up cases where there is 1 zero, 2 zeroes, 3 zeroes, and 4 zeroes.

To find the number of cases where there are $i$ zeroes:
$$
\underbrace{ ? }_{ \text{9 options} }\text{ }\underbrace{ ?\text{ }?\text{ }?\text{ }? }_{ i\text{ spots to be zero} }
$$
- The first digit can be one of 9 options (zero excluded)
- For the rest 4 digits, choose $i$ spots to be zeroes $\dbinom{4}{i}$
- For each selection, the rest $4-i$ digits can each be one of 9 options (zero excluded)

Using the [[3_Permutations#Product Rule Counting|Product Rule]], the number of cases with $i$ zeroes is:
$$
9 \times \dbinom{4}{i}\times 9^{4-i}=\dbinom{4}{i}\times 9^{5-i}
$$

Using the [[2_Sum Rule#Sum Rule Counting|Sum Rule]], the total number of cases with $i$ ranging 1-4 is:
$$
\sum_{i=1}^{4}\dbinom{4}{i}\times9^{5-i}
$$


### Dice roll

> Consider rolling a 6-sided dice $n$ times. Count how many outcomes with exactly $g$ sixes.
> 
> An example of a valid set of sorted outcome where $n=10$, $g=4$. Each entry is a roll. $$\underbrace{ \underbrace{ 6,\text{ }6,\text{ }6,\text{ }6 }_{ g },\text{ }5,\text{ }3,\text{ }3,\text{ }2,\text{ }1,\text{ }1 }_{ n }$$
>  

Imagine we have $n$ spots for roll entries, we can use combinations to pick $g$ spots to place the sixes.
$$
\underbrace{ \underbrace{ 6,\text{ }6,\text{ }6,\text{ }6 }_{ g },\text{ }\underbrace{ ?,\text{ }?,\text{ }?,\text{ }?,\text{ }?,\text{ }? }_{ n-g } }_{ n }
$$
There are $n$ choose $g$ ($\dbinom{n}{g}$) ways to place this.

For each way, the remaining spots can be anything. Using the [[3_Permutations#Product Rule Counting|Product Rule]], we can choose one out of 5 (six excluded) faces in $n-g$ spots. There are $5^{n-g}$ ways of choosing.

The total number of outcomes is $\dbinom{n}{g}\times 5^{n-g}$

Derive the same result using the [[5_Binomial Theorem#Dice roll|Binomial Theorem]]


### Pascal's identity
For any integers $n,k$ such that $1 \leq k \leq n$,
$$
\dbinom{n}{k}=\dbinom{n-1}{k-1}+\dbinom{n-1}{k}
$$

Intuition proof:
The number of ways to choose $k$ students from $n$ students is $\dbinom{n}{k}$
Focusing on one student ($\text{a}$):
- Number of ways to select such that $\text{a}$ is **SELECTED** is $\dbinom{n-1}{k-1}$, since we are excluding $\text{a}$ from the selection ($n-1$), and that $\text{a}$ is already selected ($k-1$)
- Number of ways to select such that $\text{a}$ is **NOT SELECTED** is $\dbinom{n-1}{k}$, since we are excluding $\text{a}$ from the selection ($n-1$), and $\text{a}$ is not selected ($k$ to still be selected)

