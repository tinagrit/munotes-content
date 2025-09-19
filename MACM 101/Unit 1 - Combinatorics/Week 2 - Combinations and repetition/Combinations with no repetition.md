
> How many different sets of 3 people can we pick from a group of 6

Picking people using [[Permutations]], there would $P(6,3)=120$ ways to do this.

However, by choosing from **{A,B,C,D,E,F}**, **{A,C,E}** and **{C,A,E}** are the equivalent choices.

The above solution is **incorrect** since order doesn't matter.

The correct number of ways is $C(6,3)=20$ ways

---
### Calculating combinations

For $n$ distinct objects, the number of combinations of $r$ objects is denoted $C(n,r)$.

For each unique combination, there are $r!$ equivalent orderings.
$P(n,r)=C(n,r)*r!$

$C(n,r)=\dfrac{P(n,r)}{r!}$

$C(n,r)=\dfrac{n!}{r!(n-r)!}$ , $0\leq r \leq n$

Also denoted $\displaystyle{n \choose r}$

> Note that $C(n,r) = C(n,n-r)$

---
### Examples

> A soccer club has 8 female and 7 male members. For today's match, the coach wants to have 6 female and 5 male players on the grass. How many possible configurations are there?

$C(8,6)$ ways to choose the female players
$C(7,5)$ ways to choose the male players

