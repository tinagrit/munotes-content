Section 3.2

| Laws                                                           | Formula                                                                                                |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Law of Double [[1_Operations of Set#Complements\|Complements]] | $\overline{\overline{A}}=A$                                                                            |
| DeMorgan's Law                                                 | $\overline{A\cup B}=\overline A \cap \overline B$<br>$\overline{A\cap B}=\overline A \cup \overline B$ |
| Commutative Laws                                               | $A \cup B=B\cup A$<br>$A\cap B=B\cap A$                                                                |
| Associative Laws                                               | $A\cup(B\cup C)=(A\cup B)\cup C$<br>$A\cap(B\cap C)=(A\cap B)\cap C$                                   |
| Distributive Laws                                              | $A\cup (B \cap C) = (A\cup B)\cap(A \cup C)$<br>$A\cap (B \cup C) = (A\cap B)\cup(A \cap C)$           |
| Idempotent Laws                                                | $A\cup A = A$<br>$A\cap A = A$                                                                         |
| Identity Laws                                                  | $A\cup \varnothing=A$<br>$A\cap U = A$                                                                 |
| Inverse Laws                                                   | $A\cup \overline A=U$<br>$A \cap \overline A = \varnothing$                                            |
| Domination Laws                                                | $A\cup U=U$<br>$A\cap \varnothing = \varnothing$                                                       |
| Absorption Laws                                                | $A\cup (A\cap B)=A$<br>$A\cap (A\cup B)=A$                                                             |

Same laws as the [[Logical Equivalence#The Laws of Logic|laws of logic]], 
- replacing $\lnot A$  with  $\overline A$.
- $U$ is the $T_0$ 
- $\varnothing$ is the $F_0$


---
## Proving DeMorgan's Law

- $\overline{A\cup B}=\overline A \cap \overline B$, show that:
	- $\overline{A\cup B} \subseteq \overline A \cap \overline B$
		- $x\in \overline {A \cup B}$
			$\implies x\not\in A\cup B$
			$\implies x\not\in A$ and $x\not\in B$
			$\implies x \in \overline A$ and $x \in \overline B$
			$\implies x \in \overline A \cap \overline B$
			$\therefore \overline{A\cup B} \subseteq \overline A \cap \overline B$
	
	-  $\overline A \cap \overline B \subseteq\overline{A\cup B}$
		- $x \in \overline A \cap \overline B$
			$\implies x \in \overline A$ and $x \in \overline B$
			$\implies x\not\in A$ and $x \not \in B$
			$\implies x \not \in A \cup B$
			$\implies x \in \overline {A \cup B}$
			$\therefore \overline A \cap \overline B \subseteq\overline{A\cup B}$
	
	- $\therefore \overline{A\cup B}=\overline A \cap \overline B$


---
## Example

> Simplify the following expression
> $\overline{\overline{(A \cup B)\cap C}\cup \overline B}$

- $\overline{\overline{(A\cup B)\cap C}} \cap \overline{\overline{B}}$   by DeMorgan's Law
- $[(A\cup B)\cap C] \cap B$   by Law of Double Complement
- $(A\cup B)\cap (C\cap B)$   by Associative Law of Intersection
- $(A\cup B)\cap(B\cap C)$   by Commutative Law of Intersection
- $[(A\cup B)\cap B]\cap C$   by Associative Law of Intersection
- $B \cup C$   by Absorption Law


> Negate the expression $A-B$
> Write it in terms of the $\cup$ and $-$ operators

From the [[1_Operations of Set#Relative complement|definition of relative complements]]:
$A-B$
$=\{    x|   x\in A \land x\not\in B    \}$
$=\{    x|   x\in A \land x\in \overline B    \}$
$= A\cap \overline B$

Negation of $A-B=$  $\overline{A-B}=\overline{A\cap\overline{B}}$

$\overline{A\cap\overline{B}}$
$=\overline A \cup \overline{\overline B}$   by DeMorgan's Law
$=\overline A \cup B$   by Law of Double Complement


> Negate the expression $A\Delta B$ and simplify

From the [[1_Operations of Set#Operators|definition of symmetric difference]]
$A\Delta B$
$=\{x|x\in A\cup B \land x\not\in A \cap B\}$
$=(A\cup B)-(A\cap B)$   from the definition of relative complement
$=(A\cup B)\cap\overline{(A\cap B)}$   from the result on previous example

Negation of $A\Delta B=\overline{A\Delta B}=\overline{(A\cup B)\cap\overline{(A\cap B)}}$

$\overline{(A\cup B)\cap\overline{(A\cap B)}}$
$=\overline{(A\cup B)} \cup \overline{\overline{(A\cap B)}}$   by DeMorgan's Law
$=\overline{(A\cup B)}\cup(A\cap B)$   by Law of Double Complement
$=(A\cap B)\cup\overline{(A\cup B)}$   by Commutative Law (switch order)
$=(A\cap B)\cup(\overline A \cap \overline B)$   by DeMorgan's Law
$=[(A\cap B)\cup \overline A]\cap[(A\cap B)\cup \overline B]$   by Distributive Law
$=[(A\cup \overline A)\cap(B \cup \overline A)]\cap[(A\cup \overline B)\cap(B\cup \overline B)]$   by Distributive Law
$=[U\cap(B\cup\overline A)]\cap[(A\cup\overline B)\cap U]$   by Inverse Law
$=(B\cup\overline A)\cap(A\cup\overline B)$   by Identity Law
When simplifying, we can reasonably stop here. However, to show the result in relation of the original statement:

$=(\overline A \cup B)\cap(A\cup\overline B)$   by Commutative Law
$=(\overline A \cup B)\cap(\overline{\overline A \cap B})$   by DeMorgan's Law
$=\overline A \Delta B$

$\therefore \overline{A\Delta B} = \overline A \Delta B = A \Delta \overline B$



