Section 5.4

## Unary operations
A function $g:A\to A$ is called a **unary** or **monary** operation on $A$

Example:
-  $h:R^+\to R^+$ with $h(a)=1/a$


## Binary operations
aka Multi-variable functions, *called **BO** on the cheat sheet*

For any nonempty set $A,B$, any function $f:A\times A \to B$ is called a **binary operation** on $A$.
- if $B \subseteq A$, then the binary operation is said to be closed on $A$.

Examples:
- $f:Z\times Z\to Z$, defined by $f(a,b)=a-b$
	- closed binary operation
- If $g: Z^+ \times Z^+ \to Z$ with $g(a,b)=a-b$
	- binary operation, not closed


### Commutative 
Let $f: A\times A \to B$; that is, $f$ is a [[#Binary operations|binary operation]] on $A$

- $f$ is said to be **commutative** 
	- if $f(a,b)=f(b,a),\forall(a,b)\in A\times A$

#### Example

> The addition function $f: R \times R \to R, f(x,y)=x+y$
- is commutative since $x+y$ and $y+x$ are the same

> $f:Z\times Z \to Z,$ $f(a,b)=a+b-3ab$
- is commutative since:
	- $f(a,b)=a+b-3ab$
	- $f(b,a)=b+a-3ba$
	- Addition and multiplication of integers are both commutative functions

> $h:Z\times Z \to Z$ as $h(a,b)=a\cdot |b|$
- is *not* commutative since $h(a,b) \not = h(b,a)$
	- $h(3,-2)=3\cdot |-2|=3\cdot 2=6$
	- $h(-2,3)=-2\cdot |3|=-2\cdot 3=-6$


### Associative
Let $f: A\times A \to B$; that is, $f$ is a [[#Binary operations|binary operation]] on $A$

- When $B\subseteq A$ (that is, when $f$ is closed)
	- $f$ is said to be **associative**
		- if for $a,b,c\in A,f(f(a,b),c)=f(a,(f(b,c))$
		- The order in which the functions are applied to arguments does not matter

#### Example

> $f:Z\times Z \to Z,$ $f(a,b)=a+b-3ab$
- is associative since:
	- $f(f(a,b),c)=f(a,b)+c-3f(a,b)\cdot c$
		- $=(a+b-3ab)+c-3(a+b-3ab)\cdot c$
		- $= a+b+c-3ab-3ac-3bc+9abc$
	- $f(a,f(b,c))=a+f(b,c)-3af(b,c)$
		- $=a+(b+c-3bc)-3a(b+c-3bc)$
		- $=a+b+c-3ab-3ac-3bc+9abc$

> $h:Z\times Z \to Z$ as $h(a,b)=a\cdot |b|$
- is associative since:
	- $h(h(a,b),c)=h(a,b)\cdot |c|=a\cdot |b| \cdot |c|$
	- $h(a,h(b,c))=a\cdot |h(b,c)|=a\cdot |b\cdot |c||=a\cdot |b|\cdot |c|$


### Identity Elements
Not to be confused with [[1_Composition and Inverse#Identity function|Identity functions]]

Let $f: A\times A \to B$; that is, $f$ is a [[#Binary operations|binary operation]] on $A$

- An element $x\in A$ is called an **identity element** for $f$
	- if $f(a,x)=f(x,a)=a,\forall a \in A$
	- find a single element $x$ that makes the above expression true *for all $a$*


> $f:Z\times Z \to Z$ with $f(a,b)=a+b$

Need to find $x$ such that $f(a,x)=f(x,a)=a$
- $a+x=x+a=a$

At $x=0$, 
- $a+0=0+a=a$
- $a=a=a$

Then $0$ is an *identity element* for $f$.


> The function $f:Z\times Z \to Z$ defined by $f(a,b)=a-b$

Need to find $x$ such that $f(a,x)=f(x,a)=a$
- $a-x=x-a=a$

$a-x=a$
- $x$ has to be $0$

$x-a=a$
- $x$ has to be $2a$

Then function $f$ has *no identity element*. There is no such $x$ that works $\forall a\in Z$


> Let $A=\{1,2,3,4,5,6,7\}$ and
> $g: A\times A \to A$ be defined by $g(a,b)=min\{a,b\}$

Need to find $x$ such that $g(a,x)=g(x,a)=a$

For any $a\in A$,
- $g(a,7)=a$
- $g(7,a)=a$

Then $7$ is an identity element for $f$.
