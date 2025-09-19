>"In a class of 10 students, 5 are to be chosen and seated in a row for a picture. How many such linear arrangements are possible?"

| Possibilities |   10    |    9    |    8    |    7    |    6    |
| :-----------: | :-----: | :-----: | :-----: | :-----: | :-----: |
|   Position    | 1st pos | 2nd pos | 3rd pos | 4th pos | 5th pos |
- A single person cannot be chosen twice
- Using [[Combinatorics Introduction#The Product Rule]], the total combination is $10*9*8*7*6$ or $\dfrac{10!}{5!}$ (see [[#Permutations with no repetition]])

---

A permutation of a set of $n$ distinct objects is an ordered arrangement of these object.

For an **integer** $n\geq0$, $n$ factorial (denoted $n!$) is defined by
$0!=1$
$n!=(n)(n-1)(n-2)...(3)(2)(1)$, for $n\geq1$

### Permutations with no repetition
- *Cannot* choose the same object again
- The number of ways to arrange $r$ with ($0\leq r\leq n$) objects from a set of $n$ objects, in order, but no repetition allowed is
	$P(n,r)$  $=n·(n - 1)·(n - 2)···(n - r + 1)$
		    $=\dfrac{n!}{\left(n-r\right)!}$

### Permutations with repetition
- Can choose the same object more than once
- The number of ways to arrange is $n^r$

---

### Examples

- "What are the permutations of the letters in the word ***COMPUTER*** ?"
	- $n=8$, $r=8$
	- $P(8,8)=\dfrac{8!}{(8-8)!}$
	- $=8!$

- "If only 5 letters are used from the above, what is the number of permutations?"
	- $n=8$, $r=5$
	- $P(8,5)=\dfrac{8!}{(8-5)!}$
	- $=\dfrac{8!}{3!}$

- "If repetition of letters ***ARE*** allowed, how many 12-letter sequences are possible using the letters above?"
	- $n=8$, $r=12$
	- $=8^{12}$

- "If every phone number was used in the Lower Mainland, how many individual numbers would there be?"
	- The first number of a 7-digit phone number can not be a 0 or 1. Also there are currently 2 area codes, 604 and 778.
	- Procedure
		- 2 choices of the area code
		- 8 choices (2-9) for the third digit
		- 10 choices for the digits 4-10
	- $2*8*10^6=16,000,000$

- Suppose a new area code were made available in the Lower Mainland, area code 603, how many new phone numbers could be issued?
	- $8*10^6=8,000,000$



---

### Permutations with indistinguishable objects

- $\dfrac{n!}{n_1!*n_2!*...*n_k!}$ where $n_1+n_2+...+n_k=n$

- "How many different strings can be made reordering the word **BALL** ?"
	- Formulae don't apply since the two Ls are not distinct from each other; there are only 3 distinct objects
	- Assuming 4 distinct letters $B$,$A$,$L_1$,$L_2$ then $n=4$, $r=4$. There would be $4!$ combinations
		- For each arrangement of $B$,$A$,$L_1$,$L_2$ there is an equivalent arrangement where the $L_1$ and $L_2$ are reversed.
	- (# of permutations of $B$,$A$,$L_1$,$L_2$ ) = $2*$(# of permutations of $B$,$A$,$L$,$L$)
	- Therefore, the number of arrangements of $B$,$A$,$L$,$L$ is $\dfrac{24}{2}=12$

- "How many different strings can be made reordering the letters in the word **DATABASES**?"
	- Procedure
		- 3 A's
		- 2 S's
		- 1 of each other letter
	- $\dfrac{9!}{3!*2!*1!*1!*1!*1!}=\dfrac{9!}{3!*2!}$ is total combinations

- By rearranging **MASSASAUGA**, how many different strings can be made when the 4 A's are all together.
	- All possible strings:
		$\dfrac{10!}{4!*3!*1!*1!*1!}=25,200$
	- To find permutations when all A's are together, the 4 A's are considered to be ***1 single symbol*** *(AAAA)*
		$\dfrac{7!}{3!*1!*1!*1!}=840$
	

#### Non-linear arrangements
>Six people, designated as A, B, C, D, E, F, are seated about a round table. How many different circular arrangements are possible, where it doesn't count when one can be obtained from the other by rotation?

-  **APPROACH 1**
	- For each linear arrangement, there are 6 arrangements that are identical circularly. 
		- For example, **ABCDEF** and **EFABCD** are the same when being rotated.
	- The total linear arrangements is $P(6,6)=6!$
	- Since there are 6 linear arrangements that make up one circular arrangement, the total circular arrangement is  $\dfrac{6!}{6}=5!$
- **APPROACH 2**
	- If one person if fixed at one spot, all the possible permutations of the rest will be unique circularly.
	- **A** is fixed at one spot, the permutations for the rest is $P(5,5)=5!=120$

> From the six people, there are 3 males and 3 females. How many ways are there to arrange so that sexes alternate?

-  Assume A is a female, she is fixed at one spot. The arrangement will be:
		- $A,m,f,m,f,m$
- Procedure
		- 1 choice for the first position (A only)
		- 3 choices for the second position
		- 2 choices for the third position
		- 2 choices for the fourth position
		- 1 choice for the fifth position (last female)
		- 1 choice for the sixth position (last male)
- The total permutations is $1*3*2*2*1*1=12$ ways

