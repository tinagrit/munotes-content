[[Open statements]] can be quantified using
- **$\exists$  Existential** Quantifier: "for some $x$": $\exists x$
- **$\forall$  Universal** Quantifier: "for all $x$": $\forall x$

- $x$ in $p(x)$: **free** variable
- $x$ in $\exists x$, $p(x)$: **bound** variable

### Examples

> Consider:
>- $p(x)$: $x\geq 0$
> - $q(x)$: $x^2 \geq 0$
> - $r(x)$: $x^2-3x-4=0$   $(x-4)(x+1)=0$
> - $s(x)$: $x^2-3>0$

>$\exists x[p(x)\land r(x)]$
- Can we find "some" value of x (an example) that makes $p(x)$ and $r(x)$ true?
	- When $x=4$, both $p(x)$ and $r(x)$ are true
- Then, $\exists x[p(x)\land r(x)]$: **true**, eg. $x=4$

>$\forall x[p(x)→ q(x)]$
- Is it true that for all $x$'s, if $x \geq 0$ then $x^2 \geq 0$ ?
	- If $x$ is negative, then $p(x)$ is false, then the statement becomes true.
	- If $x \geq 0$, then $p(x)$ is true, $q(x)$ is true, so $p(x) → q(x)$ is also true.
- Then $\forall x[p(x)→ q(x)]$: **true**

>$\exists x[p(x)→ q(x)]$
- Is it true that for some $x$'s, is the statement above true?
- Since $\forall x[p(x)→ q(x)]$: true, $\exists x[p(x)→ q(x)]$ is also **true**

>$\forall x[q(x) → s(x)]$
- Is it true that for all $x$'s, if $x^2 \geq 0$ then $x^2-3>0$
	- To prove that this is false, find at least a single value of $x$ that makes $q(x)$ true and $s(x)$ false. (since $q(x) → s(x)$)
	- When $x=1$, $q(x)=1$ and $s(x)=0$
- Then $\forall x[q(x) → s(x)]$: **false**

>$\forall x[r(x)\lor s(x)]$
- Is it true that for all $x$'s, at least one of $x^2-3x-4=0$ or $x^3-3>0$ is true
	- To prove that this is false, find at least a single value that makes both statements false
	- When $x=0$, $r(x)=0$ and $s(x)=0$
- Then $\forall x[r(x)\lor s(x)]$: **false**

>$\forall [r(x) → p(x)]$
- Is it true that for all $x$'s, if $x^2-3x-4=0$ then $x \geq 0$
	- To prove that this is false, find at least a single value of $x$ that makes $r(x)$ true and $p(x)$ false. (since $r(x) → p(x)$)
	- When $x=-1$, $r(x)=1$ and $p(x)=0$
- Then $\forall [r(x) → p(x)]$: **false**


---

## Implicit Quantification

Sometimes, quantifiers are **not mentioned**, but they are implicitly **implied**.

For example, the trigonometric identity $\sin^2x+\cos^2x=1$ really means:
$$\forall x[\sin^2x+\cos^2x=1]$$

*"The integer 41 is equal to the sum of two perfect squares"* would be:
$$\exists m \exists n[m^2+n^2=41]$$

### Examples

> Consider:
> - $p(x)$: Student x likes Physics
> - $q(x)$: Student x is a genius
> - $r(x)$: Student x is happy
> Translate the following into quantified statements:

> Not every student likes Physics
- $\neg[\forall x,p(x)] \Leftrightarrow \exists x \neg p(x)$

> Every student who likes Physics is a genius, but not happy.
- $\forall x[p(x) → (q(x) \land \neg r(x))]$

> For every student who is a genius, there is a student who likes Physics
- $\forall x \exists y[q(x) → p(y)]$





> If a quadrilateral is a rectangle ($p(x)$), then it has four equal angles ($q(x)$)
- $\forall x[p(x) → q(x)]$: **true**

> If a quadrilateral has four equal angles, then it is a rectangle.
- $\forall x[q(x) → p(x)]$: **false**, eg. square
- Squares are not rectangles



> For every integer $n$ we call $n$ even if it is divisible by 2
- $p(n)$: $n$ is even
- $q(n)$: $n$ is divisible by 2
- $\forall n[p(n) \leftrightarrow q(n)]$
- This is a $\leftrightarrow$ if and only if because the statements are true in both directions, unlike the quadrilateral examples above.


