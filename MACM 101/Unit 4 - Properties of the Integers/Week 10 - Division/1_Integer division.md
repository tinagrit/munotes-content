Section 4.3

## Definition
For $a,b \in Z$ and $b \not = 0$, 
- $b$ divides $a$ or $b\mid a$
	- if there is an integer $n$, such that $a=bn$. 
	- or if $\frac{a}{b}$ is an integer
- $b$ is a **divisor** of $a$
- $a$ is a **multiple** of $b$

## "The Theorem"
For all $a$, $b$, $c$ $\in Z$

-  **a)** $1\mid a\land a\mid 0$
	- Any $Z^+$ can be divided by 1
	- 0 can be divided by any $Z^+$
-  **b)** $[(a\mid b)\land(b\mid a)]\implies a=\pm b$
	- If $\frac{a}{b}$ and $\frac{b}{a}$ are both integers, then $a$ and $b$ have the same magnitude
-  **c)** $[(a\mid b)\land(b\mid c)]\implies a\mid c$
	- eg. $4\mid 8$ and $8\mid 24$, then $4\mid 24$
-  **d)** $a\mid b\implies a\mid bx$   for all   $x\in Z$
	- eg. $5\mid 10$ and so $5\mid 20$, $5\mid 30$, $5\mid -40$, $\ldots$
