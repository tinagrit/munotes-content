Section 5.6

## One-to-one correspondence
If $f: A\to B$
- $f$ is **bijective** or **one-to-one correspondence**
- if $f$ is *both* [[2_Functions#One-to-one functions|one-to-one]] and [[2_Functions#Onto functions|onto]]

### Identity function
Not to be confused with [[3_Special Functions#Identity Elements|identity elements]].

The function $1_A:A\to A$ 
- defined by $1_A(a)=a$ for all $a \in A$
- is the **identity function** for $A$
- maps every element to itself

### Equal function
If $f,g: A \to B$
- $f$ and $g$ are equal
- $f=g$
- if $f(a)=g(a)$ for all $a \in A$

### Examples

> Let $f: Z\to Z$, $g: Z\to Q$
> $f(x)=x=g(x)$ for all $x \in Z$

- These two functions are **not the same** since they are mapped differently (codomain)
- $f$ is both [[2_Functions#One-to-one functions|one-to-one]] and [[2_Functions#Onto functions|onto]]
- $g$ is only one-to-one but not onto
- $\therefore$ $f \not = g$


> Let $f,g: R\to Z$ be defined as
> $f(x) = \begin{cases} x & \text{if } x \in Z,\\ \lfloor x \rfloor + 1  & \text{if } x \in R-Z \end{cases}$
> $g(x)=\lceil x \rceil$ for all $x \in R$

- $f,g$ have the same domains and codomains
- If $x\in Z$
	- $f(x)=x$
	- $g(x)=\lceil x \rceil=x$
- If $x \in R-Z$ ($x\in R \land x \not \in Z$)
	- $f(x)=\lfloor x \rfloor + 1=\lceil x \rceil$
	- $g(x)=\lceil x \rceil$
- $\therefore f=g$


## Composite functions

If $f: A\to B$ and $g:B\to C$
- the **composite function** denoted $g \circ f:A\to C$
	- pronounced *"$g$ compose $f$"*
- defined by $(g \circ f)(a)=g(f(a))$ for each $a \in A$

If $f,g$ are [[2_Functions#One-to-one functions|one to one]], then $g\circ f$ is [[2_Functions#One-to-one functions|one to one]].
If $f,g$ are [[2_Functions#Onto functions|onto]], then $g\circ f$ is [[2_Functions#Onto functions|onto]]


> Let $f,g: R\to R$ be defined by
> $f(x)=x^2$
> $g(x)=x+5$

- $g \circ f(x)$
	- $=g(f(x))$
	- $=g(x^2)$
	- $=x^2+5$

- $f\circ g(x)$
	- $=f(g(x))$
	- $=f(x+5)$
	- $=(x+5)^2$

So $g \circ f \not = f \circ g$
The composition is **not commutative** in general


### Associativity

If 
- $f:A\to B$ and 
- $g: B\to C$ and 
- $h:C\to D$

Then $(h \circ g)\circ f = h\circ (g \circ f)$


> Let $f,g,h: R\to R$ where 
> $f(x)=x^2$
> $g(x)=x+5$
> $h(x)=\sqrt{x^2+2}$

$(h\circ g)\circ f$
$= (h\circ g)f(x)$
$=(h\circ g)(x^2)$
$=h(g(x^2))$
$=h(x^2+5)$
$=\sqrt{(x^2+5)^2+2}$

$h\circ (g\circ f)$
$=h(g\circ f(x))$
$=h(g(f(x)))$
$=h(g(x^2))$
$=h(x^2+5)$
$=\sqrt{(x^2+5)^2+2}$

$\therefore (h\circ g)\circ f = h\circ (g\circ f)$ and the composition is associative


## Invertible functions

$f:A\to B$ is invertible if
- there is a $g:B\to A$ 
- such that $g \circ f = 1_A$ and $f\circ g = 1_B$ (see [[#Identity function|identity functions]])

> [!info] The inverse function $f:A\to B$ is unique and represented by $f^{-1}$

A function $f:A\to B$ is invertible *if and only if* it is [[#One-to-one correspondence|bijective]].

If $f:A\to B$ and $g: B\to C$ are invertible functions
- then $g\circ f: A\to C$ is invertible
- $(g \circ f)^{-1}=f^{-1}\circ g^{-1}$


> $f,g: R\to R$
> $f(x)=2x+5$
> $g(x)=\dfrac{1}{2}(x-5)$

$(g\circ f)(x)$
- $=g(2x+5)$
- $=\dfrac{1}{2}[(2x+5)-5]$
- $=\dfrac{1}{2}(2x)$
- $=x$
- $=1_R$

$(f \circ g)(x)$
- $=f\left(\dfrac{1}{2}(x-5)\right)$
- $=2\left[\dfrac{1}{2}(x-5)\right]+5$
- $=x-5+5$
- $=x$
- $=1_R$

$\therefore$ $f,g$ are invertible and inverses of each other


### Proof (uniqueness)

Suppose we have $g:B\to A$ as the inverse of $f$, with 
- $g \circ f = 1_A$  
- $f\circ g = 1_B$

If $g$ is not unique, then there is another function $h:B\to A$ such that 
- $h \circ f = 1_A$ 
- $f\circ h = 1_B$

Show that $h=g$

$h$
- $=h\circ 1_B$
- $=h\circ (f\circ g)$
- $=(h\circ f)\circ g$
- $=1_A\circ g$
- $=g$

$\therefore h=g$ and $f^{-1}$ is unique.


### Examples

> Is the function $f: R\to R$ defined by $f(x)=x^2$ invertible?
- $f$ is *neither* one-to-one nor onto
- $\therefore$ no inverse function of $f$ exists

> Find the inverse of $f:R\to R$ defined by
> $f(x)=mx+b$ where $m,b$ are constants, $m\not = 0$
- $f(x)$ is one-to-one and onto, then the inverse exists
- From the original function, reverse the $x$'s and $y$'s
	- $f(x)=\{(x,y)\mid y=mx+b\}$
	- $f^{-1}(x)=\{(x,y)\mid x=my+b\}$
	- $f^{-1}(x)=\{(x,y)\mid y=\dfrac{1}{m}(x-b)\}$

>  Find the inverse of $f:R\to R^+$ defined by
> $f(x)=e^x$
- $f(x)$ is one-to-one and onto (since the codomain is $R^+$)
- $f^{-1}=\{(x,y)\mid x=e^y\}$
- $f^{-1}=\{(x,y)\mid y=\ln x\}$


## Same size sets

If $|A|=|B|$
- when $f:A\to B$ for finite sets $A$ and $B$
- then if one of these is true, everything else is true
	- $f$ is [[2_Functions#One-to-one functions|one to one]]
	- $f$ is [[2_Functions#Onto functions|onto]]
	- $f$ is [[#Invertible functions|invertible]]
