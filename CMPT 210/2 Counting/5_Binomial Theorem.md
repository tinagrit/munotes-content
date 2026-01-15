Lecture 3

## Sum of Combinations Theorem
*Expands* [[4_Combinations#Combinations|Combinations]]

> Consider an $n$-bit binary sequence, for example, $000100010111$.
> How many sequences have less than $k$ ones?

Imagine an all 0 sequence, there are $n$ spots for ones to be placed on. We are counting all combinations of no ones, $1$ one, $2$ ones, $3$ ones, $\dots$, $k-1$ ones.

Using the [[2_Sum Rule#Sum Rule Counting|Sum Rule]], the number of sequences is:
$$
\dbinom{n}{0}+\dbinom{n}{1}+\dbinom{n}{2}+\dots+\dbinom{n}{k-1}=\sum_{i=0}^{k-1}\dbinom{n}{i} 
$$

> How many sequences have at least $k$ ones?

Now, we are counting all combinations of $k$ ones, $k+1$ ones, $k+2$ ones, $\dots$, $n$ ones.

Using the [[2_Sum Rule#Sum Rule Counting|Sum Rule]], the number of sequences is:
$$
\dbinom{n}{k}+\dbinom{n}{k+1}+\dbinom{n}{k+1}+\dots+\dbinom{n}{n}=\sum_{i=k}^{n}\dbinom{n}{i} 
$$

> How many sequences in total?

Using the [[3_Permutations#Product Rule Counting|Product Rule]], each bit can be one of two ways $(0,1)$, and therefore the total number of sequences is: $2^{n}$.

The total number of sequences can also be written as:
Sequences with $<k$ ones $+$ Sequences with $\geq k$ ones

Using the results from above, it follows that:
$$
\sum_{i=0}^{k-1}\dbinom{n}{i} +\sum_{i=k}^{n}\dbinom{n}{i}
$$
$$
\implies \sum_{i=0}^{n}\dbinom{n}{i} =2^{n}
$$


## Binomial Theorem

The binomial theorem easily **expands powers** of a binomial in the form of:
$$
(x+y)^{n}
$$
where $n \in \mathbb{N}$ and $x,y \in \mathbb{R}$.

$$
(x+y)^{n}=\sum_{k=0}^{n}\dbinom{n}{k}x^{k}y^{n-k}
$$
$$
=\dbinom{n}{0}y^{n}+\dbinom{n}{1}xy^{n-1}+\dbinom{n}{2}x^{2}y^{n-2}+\dots+\dbinom{n}{n}x^{n}
$$


> Expanding $(2a+b)^{3}$, what is the coefficient of the term $a^{2}b$?

Since the binomial is to the power of $3$, we have $n=3$
Using the binomial theorem, 
$$
(2a+b)^{3}=\sum_{k=0}^{n}\dbinom{n}{k}(2a)^{k}(b)^{n-k} 
$$

To get the term $a^{2}b$, we need $k=2$

$$
\sum_{k=0}^{n}\dbinom{n}{k}(2a)^{k}(b)^{n-k} =\sum_{k=0}^{n}\dbinom{n}{k}\times 2^{k}a^{k}b^{n-k} 
$$

Notice that the coefficient is $\dbinom{n}{k}\times 2^{k}$

The result is $\dbinom{3}{2}\times 2^{2}=3\times 4=12$


### Dice roll
*Extension of* [[4_Combinations#Dice roll|Combinations Dice Roll]]

>Consider rolling a 6-sided dice $n$ times. Count how many outcomes with exactly $g$ sixes.

Rolling a die $n$ times, the total number of all possible outcomes is $6^{n}$ (six sides, using the [[3_Permutations#Product Rule Counting|Product Rule]]). This can be written as a binomial as:
$$
6^{n}=(1+5)^{n}
$$

Using the Binomial Theorem with $x=1$ and $y=5$, we get:
$$
(1+5)^{n}=\sum_{k=0}^{n}\dbinom{n}{k}1^{k}5^{n-k}=\sum_{k=0}^{n} \dbinom{n}{k}5^{n-k} 
$$

The Binomial Theorem has broken down the $6^{n}$ outcomes into groups based on how many sixes appear.
- The first term has $0$ sixes ($k=0$)
- The second term has $1$ six ($k=1$)
- The third term has $2$ sixes ($k=2$)
- $\dots$
- The last term has $n$ sixes ($k=n$)

To find the outcomes where $g$ sixes appear, use the term where $k=g$. We have the total outcomes to be
$$
\dbinom{n}{g}5^{n-g}
$$
, which is exactly equal to the [[4_Combinations#Dice roll|result]] we obtained earlier.

