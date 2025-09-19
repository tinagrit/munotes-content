Section 5.2-5.3

## Functions

For the function or mapping $f:A\to B$,
- $A$ is called the **domain** of $f$
- $B$ is called the **codomain** of $f$

All elements of $A$ has to **point to somewhere** in $B$ exactly once

When $(a,b)$ is an ordered pair in the function $f$:
- We can write $f(a)=b$
- $b$ is the **image** of $a$
- $a$ is the **preimage** of $b$

Example:
> $A=\{1,2,3\}$ and $B=\{w,x,y,z\}$
- $T_1=\{(1,w),(2,x),(3,x)\}$
	- is a function from $A$ to $B$
- $T_2=\{(1,w),(2,x)\}$
	- is *not* a function from $A$ to $B$
	- since not all elements of $A$ appear exactly once (3 is missing)
- $T_3=\{(1,w),(2,w),(2,x),(3,z)\}$
	- is *not* a function from $A$ to $B$
	- since not all elements of $A$ appear exactly once (2 is mapped twice)

The **range** of $f$ or $f(A)$ is
- the [[Sets and Subsets#Subset|subsets]] of $B$ consisting of those elements that appear as second components in the ordered pairs of $f$

> For
> - $A=\{1,2,3\}$
> - $B=\{w,x,y,z\}$
> - $f=\{(1,w),(2,x),(3,x)\}$

- Domain of $f$ = $A$ = $\{1,2,3\}$
- Codomain of $f$ = $B$ = $\{w,x,y,z\}$
- Range of $f$ = $\{w,x\}$

### Floor function
$f:R\to Z$ is defined as
- $f(x)=\lfloor x \rfloor$
- The greatest integer less than or equal to $x$
- The floor of a real number is an integer *just below* that number

Example: 
- $\lfloor 3.8 \rfloor=3$
- $\lfloor -3.8 \rfloor = -4$
- $\lfloor -3 \rfloor = -3$


### Ceiling function
$g:R\to Z$ is defined as
- $g(x)=\lceil x \rceil$
- The least integer greater than or equal to $x$
- The ceiling of a real number is an integer *just above* that number

Example:
- $\lceil 3.01 \rceil=4$
- $\lceil -3.01 \rceil=-3$
- $\lceil -3.7 \rceil=-3$


### Truncation function
returns the integer part of a real number
- write the real number as decimals and *cut off* everything after the integer

Example:
- $trunc(3.78)=3$
- $trunc(-7.22)=-7$
- $trunc(-3)=-3$


### Counting number of functions
For the general case, let $A,B$ be nonempty sets
- $|A|=m$, $|B|=n$.
- I.e. $A=\{a_1,a_2,a_3,\ldots,a_m\}$ and $B=\{b_1,b_2,b_3,\ldots,b_n\}$

A typical function $f:A\to B$ can be described by:
- $\{(a_1,x_1),(a_2,x_2),(a_3,x_3),\ldots,(a_m,x_m)\}$.

Number of choices for $x_1$ to map: $n$
Number of choices for $x_2$ to map: $n$
...
Number of choices for $x_m$ to map: $n$

By the [[Combinatorics Introduction#The Product Rule|Product rule]], there are $n^m=|B|^{|A|}$ functions from $A$ to $B$ 


## One-to-one functions
A function $f:A\to B$ is called **one-to-one**, or **injective**, 
- if each element of $B$ appears **at most once** 
	- as the image of an element of $A$.

If $f:A\to B$ is one to one, with $A,B$ finite, 
- we must have $|A| \leq |B|$.
- since every element of $A$ has to map somewhere

If $f:A\to B$ is one to one,
- for $a_1,a_2\in A$,
	- $f(a_1)=f(a_2)\implies a_1=a_2$


> Consider the function $f:R\to R$ where $f(x)=3x+7$
> Is $f$ one-to-one?

$f(x_1)=f(x_2)$
$\implies 3x_1+7=3x_2+7$
$\implies 3x_1=3x_2$
$\implies x_1=x_2$

$\therefore f$ is one-to-one (1-1)


>Is $g$ in $g:R\to R$ where $g(x)=x^4-x$ one-to-one?

Is it possible that if $f(x_1)=f(x_2)$ then $x_1 \not = x_2$?

Example: 
- $g(0)=0^4-0=0$
- $g(1)=1^4-1=0$
Then $g(0)=g(1)$ but $0 \not = 1$, so $g$ is *not* one-to-one.


### Counting number of one-to-one functions
With $A=\{a_1,a_2,a_3,\ldots,a_m\}$ and $B=\{b_1,b_2,b_3,\ldots,b_n\}$
- One-to-one function $f:A\to B$ has the form
	- $\{(a_1,x_1),(a_2,x_2),(a_3,x_3),\ldots,(a_m,x_m)\}$.

Number of choices for $x_1$ to map: $n$
Number of choices for $x_2$ to map: $n-1$
Number of choices for $x_3$ to map: $n-2$
...
Number of choices for $x_m$ to map: $n-(m-1)$

By the [[Combinatorics Introduction#The Product Rule|Product Rule]], $n\cdot (n-1)\cdot (n-2)\cdot \ldots \cdot (n-m+1)$
$=\dfrac{n!}{(n-m)!}=P(n,m)$

See [[Permutations]]


## Images of subsets

If $f: A\to B$ and $A_1 \subseteq A$, then
- $f(A_1)=\{b \in B \mid b=f(a)$ for some $a\in A_1$$\}$
- $f(A_1)$ is called the **image of** $A_1$ under $f$.

> For $A=\{1,2,3,4,5\}$ and $B=\{w,x,y,z\}$
> Let $f:A\to B$ be given by
> $f=\{(1,w),(2,x),(3,x),(4,y),(5,y)\}$

- For $A_1=\{1\}$
	- $f(A_1)$
	- $=\{f(a)\mid a\in A_1\}$
	- $=\{f(1)\}$
	- $=\{w\}$ 

- For $A_2=\{1,2\}$
	- $f(A_2)$
	- $=\{f(a)\mid a\in A_2\}$
	- $=\{f(1),f(2)\}$
	- $=\{w,x\}$

### Theorem

Let $f:A\to B$, with $A_1,A_2 \subseteq A$. Then
- **a)** $f(A_1 \cup A_2)=f(A_1)\cup f(A_2)$
- **b)** $f(A_1 \cap A_2)\subseteq f(A_1) \cap f(A_2)$
- **c)** $f(A_1 \cap A_2)=f(A_1) \cap f(A_2)$ when $f$ is [[#One-to-one functions|injective]]

#### Proof (b)

For each $b \in B$, $b \in f(A_1 \cap A_2)$
- $\implies b=f(a)$ for some $a \in A_1 \cap A_2$
- $\implies [b=f(a)$ for some $a\in A_1]$ and $[b=f(a)$ for some $a\in A_2]$
- $\implies b\in f(A_1)$ and $b \in f(A_2)$
- $\implies b \in f(A_1)\cap f(A_2)$
- $\therefore f(A_1 \cap A_2) \subseteq f(A_1) \cap f(A_2)$

This is only a *subset*, not *equal*, because the same ***cannot be done*** in reverse, unlike Theorem **a)** and **c)**. If we try to show the theorem in reverse:
- $b \in f(A_1)\cap f(A_2)$
- $\implies b\in f(A_1)$ and $b \in f(A_2)$
-  $\implies [b=f(a)$ for some $a\in A_1]$ and $[b=f(c)$ for some $c\in A_2]$
- Since we don't know if the function is [[#One-to-one functions|injective]], the two $a$'s can be different values that make up the same $b$.
- If the function is [[#One-to-one functions|injective]], then $a=c$ and can be proven backwards.


## Onto functions

A function $f:A\to B$ is called **onto**, or **surjective**,
- if $f(A)=B$
- for all $b\in B$ there is at least one $a\in A$ with $f(a)=b$
- "none of the elements in $B$ is untouched"

If $f: A\to B$ is onto, with $A,B$ finite,
- we must have $|A| \geq |B|$
- since elements in $A$, the domain, cannot be mapped more than once as the definition of [[#Functions|functions]].

### Examples

> Is the function $f:R\to R$ defined by $f(x)=x^3$ onto?

**Yes**. Height values reach both $+\infty$ and $-\infty$

To show, pick an arbitrary value and show that it is mapped.

If $r$ is any real number in the codomain of $f$,
then $\sqrt[3]{r}$ is a real number in the domain of $f$,
and $f(\sqrt[3]{r})=(\sqrt[3]{r})^3=r$
i.e., the codomain of $f=R=$ the range of $f$. 

$\therefore f(x)$ is onto.


> Is the function $f:Z\to Z$ where $f(x)= 3x+1$ onto?

Range of $f=\{\ldots,-5_{x=-2},-2_{x=-1},1_{x=0},4_{x=1},7_{x=2},\ldots\}$
Some integers are not possible to get to, such as -1, 0, 2, 3
i.e., $3x+1=0$ has no solution in $Z$
$\implies$ Range of $f \subset Z$

$\therefore f(x)$ is *not* onto

However, if the function was defined as $g:R\to R, g(x)=3x+1$, it would be onto.


> For $A=\{1,2,3,4\}$ and $B=\{x,y,z\}$, are the following onto?

- $f_1=\{(1,z),(2,y),(3,x),(4,y)\}$
	- Onto since $x,y,z$ are all hit
	- Not one-to-one since $y$ is hit twice

- $f_2=\{(1,x),(2,x),(3,y),(4,z)\}$
	- Onto since $x,y,z$ are all hit
	- Not one-to-one since $x$ is hit twice

- $f_3=\{(1,x),(2,x),(3,y),(4,y)\}$
	- Not onto since $z$ is not hit
	- Not one-to-one since $x$ is hit twice