---

## Logical Equivalence
See [[Logical Equivalence|non-quantifying logical equivalences]]

For the statement $\forall x [p(x) → q(x)]$
- **Contrapositive**: $\forall x[\neg q(x) → \neg p(x)]$
- **Converse**: $\forall x[q(x) → p(x)]$
- **Inverse**: $\forall x[\neg p(x) → \neg q(x)]$

For negation for non-quantifying statements, see [[Implications and Argument#Negation|Negation]]

> Consider the universe of all integers and the open statements:
> $r(x)$: $2x+1=5$, $x=2$
> $s(x)$: $x^2=0$, $x=\pm3$
- $\exists x[r(x) \land s(x)]$: **false**
- $\exists x, r(x) \land \exists x, s(x)$: **true**, eg. 2 and 3, since $x$ for $r$ and $s$ don't have to be the same since they are structurally separated. 

In general, $\exists x[p(x)\land q(x)] \centernot \iff \exists x,p(x) \land \exists x, q(x)$

**However**, $\exists x[p(x)\land q(x)] \implies \exists x,p(x) \land \exists x, q(x)$


For a prescribed universe and any open statements $p(x)$, $q(x)$

- $\exists x[p(x)\land q(x)] \implies \exists x,p(x) \land \exists x, q(x)$
- $\exists x[p(x) \lor q(x)] \iff [\exists x,p(x) \lor \exists x, q(x)]$
- $\forall x[p(x) \land q(x)] \iff [\forall x,p(x) \land \forall x, q(x)]$
- $[\forall x ,p(x) \lor \forall x ,q(x)] \implies \forall x [p(x)\lor q(x)]$
	- eg. $p(x)$: $x$ is odd, $q(x)$: $x$ is even
	- All integers are odd or even does **NOT** imply that all integers are odd or all integers are even
	- This arrow only works one way


Negation:
Bring the **negation in** and **switch** between universal $\forall$ / existential $\exists$.
- $\neg [\forall x,p(x)] \iff \exists x, \neg p(x)$
- $\neg [\exists x,p(x)]\iff\forall x,\neg p(x)$
- $\neg [\forall x,\neg p(x)] \iff \exists x, p(x)$
- $\neg [\exists x, \neg p(x)]\iff\forall x, p(x)$

### Example

> For the universe of all integers:
> $p(x)$: $x$ is odd
> $q(x)$: $x^2-1$ is even
> Find the negation of the statement $\forall x[p(x) → q(x)]$

$\neg[\forall x[p(x) → q(x)]]$
$\iff \exists x,\neg[p(x) → q(x)]$
$\iff \exists x,\neg[\neg p(x) \lor q(x)]$  
$\iff \exists x[\neg\neg p(x) \land \neg q(x)]$
$\iff \exists x[p(x) \land \neg q(x)]$


### Multiple Variables

- $\forall x \forall y,p(x,y)\iff \forall y \forall x,p(x,y)$
- $\exists x \exists y,p(x,y) \iff \exists y \exists x,p(x,y)$

>For example, for the universe of all integers and $p(x,y)$: $x+y=17$
- $\forall x \exists y, p(x,y)$: for every integer $x$ there is an integer y such that $x+y=17$: **true**
- $\exists y \forall x, p(x,y)$: there's an integer $y$  such that any value of $x$ makes $x+y=17$: **no longer true**

In general, $\forall x \exists y,p(x,y) \not \Leftrightarrow \exists y \forall x,p(x,y)$


> Consider: $p(x,y)$, $q(x,y)$, and $r(x,y)$.
> Find the negation of:$$\forall x \exists y [(p(x,y) \land q(x,y))→ r(x,y)]$$

$\neg[\forall x \exists y [(p(x,y) \land q(x,y))→ r(x,y)]]$
$\iff \exists x[\neg \exists y[(p(x,y) \land q(x,y))→ r(x,y)]]$
$\iff \exists x \forall y, \neg[(p(x,y) \land q(x,y))→ r(x,y)]$
$\iff \exists x \forall y, \neg[\neg(p(x,y) \land q(x,y)) \lor r(x,y)]$
$\iff \exists x \forall y[(p(x,y) \land q(x,y)) \land \neg r(x,y)]$

