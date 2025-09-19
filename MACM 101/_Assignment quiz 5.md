
## q1

![[Pasted image 20241202000246.png]]

- $\lfloor \dfrac{n}{5} \rfloor=-10$
	- $\implies -9 > \dfrac{n}{5} \geq -10$
	- $\implies -45 > n \geq -50$

- Since $n$ has a remainder of 4, by the Division algorithm
- $n=5q+r$
	- where $r=4$ and $q=-10$ due to the floor function above
	- $n=5(-10)+4=-46$

---
## q2

![[Pasted image 20241202001315.png]]

- A) 4 is not prime
- C) 1 is not prime
- D) 4 is not prime
Answer is B

---

## q3

![[Pasted image 20241202001838.png]]

Binary relations on $A=A\times A$

Number of binary relations is $2^{|A|\cdot|A|}$

$=2^{7\times 7}$
$=2^{49}$

---

## q4

![[Pasted image 20241202002145.png]]

- Since $A\subset B$ then $|A| < |B|$
- then $f:A\to B$ cannot be onto
- $f$ may or may not be one-to-one
- There is not enough elements in $A$ to point to each elements in $B$, which means $B$ must be greater than the range of $f$
- only $c)$ is true

---

## q5

![[Pasted image 20241202003100.png]]

Show that for each $b\in B$, 
Part 1: $b\in g(A_1 \cap A_2) \implies b\in g(A_1) \cap g(A_2)$
Part 2: $b\in g(A_1) \cap g(A_2) \implies b\in g(A_1 \cap A_2)$

### Part 1
- $b \in g(A_1 \cap A_2)$
- $\implies b= g(a)$ for some $a \in A_1 \cap A_2$
- $\implies [b= g(a)$ for some $a \in A_1]$  and  $[b= g(a)$ for some $a \in A_2]$
- $\implies b\in g(A_1)$ and $b\in g(A_2)$
- $\implies b\in g(A_1) \cap g(A_2)$

### Part 2
- $b \in g(A_1) \cap g(A_2)$
- $\implies b\in g(A_1)$ and $b \in g(A_2)$
- $\implies [b= g(a_1)$ for some $a_1 \in A_1]$ and $[b= g(a_2)$ for some $a_2 \in A_2]$
- Since $b=b$, It follows that $g(a_1)=g(a_2)$
- Since $g$ is one-to-one, $g(a_1)=g(a_2)\implies a_1=a_2$
- $\implies [b= g(a)$ for some $a \in A_1]$ and $[b= g(a)$ for some $a \in A_2]$
- $\implies b=g(a)$ for some $a\in A_1 \cap A_2$
- $\implies b \in g(A_1 \cap A_2)$

Since for each $b\in B$, 
$b\in g(A_1 \cap A_2) \iff b\in g(A_1) \cap g(A_2)$
Then $g(A_1 \cap A_2)=g(A_1) \cap g(A_2)$

---

## q6

![[Pasted image 20241202005939.png]]

Prove by contradiction. Assume that $p+1$ can be written as a perfect square where $p \geq 5$.

Since $p+1$ is a perfect square, there exists an $a\in Z$  such that $p+1=a^2$

$p+1=a^2$
$p=a^2-1$
$p=(a-1)(a+1)$

Since $a\in Z$, then $a-1,a+1 \in Z$

$p$ is multiple of $(a-1)$ and $(a+1)$
$\implies (a-1 \mid p)$ and $(a+1 \mid p)$

However, since $p$ is a prime number, it must follow that only $(1\mid p)$ and $(p\mid p)$
This implies that one of $(a-1)$ and $(a+1)$ should equal to $1$ and the other should equal to $p$.

|     Case 1<br>$a-1=1$ and $a+1=p$     |     Case 2<br>$a-1=p$ and $a+1=1$      |
| :-----------------------------------: | :------------------------------------: |
| $a=2$ and $a=p-1$<br>$2=p-1$<br>$p=3$ | $a=p+1$ and $a=0$<br>$p+1=0$<br>$p=-1$ |
|   $p$ cannot be 3 since $p \geq 5$    | $p$ cannot be -1 since -1 is not prime |

There is no such $a$ that can allow $a-1$ and $a+1$ to appropriately divide $p$

Since $a$ exists and does not exist, this is a contradiction, and therefore, the original conclusion is true.
$\therefore$ For all primes $p\geq 5$, $p+1$ is not a perfect square

