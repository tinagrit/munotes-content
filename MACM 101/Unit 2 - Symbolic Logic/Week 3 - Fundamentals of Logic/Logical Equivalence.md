
> Consider the following
> $s_1$: $\lnot p \lor q$
> $s_2$: $p \rightarrow q$

| $p$ | $q$ | $\lnot p$ | $\lnot p \lor q$ | $p \rightarrow q$ |
| --- | --- | --------- | ---------------- | ----------------- |
| 🔴  | 🔴  | 🟢        | 🟢               | 🟢                |
| 🔴  | 🟢  | 🟢        | 🟢               | 🟢                |
| 🟢  | 🔴  | 🔴        | 🔴               | 🔴                |
| 🟢  | 🟢  | 🔴        | 🟢               | 🟢                |
- $s_1$ and $s_2$ are **logically equivalent**
- $s_1\Leftrightarrow s_2$

### Other examples
- $p \rightarrow q$     $\Leftrightarrow$     $\lnot p \lor q$
- $p\leftrightarrow q$     $\Leftrightarrow$    $(p \rightarrow q)\land(q \rightarrow p)$
- $p \oplus q$       $\Leftrightarrow$    $(p \lor q)\land \lnot(p \land q)$


> If $s_1 \leftrightarrow s_2$ is a tautology, then $s_1 \Leftrightarrow s_2$

> If $s_1 \Leftrightarrow s_2$, then $s_1 \leftrightarrow s_2$ is a tautology

---

## The Laws of Logic

| Laws                   | Formula                                                                                                                           |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Law of Double Negation | $\lnot\lnot p \Leftrightarrow p$                                                                                                  |
| DeMorgan's Laws        | $\lnot (p\lor q) \Leftrightarrow \lnot p \land \lnot q$<br>$\lnot (p\land q) \Leftrightarrow \lnot p \lor \lnot q$                |
| Commutative Laws       | $p \lor q \Leftrightarrow q \lor p$<br>$p \land q \Leftrightarrow q \land p$                                                      |
| Associative Laws       | $p\lor (q\lor r) \Leftrightarrow (p \lor q) \lor r$<br>$p\land (q\land r) \Leftrightarrow (p \land q) \land r$                    |
| Distributive Laws      | $p \lor (q \land r) \Leftrightarrow (p\lor q)\land (p \lor r)$<br>$p \land (q \lor r) \Leftrightarrow (p\land q)\lor (p \land r)$ |
| Idempotent Laws        | $p \lor p \Leftrightarrow p$<br>$p \land p \Leftrightarrow p$                                                                     |
| Identity Laws          | $p\lor F_0 \Leftrightarrow p$<br>$p\land T_0 \Leftrightarrow p$                                                                   |
| Inverse Laws           | $p \lor \lnot p \Leftrightarrow T_0$<br>$p \land \lnot p \Leftrightarrow F_0$                                                     |
| Domination Laws        | $p \lor T_0 \Leftrightarrow T_0$<br>$p \land F_0 \Leftrightarrow F_0$                                                             |
| Absorption Laws        | $p \lor (p \land q) \Leftrightarrow p$<br>$p \land (p \lor q) \Leftrightarrow p$                                                  |

All the laws, except for the Law of Double Negation, come in **pairs**.

If $s$ contains no logical connectives other than $\land,\lor$, then the **dual** of $s$ ($s^d$) is created by flipping $\land$ and $\lor$, and $T_0$ and $F_0$.

While  $s \not\Leftrightarrow s^d$, If $s \Leftrightarrow t$ then $s^d \Leftrightarrow t^d$


### First Substitution rule
The compound statement $P$ is a [[Connectives and Truth Table#Tautology and Contradiction|tautology]]. If $p$ is a primitive statement that appears in $P$ and we replace each occurrence of $p$ by the same statement $q$, then the resulting compound statement $P_1$ is also a tautology.

For example, $P$: $\lnot (p \lor q) \leftrightarrow (\lnot p \land \lnot q)$ is a tautology
- Replacing $p$ with $r\land s$
	- $P_1$: $\lnot [(r\land s)\lor q]\leftrightarrow[\lnot(r\land s)\land \lnot q]$
	- $P_1$ is *still a tautology*


### Second Substitution rule
If $p$ is a primitive statement that appears in $P$, and let $q$ be a statement such that $q\Leftrightarrow p$. Any of the $p$'s can be replaced with $q$ and the [[Connectives and Truth Table#Compound Statements|compound statement]] $P_1$ will be $P_1 \Leftrightarrow P$.

For example, $P$: $p\rightarrow(p\lor q)$
- Replacing the second $p$ with $\lnot\lnot p$ (since $p \Leftrightarrow \lnot\lnot p$)
- $P_1$: $p\rightarrow(\lnot\lnot p \lor q)$
	- $P_1 \Leftrightarrow P$


---

