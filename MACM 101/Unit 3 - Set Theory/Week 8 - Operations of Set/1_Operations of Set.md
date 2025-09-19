Section 3.2
## Operators
See [[Sets and Subsets]]

| Operation               | Denoted      | Definition                                                                       |
| ----------------------- | ------------ | -------------------------------------------------------------------------------- |
| Union                   | $A \cup B$   | $\{x\vert x\in A \lor x\in B\}$                                                  |
| Intersection            | $A \cap B$   | $\{x\vert x\in A \land x\in B\}$                                                 |
| Symmetric<br>Difference | $A \Delta B$ | $\{x\vert x\in A\cup B \land x\not\in A\cap B\}$<br>in the $\cup$ but not $\cap$ |

> $A=\{1,2,3,4,5\}$
> $B=\{3,4,5,6,7\}$
> $C=\{7,8,9\}$

$A\cap B = \{3,4,5\}$
$A\cup B = \{1,2,3,4,5,6,7\}$
$B\cup C = \{3,4,5,6,7,8,9\}$
$A\Delta B=\{1,2,6,7\}$
$A\cap C=\varnothing$
$A\cup C=\{1,2,3,4,5,7,8,9\}$
$A\Delta C=\{1,2,3,4,5,7,8,9\}$

### Mutually disjoint

Sets $S$ and $T$ are **disjoint** or **mutually disjoint** when $S\cap T = \varnothing$. ($S$ and $T$ don't share anything)
- $S$ and $T$ are disjoint if and only if $S\cup T=S\Delta T$
- Proof:
	- Two proofs needed (due to "if and only if")
	- Part 1 ($\Rightarrow$) $S\cap T = \varnothing$ $\implies S\cup T=S\Delta T$
		-  $S$ and $T$ are disjoint. 
		- Must show $S\cup T=S\Delta T$, then:
			- $S\cup T \subseteq S\Delta T$
				- If $x\in S\cup T$, then $x\in S$ or $x \in T$
				- But with $S,T$ disjoint, $x\not\in S \cap T$
				- So $x\in S\Delta T$ by definition
				- Thus, $x\in S\cup T \implies x \in S\Delta T$, and $S\cup T \subseteq S\Delta T$
			- $S\Delta T \subseteq S\cup T$
				- If $y\in S\Delta T$, then $y\in S$ or $y\in T$, so $y\in S\cup T$
				- Thus $S\Delta T \subseteq S\cup T$
		- $\therefore S\Delta T = S\cup T$
	- Part 2 ($\Leftarrow$)  $S\cup T=S\Delta T \implies S\cap T = \varnothing$ 
		- Proof by contradiction, assume $S\cup T = S\Delta T$ and $S,T$ are *not* disjoint, then $S\cap T \not = \varnothing$
		- Let $x\in S \cap T$, then $x\in S$ and $x\in T$, so $x\in S\cup T$
		- Thus $x \in S\Delta T$ (since $S\cup T = S\Delta T$)
		- But when $x \in S \cup T$ and $x \in S \cap T$, then $x \not \in S \Delta T$ by definition
		- Contradiction ($x\in S\Delta T \land x\not\in S \Delta T$)
		- $\therefore$ $S,T$ are disjoint.

---
## Complements

For a universe $U$ and set $A \subseteq U$, the **complement** of $A$
- denoted $U-A$ or $\overline A$ (*negation of $A$; anything but $A$*)
- given by $\{x|x\in U \land x \not \in A\}$

> $U=\{1,2,3,4,5,6,7,8,9,10\}$
> $A=\{1,2,3,4,5\}$
> $B=\{3,4,5,6,7\}$
> $C=\{7,8,9\}$

$\overline A = \{ 6,7,8,9,10 \}$ 
$\overline B = \{   1,2,8,9,10   \}$
$\overline C = \{    1,2,3,4,5,6,10     \}$


### Relative complement

For sets $A,B$, the **relative complement** of $A$ in $B$
- denoted by $B-A$
- given by $\{x|x\in B \land x \not \in A\}$
	- Anything in $B$ but not in $A$

Using above sets:
$B-A=\{    6,7    \}$
$A-B=\{     1,2     \}$
$A-C=\{     1,2,3,4,5     \}=A$
$C-A=\{7,8,9\}=C$
$A-A=\varnothing$
$U-A=\overline A$


### Theorem

For any universe $U$ and any set $A,B$ in $U$, the following statements are **equivalent**:
- all the elements of $A$ are in $B$
- $A\subseteq B$
- $A\cup B = B$
- $A\cap B = A$
- $\overline B \subseteq \overline A$