Two choices are made one after another. See [[Combinatorics Introduction#The Product Rule]] 

$C(8,6)*C(7,5)$ = $\dfrac{8!}{6!*2!}*\dfrac{7!}{5!*2!}$ = $588$ ways to form the team


> A student taking a history exam chooses to answer 7 out of 10 essay questions. How many ways can the student choose the question to answer?

$\displaystyle{10\choose7} = \dfrac{10!}{7!*3!}$ ways 

> What if the student must answer 3 questions from the first five, and 4 questions from the last five?

- There are $5\choose3$ ways to choose 3 out of the first five
- There are $5\choose4$ ways to choose 4 out of the last five

$\displaystyle {5 \choose 3}*{5 \choose 4}=50$ ways

> What if the student must answer 7 out of the 10 questions where at least three are selected from the first five?

- **CASE 1**
	- choosing 3 out of the *first* five
	- choosing 4 out of the *last* five
	- $\dbinom{5}{3}*\dbinom{5}{4}=50$ ways

- **CASE 2**
	- choosing 4 out of the *first* five
	- choosing 3 out of the *last* five
	- $\dbinom54*\dbinom53=50$ ways

- **CASE 3**
	- choosing 5 out of the *first* five
	- choosing 2 out of the *last* five
	- $\dbinom55*\dbinom52=10$ ways

The three cases **are not** done one after the other, the [[Combinatorics Introduction#The Sum Rule|sum rule]] is used.

The total number of ways is $50+50+10=110$ ways.


> What is the total number of arrangements in the letters in **TALLAHASSEE**?
- There are:
	- 3 A's
	- 2 L's
	- 2 S's
	- 2 E's
- Using [[Permutations#Permutations with indistinguishable objects]], the total number of arrangements is $\dfrac{11!}{3!*2!*2!*2!}=831,600$ ways

> How many of these arrangements have no adjacent A's
> This is different than asking how many of these have four A's all together.
- **Disregarding the A's**:
	- the number of arrangements is $\dfrac{8!}{2!*2!*2!}=5,048$ ways
- **Putting the A's back**:
	- The string now looks like this:
		`E  E  S  T  L  L  S  H`
		The A's that are to be inserted cannot be adjacent to each other
	- There are 9 spaces that A's can go to. Since there are 3 A's, we need to select 3 locations out of 9 locations.
	- The number of ways that A can go to is $\binom93=84$ ways
- For each arrangement of the word without the A's, there are 84 ways to arrange the A's
- The total number of ways to arrange this is $5040*84=423,360$ ways

---

### Summation Notation
$a_m+a_{m+1}+a_{m+2}+...+a_{m+n}$ = $\displaystyle\sum_{i=m}^{m+n}a_i$

Also see [[1_Arithmetic#Pi notation|Pi notation]]

---

### The Binomial Theorem

$(x+y)^{n}$ 

= $\displaystyle{n\choose0}x^0y^n+{n\choose1}x^1y^{n-1}+...+{n\choose{n-1}}x^{n-1}y^1+{n\choose{n}}x^ny^0$ 

= $\displaystyle\sum_{k=0}^{n}{n\choose{k}}x^ky^{n-k}$ 

or can be written as  $\displaystyle\sum_{k=0}^{n}{n\choose{n-k}}x^ky^{n-k}$ since $C(n,r) = C(n,n-r)$


> What is the coefficient of $x^5y^2$ in the expansion of $(x+y)^7$?

- $n$ (the exponent) = $7$
- $k$ (the exponent of $x$) = $5$

- The coefficient is $\dbinom{7}{5}=21$

#### Corollaries
- Proving that $\displaystyle{n\choose0}+{n\choose1}+{n\choose2}+...+{n\choose{n}}=2^n$
	- In the Binomial Theorem, when $x=1$ and $y=1$
	- This is equivalent to $(1+1)^n=2^n$
	- According to the formula:
		$\displaystyle2^n={n\choose0}\cdot1^0\cdot1^n+{n\choose1}\cdot1^1\cdot1^{n-1}+...+{n\choose{n}}\cdot1^n\cdot1^0$
		$\displaystyle2^n={n\choose0}+{n\choose1}+...+{n\choose{n}}$

- $\displaystyle{n\choose0}-{n\choose1}+{n\choose2}-...+(-1)^n{n\choose{n}}=0$
	- Use $x=-1$, $y=1$ in the Binomial Theorem 


---

### Examples

> An alphabet defines the symbols in a language. Strings are formed from these alphabets.
> If we have a string $x=x_1x_2x_3\ldots x_n$ then the weight of $x$ is defined as $wt(x)=x_1+x_2+x_3+\ldots+x_n$
> Consider the alphabet $0$, $1$, $2$ and $\text{length}=3$, then $wt(101)=2$, $wt(210)=3$, $wt(222)=6$
> How many different strings of length 10 are there for the above alphabet?

Order matters, so this is **PERMUTATION** where repetition is allowed.
Using the formula from [[Permutations#Permutations with repetition]],
the total number of strings is $n^r=3^{10}$ strings.

> Among these strings of length 10, how many have even weight?
- The string has even weight when the number of 1's in the string is even *(including zero)*.
- **CASE 1**: No 1's
	- Choosing between 0 and 2 for 10 digits
	- Total number of ways is $2^{10}$ strings
- **CASE 2:** Two 1's
	- Choosing between 0 and 2 for 8 digits
		- There are $2^8$ ways to arrange
	- Choosing the locations for the two 1's
		- There are $\dbinom{10}{2}=45$ ways to put in the 1's
	- The total number of ways is $45*2^8$ strings
- **CASE 3:** Four 1's
	- The total number of ways is $\dbinom{10}{4}*2^6=210*2^6$ strings
- 
- 
- 

Using the sum rule:

$\displaystyle{10\choose0}2^{10}+{10\choose2}2^8+{10\choose4}2^6+{10\choose6}2^4+{10\choose8}2^2+{10\choose{10}}2^0$

= $\displaystyle\sum_{n=0}^{5}{10\choose{2n}}2^{10-2n}$

---

### The Multinomial Theorem

For positive integers $n$, $t$, the coefficient of $x_1^{n1}x_2^{n2}x_3^{n3}\ldots x_t^{nt}$ in the expansion of $(x_1+x_2+x_3+\ldots+x_t)^n$ is
$$\dfrac{n!}{n_1!n_2!n_3!\ldots n_t!}=\dbinom{n}{n_1,n_2,n_3,\ldots,n_t}$$
where each $n_i$ is an integer with $0\leq n_i\leq n$, for all $1\leq i\leq t$, and $n_1+n_2+\ldots+n_t=n$.

> What is the coefficient of $x^2y^2z^3$ in the expansion of $(x+y+z)^7$?
- $n=7$
- $\dbinom{7}{2,2,3}=\dfrac{7!}{2!\cdot2!\cdot3!}=210$
