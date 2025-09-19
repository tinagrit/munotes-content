## Proof by Method of Exhaustion

Exhaust all ways of the proof to find out

> Consider a universe of 13 integers: $2,4,6,8,\ldots,24,26$
> Prove the statement "For all $n$, we can write $n$ as the sum of at most three perfect squares"

- $2=1+1$
- $4=4$
- $6=4+1+1$
- $8=4+4$
- $10=9+1$
- $12=4+4+4$
- $14=9+4+1$
- $16=16$
- $18=16+1+1$
- $20=16+4$
- $22=9+9+4$
- $24=16+4+4$
- $26=25+1$
The statement is **true**.

---

## Rule of Universal Specification
See [[Quantifiers]]

If $p(x)$ is true in a given universe, and
if $\forall x,p(x)$ is true, then $p(a)$ is true for each $a$ in the universe.

**TL;DR**: When $\forall x,p(x)$ is true, it can be reduced to $p(a)$

### Example

> Consider:
> $m(x)$:  $x$ is a mathematics professor
> $c(x)$:  $x$ has studied calculus
> Argument: All mathematics professors have studied calculus. Damian is a mathematics professor. Therefore, Damian has studied calculus.

Let $b$ represent the individual Damian

| Argument                  |
| ------------------------- |
| $\forall x [m(x) → c(x)]$ |
| $m(b)$                    |
| $\therefore c(b)$         |

| Steps | Expression                | Reasons                                    |
| ----- | ------------------------- | ------------------------------------------ |
| 1     | $\forall x [m(x) → c(x)]$ | Premise                                    |
| 2     | $m(b) → c(b)$             | Step 1 and Rule of Universal Specification |
| 3     | $m(b)$                    | Premise                                    |
| 4     | $\therefore c(b)$         | Step 3 and Modus Ponens                    |

