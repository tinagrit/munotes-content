 Section 4.5

## Lemma Proof

See [[1_Integer division#Lemma|Lemma]]

> If $a,b\in Z^+$ and $p$ is prime, 
> then $p\mid ab \implies p\mid a$  or  $p\mid b$

^56a989

If $p\mid a$, we are done
If not, we have to show that $p\mid b$
- If $p \not \mid a$, then the [[2_Greatest common divisor#Greatest common divisor|GCD]]$(p,a)=1$
	- Since $p$ is prime, the only divisors of $p$ are $1,p$
- So we can write $1=px+ay$ for $x,y \in Z$.
	- See [[2_Greatest common divisor#Conclusion|proof of theorem]]
- Then $b\cdot 1 = b\cdot (px+ay)$
- $b=p(bx)+(ab)y$
	- $p$ divides both terms (notice that we assume $p\mid ab$)
		- by part **d)** of the [[1_Integer division#"The Theorem"|Theorem]]
- $\therefore p\mid b$  by part **e)** of the [[1_Integer division#"The Theorem"|Theorem]]


> Let $a_i \in Z^+$ for all $1\leq i \leq n$.
> If $p$ is prime and $p\mid a_1a_2\dots a_n$,
> then $p\mid a_i$ for some $1 \leq i \leq n$

By [[1_Induction#Principle of Mathematical Induction|Induction]],
- **Basis**
	- $n=1$
		- $p\mid a_1 \implies p\mid a_i$ for $i=1$
		- $S(1)$ is true
	- $n=2$
		- $p\mid a_1 \cdot a_2 \implies p \mid a_i$ for $1 \leq i \leq 2$
		- Follows from the [[#^56a989|proof above]]
- **Induction**
	- Assume $p\mid a_1\cdot a_2 \cdot \ldots \cdot a_k \implies p \mid a_i$ for some $1\leq i \leq k$
	- Consider $p\mid a_1 \cdot a_2 \cdot \ldots \cdot a_k \cdot a_{k+1}$
		- Let $z=a_1\cdot a_2 \cdot \ldots \cdot a_k$
		- Then $p \mid z \cdot a_{k+1} \implies p\mid z$ or $p \mid a_{k+1}$
		- Since $z$ is a multiplication of integers, this is the same case for $n=2$
	- $\implies p\mid a_1\cdot a_2 \cdot \ldots \cdot a_k$ or $p \mid a_{k+1}$
	- $\implies p \mid a_i$ for $1\leq i \leq k$ or $p \mid a_{k+1}$
	- $\implies p \mid a_i$ for $1 \leq i \leq k+1$
- Since $S(k) \implies S(k+1)$, $S(n)$ is true for all $n \in Z^+$
 

> Show that $\sqrt{2}$ is irrational

[[Sets and Subsets#Common infinite sets|Irrational]] = cannot be written as fraction, rational number

**Prove by contradiction**

Assume that $\sqrt{2}=\dfrac{a}{b}$ where $a,b \in Z^+$ and $gcd(a,b)=1$ (reduced fraction)

$\sqrt{2}=\dfrac{a}{b}$
- $\implies 2=\dfrac{a^2}{b^2}$
- $\implies 2b^2=a^2$
- $\implies 2 \mid a^2$
- $\implies 2 \mid a \cdot a$
- $\implies 2 \mid a$
	- Since $2$ is a prime number, $2\mid a \cdot a$ implies that $2\mid a$ or $2 \mid a$ by Lemma above
- $2\mid a \implies a=2c$ for some $c \in Z^+$
- So from $2b^2=a^2$
- $\implies 2b^2=(2c)^2$
- $\implies 2b^2=4c^2$
- $\implies b^2=2c^2$
	- Since we can write $b^2=2\cdot\text{integer}$,
	- then $2 \mid b^2$
	- then $2 \mid b$ by Lemma above
- We have shown that $2 \mid a$ and $2 \mid b$.
- Then, $gcd(a,b) \geq 2$, a contradiction

This means that $\sqrt{2}$ doesn't have a reduced fraction, while all rational numbers do.

The original conclusion, that $\sqrt{2}$ is irrational, is true.


## Theorem of Arithmetic

Every positive integer $n>1$ can be written **uniquely** as the **product of [[1_Integer division#Prime numbers|prime numbers]]**, where the prime factors are written in order of increasing size.

> [!info] This is used in encryption

Example:
- $15=3\cdot 5$
- $48=2\cdot 2\cdot 2\cdot 2\cdot 3 = 2^4 \cdot 3$
- $17=17$
- $100=2\cdot 2\cdot 5\cdot 5=2^2\cdot 5^2$

### Partial proof of theorem

> Prove the existence of a prime factorization
> Leave the uniqueness of it as a separate proof

**Prove by contradiction**
Similar approach to [[1_Induction#Proof|Induction Proof]] where a [[Sets and Subsets#Sets|set]] of all violating integers is assumed to be not empty.

Let $S=\{x\mid x\in Z^+,x>1,x$ cannot be written as a prime factorization$\}$
Assume that $S\not = \varnothing$
By the [[1_Induction#The Well-Ordering Principle|Well-Ordering principle]], $S$ has a smallest element $m$ 

Since $m$ is not prime, we can write $m=m_1 \cdot m_2$ 
- where $1<m_1<m$ and $1<m_2<m$

Since $m_1$ and $m_2$ are smaller than $m$,
- They are not in the set $S$
- and therefore they can be written as prime factorizations

$\therefore m=m_1\cdot m_2$ can also be written as prime factorization by combining the prime factorizations of $m_1$ and $m_2$, a contradiction

The original conclusion, that $m$ can be written as prime factorization, is true.

### Example

> Suppose that $n \in Z^+$ and that
> $10\cdot 9\cdot 8\cdot 7\cdot 6\cdot 5\cdot 4\cdot 3\cdot 2\cdot n=21\cdot 20\cdot 19\cdot 18\cdot 17\cdot 16\cdot 15\cdot 14$
> Show that $17 \mid n$

Notice that $17$ is on the right, 
- which means the right side is a multiple of $17$.
- $17$ is a **prime** factor of the right side
- $17$ must be a prime factor of the left by the uniqueness part of the Fundamental Theorem of Arithmetic
- Since $17$ does not divide $10,9,8,\ldots,2$, so it follows that $17\mid n$


## Pi notation
similar to [[Combinations with no repetition#Summation Notation|Sigma notation]], but for multiplications.

Example:

- $\displaystyle\prod_{i=1}^{6}{x_i}=x_1\cdot x_2\cdot x_3\cdot x_4\cdot x_5\cdot x_6$

-  $\displaystyle\prod_{i=3}^{6}{i}=3\cdot 4\cdot 5\cdot 6$

 - $\displaystyle\prod_{i=m}^{n}{i}=m\cdot(m+1)\cdot(m+2)\cdot\ldots\cdot(n-1)\cdot n=\dfrac{n!}{(m-1)!}$