-  **e)** If   $x=y+z$   for some   $x$, $y$, $z$ $\in Z$,   and $a$ divides two of the three integers $x$, $y$, $z$, then $a$ divides the remaining integer.
-  **f)** $[(a\mid b)\land(a\mid c)]\implies a\mid (bx+cy)$,   for all   $x$, $y$ $\in Z$
	- [[#Proof of theorem (f)|Proof below]]
-  **g)** For $1 \leq i \leq n$, let $c_i \in Z$.   If $a$ divides each $c_i$, then   $a\mid (c_1x_1+c_2x_2+\ldots+c_nx_n)$, where $x_i \in Z$ for all $1 \leq i \leq n$
	- eg. $4\mid 16$ and $4\mid 24$, then $4\mid (16+24)$
	- If $a$ each term, it must also divide the linear combination for all of them

### Proof of theorem (f)

> $[(a\mid b)\land(a\mid c)]\implies a\mid (bx+cy)$,   for all   $x$, $y$ $\in Z$

> [!info]
> The expression $bx+cy$ is called a **linear combination** of $b$, $c$

If $a\mid b$ and $a\mid c$, then we can write $b=am$ and $c=an$ for some $m,n \in Z$
Then $bx+cy=(am)x+(an)y$
			$=a(mx+ny)$

Since $mx+ny \in Z$, then $a\mid (bx+cy)$


### Example

> Do there exist integers $x$, $y$, $z$ (positive, negative, or zero) so that:
> $6x+9y+15z=107$

Notice: $3\mid 6$, $3\mid 9$, $3\mid 15$

By part **g)** of [[#"The Theorem"|the Theorem]], 
- if $3\mid 6$, $3\mid 9$, $3\mid 15$, 
- then $3\mid (6x+9y+15z)$ and $3\mid 107$

However, $3 \nmid 107$
So the integers $x$, $y$, $z$ do not exist.


> Let $a$, $b$ $\in Z$  so that $2a+3b$ is a multiple of $17$.
> Prove that $17$ divides $9a+5b$

Eg. $a=7$, $b=1$ then $2a+3b=17$

If we can multiply $(2a+3b)$ with an integer and make it $(9a+5b)$, it would be convenient. However, this doesn't work here.

Notice: $17\mid 17 \implies 17\mid (17a+17b)$ by part **f)** of [[#"The Theorem"|the Theorem]]

$17\mid (2a+3b)\implies 17\mid x(2a+3b)$  by part **d)** of [[#"The Theorem"|the Theorem]]

Choose the value of $x$ that helps us continue. ($x \in Z^+$)
- Above, in $(17a+17b)$, 
	- To get to $(9a+5b)$,
		- $a$ needs to be $-8$
		- $b$ needs to be $-12$
- Choose $x=-4$, then $17\mid -4(2a+3b)\implies 17\mid (-8a-12b)$

Since $17\mid (17a+17b)$ and $17\mid (-8a-12b)$
- $\implies 17\mid (9a+5b)$  by part **f)** of [[#"The Theorem"|the Theorem]]


---
## Prime numbers
For $n\in Z^+$ where $n>1$,
- $n$ is a **prime number**
	- if $n$ only has two divisors, $1$ and $n$
- $n$ is, otherwise, a **composite**.

> [!warning] 1 is not a prime number since 1 has only 1 divisor

Example:
- $13$ = prime
	- Divisors: $1$, $13$
- $24$ = composite
	- Divisors: $1$, $2$, $3$, $4$, $6$, $8$, $12$, $24$

> [!info]
> The only way to multiply 2 integers to make a prime number is
> $1\times \text{the prime number}$

Also see [[2_Greatest common divisor#Relatively prime numbers|Relatively prime numbers]]


### Lemma

See more: [[1_Arithmetic#Lemma Proof|Arithmetic Lemma Proof]]

> If $n\in Z^+$ and $n$ is composite, then there is a prime $p$ such that $p\mid n$
> "Every composite has a prime divisor"

**Prove by contradiction**
Similar to the [[1_Induction#Proof|proof of the Principle of Mathematical Induction]],
- Start by creating a set of all integers that violate the principle
- Show that the set is empty

Let set $S$ be the set of all composite numbers that have *no prime divisors*
Assume that $S \not = \varnothing$

Since $S \not = \varnothing$, by the [[1_Induction#The Well-Ordering Principle|Well-Ordering principle]], $S$ has a smallest element $m$

Since $m$ is a composite number, $m=m_1\cdot m_2$ 
- where $m_1, m_2 \in Z^+$ 
- and $1<m_1<m$ 
- and $1<m_2<m$
"$m$ can be written as two integers between $1$ and $m$ multiplied together"

$m_1$ and $m_2$ **cannot** be in $S$, since $m$ is the smallest element in $S$
- $m_1\not\in S\implies m_1$ is divisible by a prime number $p\mid m_1$
	- $m_1=px$ for some $x\in Z$

$m=m_1\cdot m_2$ 
$m=(px)\cdot m_2$

Since $m$ is a multiple of $p$, then $p\mid m$
However, $m$ can't have a prime divisor. 

There is a contradiction, and therefore the original conclusion is true.
$\therefore S=\varnothing$ 


> If $n \in Z^+$ and $n$ is composite
> Prove that there exists a prime $p$ such that $p\mid n$ and $p \leq \sqrt{n}$

Everything except the $p\leq \sqrt{n}$ has already been proven by the Lemma

Since $n$ is a composite number, $n=n_1\cdot n_2$ 
- where $n_1, n_2 \in Z^+$ 
- and $1<n_1<n$ 
- and $1<n_2<n$
"$n$ can be written as two integers between $1$ and $n$ multiplied together"

At least one of $n_1$ and $n_2$ have to be less than $\sqrt{n}$
- If not, then:
	- $n_1>\sqrt{n}$ and $n_2>\sqrt{n}$
	- and $n_1\cdot n_2 > \sqrt{n} \cdot \sqrt{n}$
	- and $n > n$
	- which is false

Without the loss of generality, assume $n_1 \leq \sqrt{n}$

If $n_1$ is prime, then $p=n_1$

However, if $n_1$ is composite, then 
- by the Lemma, there is a prime $p$ that divides $n_1$
- If $p\mid n_1$, also $p \mid n$

$\therefore p \mid n$ and $p \leq \sqrt{n}$


### Euclid's theorem

> There are infinitely as many primes
> "We can never find a max prime number"

**Prove by contradiction**

Assume that there is a *finite* number of prime
Let $p_1,p_2,p_3,\ldots,p_k$ be the finite list of all prime numbers

Let $B=p_1\cdot p_2\cdot p_3\cdot \ldots \cdot p_k+1$
(all of the prime numbers multiplied plus one)
Then $B>p_i$ for all $1\leq i \leq k$

Since $B$ is larger than anything in the list, $B$ is not in the list and thus not a prime number. 

Since $B$ is a composite number, by the Lemma, 
- there is a prime $p_j$ such that $p_j \mid B$
- $p_j$ is in the list $p_1,p_2,p_3,\ldots,p_k$

Since $p_j$ is in the list, $p_j$ can also divide the multiplication of everything in the list
- $p_j \mid p_1\cdot p_2\cdot p_3\cdot \ldots \cdot p_k$

$p_j \mid B$ and $p_j \mid p_1\cdot p_2\cdot p_3\cdot \ldots \cdot p_k$
- $\implies p_j \mid 1$ by part **e)** of [[#"The Theorem"|the Theorem]]

It is not possible to write an integer $\dfrac{1}{p_j}$ when $p_j$ is a prime number. 
This is a contradiction, and therefore the original conclusion is true.

$\therefore$ There are an infinite number of primes


---
## The Division Algorithm

If $a$, $b$ $\in Z$, with $b>0$
- then there exists unique $q$, $r$ $\in Z$ 
- $a=qb+r$,  $0\leq r < b$
- $\dfrac{a}{b}=q$  with a remainder of $r$

where
$q$ is the **quotient**
$r$ is the **remainder**
$b$ is the **divisor**
$a$ is the **dividend**

### Example

> When $a=170$ and $b=11$
- $170=15\cdot 11 + 5$
- $q=15$ and $r=5$

> When $a=98$ and $b=7$
- $98=14\cdot 7 + 0$
- $q=14$ and $r=0$

> When $a=-45$ and $b=8$
- $-45=-6\cdot 8 + 3$
- $q=-6$ and $r=3$

> [!info] Remainders cannot be negative
