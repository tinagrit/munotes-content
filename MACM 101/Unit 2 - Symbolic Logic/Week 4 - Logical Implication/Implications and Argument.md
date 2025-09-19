## Negation

> Negate and simplify the compound statement
> $(p\lor q)\rightarrow r$ 

- Laws of logic don't include ($\rightarrow$)
	- First step is to **get rid** of the arrow
	- $(p\lor q)\rightarrow r$     $\Leftrightarrow$     $\lnot(p\lor q)\lor r$
	- by the [[Logical Equivalence#First Substitution rule|first substitution rule]] because $s\rightarrow t \leftrightarrow \lnot s \lor t$ is a tautology
- Negating:
	- $\lnot[\lnot(p \lor q)\lor r]$
	- $\lnot\lnot (p\lor q) \land \lnot r$     by DeMorgan's Law
	- $(p \lor q) \land \lnot r$      by Law of Double Negation


> $p$:   Joan goes to Lake George
> $q$:   Mary pays for Joan's shopping spree
> $p\rightarrow q$:    If Joan goes to Lake George, then Mary will pay for Joan's shopping spree
>
> What is the negation of $p\rightarrow q$?

$\lnot(p\rightarrow q)$   $\Leftrightarrow$   
- $\lnot(\lnot p \lor q)$ 
- $\lnot\lnot p \land \lnot q$  by DeMorgan's Law
- $p\land \lnot q$   by Law of Double Negation


| $p$ | $q$ | $\lnot p$ | $\lnot q$ | $p \rightarrow q$ | $\lnot q \rightarrow \lnot p$<br>Contrapositive | $q\rightarrow p$<br>Converse | $\lnot p \rightarrow \lnot q$<br>Inverse |
| --- | --- | --------- | --------- | ----------------- | ----------------------------------------------- | ---------------------------- | ---------------------------------------- |
| 🔴  | 🔴  | 🟢        | 🟢        | 🟢                | 🟢                                              | 🟢                           | 🟢                                       |
| 🔴  | 🟢  | 🟢        | 🔴        | 🟢                | 🟢                                              | 🔴                           | 🔴                                       |
| 🟢  | 🔴  | 🔴        | 🟢        | 🔴                | 🔴                                              | 🟢                           | 🟢                                       |
| 🟢  | 🟢  | 🔴        | 🔴        | 🟢                | 🟢                                              | 🟢                           | 🟢                                       |


> $p$:   Jeff is concerned about his cholesterol level
> $q$:   Jeff walks at least 5 km a week
> $p\rightarrow q$:   If Jeff is concerned about his cholesterol level, then he will walk at least 5 km a week

Contrapositive: $\lnot q \rightarrow \lnot p$

Converse: $q\rightarrow p$

Inverse: $\lnot p → \lnot q$



> Simplify $(p\lor q)\land \lnot (\lnot p \land q)$

- $(p\lor q)\land(\lnot \lnot p \lor\lnot q)$   by DeMorgan's Law
- $(p\lor q)\land(p\lor \lnot q)$    by Law of Double Negation
- $p \lor (q\land \lnot q)$   by Distributive Law
- $p \lor F_0$    by Inverse Law
- $p$    by Identity Law



> Simplify $\lnot [\lnot [(p \lor q) \land r] \lor \lnot q]$

- $\lnot \lnot [(p \lor q) \land r] \land \lnot \lnot q$    by DeMorgan's Law
- $[(p \lor q) \land r] \land q$     by Law of Double Negation
	- $(p\lor q)\land(r \land q)$   by Associative Law
	- $(p\lor q)\land(q \land r)$   by Commutative Law
- $[(p\lor q)\land q]\land r$    by Associative Law
- $q\land r$     by Absorption Law


---

## Argument

$(p_1\land p_2\land p_3 \land \ldots \land p_n) \rightarrow q$ 
$\text{premises} \rightarrow \text{conclusion}$

is a valid argument if and only if $(p_1\land p_2\land p_3 \land \ldots \land p_n) \rightarrow q$  is a **[[Connectives and Truth Table#Tautology and Contradiction|tautology]]**


> $p$:  Roger studies
> $q$:  Roger plays tennis
> $r$:  Roger passes discrete mathematics
>
> $p_1$:  $p → r$     If Roger studies, then he will pass discrete mathematics
> $p_2$:  $\lnot q → p$     If Roger doesn't play tennis, then he'll study
> $p_3$:  $\lnot r$     Roger failed discrete mathematics
>
> Is the argument $(p_1\land p_2 \land p_3) \rightarrow q$ valid?


$[(p\rightarrow r)\land (\lnot q → p)\land \lnot r] → q$

| $p$ | $q$ | $r$ | $p_1$<br>$p → r$ | $p_2$<br>$\lnot q → p$ | $p_3$<br>$\lnot r$ | $p_1$ <br>$\land p_2$ <br>$\land p_3$ | $→ q$ |
| --- | --- | --- | ---------------- | ---------------------- | ------------------ | ------------------------------------- | ----- |
| 🔴  | 🔴  | 🔴  | 🟢               | 🔴                     | 🟢                 | 🔴                                    | 🟢    |
| 🔴  | 🔴  | 🟢  | 🟢               | 🔴                     | 🔴                 | 🔴                                    | 🟢    |
| 🔴  | 🟢  | 🔴  | 🟢               | 🟢                     | 🟢                 | 🟢                                    | 🟢    |
| 🔴  | 🟢  | 🟢  | 🟢               | 🟢                     | 🔴                 | 🔴                                    | 🟢    |
| 🟢  | 🔴  | 🔴  | 🔴               | 🟢                     | 🟢                 | 🔴                                    | 🟢    |
| 🟢  | 🔴  | 🟢  | 🟢               | 🟢                     | 🔴                 | 🔴                                    | 🟢    |
| 🟢  | 🟢  | 🔴  | 🔴               | 🟢                     | 🟢                 | 🔴                                    | 🟢    |
| 🟢  | 🟢  | 🟢  | 🟢               | 🟢                     | 🔴                 | 🔴                                    | 🟢    |

The argument is valid since $(p_1 \land p_2 \land p_3) → q$ is a tautology.


If $p\rightarrow q$ is a tautology, then p **logically implies** q, written as $p \implies q$

- $p\implies q$    means    $p → q$ is a tautology 
- $p\Leftrightarrow q$    means    $p \leftrightarrow q$ is a tautology 


Examples on proving arguments, see [[Inference rules#Examples]]