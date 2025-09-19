Section 4.4

## Common divisor
For $a$, $b$ $\in Z$,  
- $c \in Z^+$ is said to be a **common [[1_Integer division#The Division Algorithm|divisor]]** of $a$ 
	- if $c\mid a$ and $c\mid b$

Example: For $48$ and $72$
Common divisors: $1$, $2$, $3$, $4$, $6$, $8$, $12$, $24$

## Greatest common divisor
For $a$, $b$ $\in Z$,  where either $a\not= 0$ or $b \not = 0$. (At least one of $a$, $b$ is a non-zero integer)
- $c\in Z^+$ is called a **greatest common divisor** of $a$, $b$ 
	- if $c\mid a$ and $c\mid b$ and
	- for any common divisor $d$ of $a$ and $b$ we have $d\mid c$
- Denoted by $gcd(a,b)$

In the example above, $1$, $2$, $3$, $4$, $6$, $8$, $12$ are all divisors of $24$. Therefore, $24$ is the $gcd(48,72)$

Example: $gcd(19,72)=1$

### Theorem

> For all $a$, $b$ $\in Z^+$ 
> Prove that there exists a unique $c \in Z^+$ that is the greatest common divisor of $a$, $b$
> Prove that the greatest common divisor exists

Given $a,b \in Z^+$ let $S=\{as+bt\mid s,t\in Z \land as+bt >0\}$ 
$S$ is the set of positive [[1_Integer division#Proof of theorem (f)|linear combinations]] of $a$ and $b$

Since $S\not = \varnothing$, by the [[1_Induction#The Well-Ordering Principle|Well-Ordering principle]], the set $S$ has a smallest element $c$.

Claim: $c$ is the greatest common divisor of $a$, $b$
Since $c\in S$,
- $c=ax+by$ for some $x,y \in Z$

Must prove that
- **Part 1**:  $c\mid a$ and $c\mid b$
- **Part 2**:  $c$ is a greatest common divisor
- **Part 3**:  $c$ is the *only* greatest common divisor

#### Part 1
$c\mid a$ and $c\mid b$
**Prove by contradiction**

Assume that $c \nmid a$
By the [[1_Integer division#The Division Algorithm|division algorithm]], we can write $a=qc+r$ with
- $q,r\in Z^+$
- $0<r<c$
	- Remainder can't be 0 because $c$ is not evenly dividing $a$

Then $r=a-qc$
Since $c=ax+by\implies r=a-q(ax+by)$

$\implies r=(1-qx)a+(-qy)b$

Since $r$ is a [[1_Integer division#Proof of theorem (f)|linear combination]] of $a$ and $b$, then $r$ is in the set $S$
However, $r<c$ and $c$ is the smallest element, so $r$ can't be in $S$

This is a contradiction, and therefore, the original conclusion is true.
$\therefore$ $c \mid a$

By similar argument, also $c\mid b$

#### Part 2
$c$ is a greatest common divisor

Show that any other common divisor would divide $c$

By part **f)** of the [[1_Integer division#"The Theorem"|Theorem]],
If $d\in Z$ and $d\mid a$ and $d\mid b$, then $d\mid(ax+by)$ 
Since $c=ax+by$,
$\implies d\mid c$

$\therefore c$ is a greatest common divisor 


#### Part 3
$c$ is the *only* greatest common divisor

If $c_1,c_2$ are both $gcd$'s, then by definition:
- Any other divisors divide the greatest common divisor
- $c_1 \mid c_2$
- $c_2 \mid c_1$

By part **b)** of the Theorem,
- $c_1=c_2$
 It is not $\pm c_2$ since we have established that $S$ can only contain positive integers

$\therefore c$ is unique 

#### Conclusion
$\therefore$ For all $a,b\in Z^+$, a $gcd$ exists and is unique

> [!note]
> From the proof, we have also shown that
> 
> If $d\mid a$ and $d \mid b$, 
> - We can write $d$ as a linear combination of $a$ and $b$
> - i.e., $d=ax+by$ for some $x,y\in Z$


### Relatively prime numbers
See [[1_Integer division#Prime numbers|Prime numbers]]
Two integers $a$ and $b$ are **relatively prime** if $gcd(a,b)=1$
This also means that $a \not \mid b$

> Are $15$ and $28$ relatively prime?

$gcd(15,28)=1$
$\therefore 15$ and $28$ are relatively prime 

> Are $55$ and $28$ relatively prime?

$gcd(28,55)=1$
$\therefore 28$ and $55$ are relatively prime

> Are $35$ and $28$ relatively prime?

$gcd(28,35)=7$
$\therefore 28$ and $35$ are *not* relatively prime


## Least common multiple
The smallest positive integer that is divisible by both $a$ and $b$
- Denoted by $lcm(a,b)$

Example:
- $lcm(3,4)=12$
- $lcm(5,10)=10$
