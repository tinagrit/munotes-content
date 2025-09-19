Section 5.5

## The Pigeonhole Principle
See [[Combinatorics Introduction|Counting]]

If there are $m$ pigeons who occupy $n$ pigeonholes
- and $m>n$
- then **at least one pigeonhole** has two or more pigeons

### Proof

**Prove by contradiction**
Assume that $m>n$, and that all pigeonholes can be filled with at most 1 pigeons in each hole.

Since there are at most 1 pigeons in each hole, all the holes can handle $n$ pigeons.

However, $n<m$, which means we are missing at least $m-n$ pigeons.


### Example

> If we have 3 people, 2 must be of the same gender
- Think of people as "*pigeons*" $=3$
- Think of genders as "*pigeonholes*" $=2$
- At least 2 people have the same genders

> If we have 13 people, at least two of them must be born in the same month
- Think of people as "*pigeons*" $=13$
- Think of months as "*pigeonholes*" $=12$
- At least 2 people were born in the same month

> Larry returns from the laundromat with 12 pairs of socks (each pair a different colour) in a laundry bag. If he draws the socks randomly from the bag, what is the most number of socks he must draw to get a matched pair?
- $13$
- If Larry is unlucky, the first 12 draws can be of different colours

> A tape contains 500,000 words of four or fewer lowercase letters. Can it be that they are all different?
- Find if it is possible to have 500,000 different words
- Counting problem, using [[Permutations#Permutations with repetition|permutations with repetition]]:
	- **Case 1:** 1 letter = $26$ choices
	- **Case 2:** 2 letters = $26\times 26$ = $26^2$ choices
	- **Case 3:** 3 letters = $26\times 26\times 26$ = $26^3$ choices
	- **Case 4:** 4 letters = $26\times 26\times 26\times 26$ = $26^4$ choices
	- All cases combined, by the [[Combinatorics Introduction#The Sum Rule|sum rule]], there are $26+26^2+26^3+26^4$ = $475,254$ different possible words
- $\therefore$ By the pigeonhole principle, there must be repeated words.

> Let $S \subset Z^+$ where $|S|=37$
> Then $S$ contains at least 2 elements that have the same remainder upon division by 36
- Think of all 37 integers in $S$ as "*pigeons*" $=37$
- By the [[1_Integer division#The Division Algorithm|division algorithm]], 
	- each $n\in S$ can be written as $n=36q+r$ with a unique $q$, $r$
	- Remainders can be $0\leq r < 36$
- Think of the maximum possible remainders as "*pigeonholes*" $=35$
- $\therefore$ at least two elements of $S$ have the same remainder

> Any subset of size 6 from the set $S=\{1,2,3,\ldots,9\}$ must contain at least two elements whose sum is 10
- The pairs of values that sum to 10 from $S$
	- $(1,9),(2,8),(3,7),(4,6)$
- When we form our 6 element [[Sets and Subsets#Subset|subset]], for no pair to sum to 10, we must choose only one integer from each pair, plus the single element $5$
- So there are 5 pigeonholes (numbers that no pairs add up to 10)
- There are 6 pigeons (elements required to form a 6 element subset)
- $\therefore$ The set $S$ must contain at least two elements whose sum is 10