See [[Inference rules]] and [[Logical Equivalence#The Laws of Logic|The Laws of Logic]]


> Consider:
> $p(t)$:  $t$ has two sides of equal length
> $q(t)$:  $t$ is an isosceles triangle
> $r(t)$:  $t$ has two angles of equal measure
> And the argument shown below:

Let $c$ represent triangle XYZ.

| Wording                                                             | Argument                 |
| ------------------------------------------------------------------- | ------------------------ |
| In the triangle XYZ, there is no pair of angles of equal measure.   | $\neg r(c)$              |
| If a triangle has two sides of equal length, then it is isoselces   | $\forall t[p(t) → q(t)]$ |
| If a triangle is isosceles, then it has two angles of equal measure | $\forall t[q(t) → r(t)]$ |
| Therefore, triangle XYZ has no two sides of equal length            | $\therefore \neg p(c)$   |

| Steps | Expression               | Reasons                                    |
| ----- | ------------------------ | ------------------------------------------ |
| 1     | $\forall t[p(t) → q(t)]$ | Premise                                    |
| 2     | $p(c) → q(c)$            | Step 1 and Rule of Universal Specification |
| 3     | $\forall t[q(t) → r(t)]$ | Premise                                    |
| 4     | $q(t) → r(t)$            | Step 3 and Rule of Universal Specification |
| 5     | $p(c) → r(c)$            | Steps 2, 4 and Law of Syllogism            |
| 6     | $\neg r(c)$              | Premise                                    |
| 7     | $\therefore \neg p(c)$   | Steps 5, 6 and Modus Tollens               |



> Consider the universe of all polygons.
> Let $c$ denote one specific polygon -- the quadrilateral EFGH, where the measure of angle E is $91 \degree$
> $p(x)$:  $x$ is a square
> $q(x)$:  $x$ has four sides
> And the argument shown below:

| Wording                           | Argument                 |
| --------------------------------- | ------------------------ |
| All squares have four sides       | $\forall x[p(x) → q(x)]$ |
| Quadrilateral EFGH has four sides | $q(c)$                   |
| Quadrilateral EFGH is a square    | $\therefore p(c)$        |
This is an **invalid argument** as we are arguing using the converse.


---

## Rule of Universal Generalization

If $p(x)$ is proven to be true when $x$ is replaced by **any arbitrarily chosen** element $c$ from the universe
Then, $\forall x,p(x)$ is true

**TL;DR**: If $p(c)$ is true when $c$ is arbitrary, then it can be expanded to $\forall x,p(x)$

### Example

> Consider the following argument

| Argument                            |
| ----------------------------------- |
| $\forall x[p(x) → q(x)]$            |
| $\forall x [q(x) → r(x)]$           |
| $\therefore \forall x[p(x) → r(x)]$ |

| Steps | Expression                         | Reasons                                     |
| ----- | ---------------------------------- | ------------------------------------------- |
| 1     | $\forall x[p(x) → q(x)]$           | Premise                                     |
| 2     | $p(c) → q(c)$                      | Step 1 and Rule of Universal Specification  |
| 3     | $\forall x [q(x) → r(x)]$          | Premise                                     |
| 4     | $q(c) → r(c)$                      | Step 2 and Rule of Universal Specification  |
| 5     | $p(c)→ r(c)$                       | Steps 2, 4 and Law of Syllogism             |
| 6     | $\therefore \forall x[p(x)→ r(x)]$ | Step 5 and Rule of Universal Generalization |



> Consider the following argument

| Argument                                  |
| ----------------------------------------- |
| $\forall x[p(x) \lor q(x)]$               |
| $\forall x[(\neg p(x) \land q(x))→ r(x)]$ |
| $\therefore \forall x[\neg r(x) → p(x)]$  |

| Argument (modified)                       |
| ----------------------------------------- |
| $\forall x[p(x) \lor q(x)]$               |
| $\forall x[(\neg p(x) \land q(x))→ r(x)]$ |
| $\forall x,\neg r(x)$                     |
| $\therefore \forall x,p(x)$               |

| Steps | Expression                                 | Reasons                                      |
| ----- | ------------------------------------------ | -------------------------------------------- |
| 1     | $\forall x[p(x) \lor q(x)]$                | Premise                                      |
| 2     | $p(c) \lor q(c)$                           | Step 1 and Rule of Universal Specification   |
| 3     | $\forall x[(\neg p(x) \land q(x))→ r(x)]$  | Premise                                      |
| 4     | $(\neg p(c) \land q(c))→ r(c)$             | Step 3 and Rule of Universal Specification   |
| 5     | $\forall x,\neg r(x)$                      | Premise                                      |
| 6     | $\neg r(c)$                                | Step 5 and Rule of Universal Specification   |
| 7     | $\neg(\neg p(c) \land q(c))$               | Steps 4, 6 and Modus Tollens                 |
| 8     | $p(c) \lor \neg q(c)$                      | Step 7 and DeMorgan's Law                    |
| 9     | $(p(c)\lor q(c))\land(p(c)\lor \neg q(c))$ | Steps 2, 8 and Rule of Conjunction           |
| 10    | $p(c) \lor (q(c)\land \neg q(c))$          | Step 9 and Distributive Law                  |
| 11    | $p(c) \lor F_0$                            | Step 10 and Inverse Law                      |
| 12    | $p(c)$                                     | Step 11 and Identity Law                     |
| 13    | $\therefore \forall x,p(x)$                | Step 12 and Rule of Universal Generalization |


---

## Direct proof

> For the universe of integers, prove that for all integers $k$ and $l$, if $k$ and $l$ and both odd, then $k+l$ is even.

Since $k$, $l$ are odd,
they each can be written as $(2*\text{integer})+1$

$k=2a+1,a\in \mathbb{Z}$
$l=2b+1,b\in \mathbb{Z}$

Then $k+l=(2a+1)+(2b+1)=2(a+b+1)$

Since $a$, $b$ are integers, $c=a+b+1$ is an integer, and $k+l=2c$, and therefore, $k+l$ is even.


> Consider the statement
> $\forall n [n^2 = n]$

$n=0$:  $0^2=0$   so the result holds
$n=1$:  $1^2=1$   so the result holds

We cannot conclude that $\forall n [n^2=n]$ based on the above.
We must choose $n$ arbitrarily.

We, instead, have shown $\exists n[n^2+n]$


> Prove that $m$ is an even integer, then $m+7$ is odd.

$p(m)$:  $m$ is an even integer
$q(m)$:  $m+7$ is odd

$\forall m[p(m) → q(m)]$

Show that $p(m)$ is true, and show that $p(m)$ leads to $q(m)$ being true.

Since $m$ is even, we can write $m=2a,a\in\mathbb{Z}$
$m+7$
$=2a+7$
$=2a+6+1$
$=2(a+3)+1$

Since $a$ is an integer, then $a+3$ is an integer.
$m+7$ is odd.


---

## Indirect proof

### Prove by contrapositive

> Prove that $m$ is an even integer, then $m+7$ is odd.

$\forall m [p(m) → q(m)]\iff\forall m [\lnot q(m) → \lnot p(m)]$

If $m+7$ isn't odd, then $m$ isn't an even integer.

Since $m+7$ is even, we can write $m+7=2c,c\in\mathbb{Z}$

$m+7=2c$
$m=2c-7$
$m=2c-8+1$
$m=2(c-4)+1$  where $c-4$ is an integer

$m$ is odd.

The original conclusion ($m$ is an even integer then $m+7$ is odd) is true.

### Prove by contradiction

> Prove that $m$ is an even integer, then $m+7$ is odd.

Assume $m$ is even, and $m+7$ is also even.

Then $m+7=2c$      for some integer $c$

$m=2c-7$
$m=2c-8+1$
$m=2(c-4)+1$   where $c-4$ is an integer

$m$ is both even and odd at the same time, it is a **contradiction**

The original conclusion ($m$ is an even integer then $m+7$ is odd) is true.

---

## Examples

> Prove that for all positive real numbers $x$ and $y$, if the product $xy$ exceeds $25$, then $x>5$ or $y>5$.

$\forall x \forall y[p(x,y)→ q(x,y)]$

**Direct proof**
- Assume that $xy>25$
- Show that $x>5$ or $y>5$
- This is *difficult* to do

**Contrapositive**
- The negation of the conclusion leads to the negation of the premise
- $\forall x \forall y[\lnot q(x,y) → \lnot p(x,y)]$
	- If $\lnot(x>5$ or $y>5)$ then the product $xy$ doesn't exceed $25$
	-  $(0<x\leq5$ (positive) *and* (DeMorgan's) $0<y\leq5)$
		Then $0\cdot0<x\cdot y\leq 5\cdot 5$
				$0<xy\leq 25$
	- Original statement is valid since its contrapositive is valid
- Many times, this is easier than direct proof
