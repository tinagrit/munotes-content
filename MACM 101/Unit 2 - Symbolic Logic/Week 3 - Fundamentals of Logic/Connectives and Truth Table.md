
## Statements (propositions)
- declarative sentences that are either **TRUE** or **FALSE**.
- This is denoted using $p$, $q$, etc.
- For example:
	- $p$: Combinatorics is a required course for sophomores
	- $q$: Margaret Mitchell wrote *Gone with the Wind*
	- $r$: 2+3=5
- Not:
	- "What a beautiful morning!" since it is an *exclamation*
	- "Get up and do your exercises" since it is a *command*

### Primitive Statements
- statements that cannot be broken down into anything simpler
### Compound Statements
- combined from primitive statements by **logical connectives** or by **negation** (NOT $\lnot p$)
- Logical connectives include:
	- Conjunction (AND) $p\land q$
	- Disjunction (OR) $p\lor q$
	- Exclusive or (XOR) $p\oplus q$ or $p \veebar q$
	- Implication (If.. then.. or implies) $p\rightarrow q$
	- Bi-conditional (..if and only if.. or iff) $p\leftrightarrow q$

> "The number $x$ is an integer" is not a statement until $x$ is given a numerical value.

---

## Truth Tables

| $p$ | $q$ | $p\land q$ | $p \lor q$ | $p \oplus q$ | $p → q$ | $p\leftrightarrow q$ |
| --- | --- | ---------- | ---------- | ------------ | ------- | -------------------- |
| 🔴  | 🔴  | 🔴         | 🔴         | 🔴           | 🟢      | 🟢                   |
| 🔴  | 🟢  | 🔴         | 🟢         | 🟢           | 🟢      | 🔴                   |
| 🟢  | 🔴  | 🔴         | 🟢         | 🟢           | 🔴      | 🔴                   |
| 🟢  | 🟢  | 🟢         | 🟢         | 🔴           | 🟢      | 🟢                   |

- $p \oplus q$ is only true when ONE of $p,q$ is true

- $p\rightarrow q$ is like a promise
	- For example, "The vending machine will give you food if you pay"
		- If you haven't paid, whatever the machine does wouldn't break the promise
		- If you have paid, the machine would break the promise if it won't give you food

- $p \leftrightarrow q$ is checking if $p=q$

### Examples

> Consider the statements
> - $s$: Phyllis goes out for a walk
> - $t$: The moon is out
> - $u$: It is snowing
> **If the moon is out and it is not snowing, then Phyllis goes out for a walk**

- If the moon is out ($t$)
- It is not snowing ($\lnot u$)
- Phyllis goes out for a walk ($s$)

$(t\land \lnot u) \rightarrow s$


---

## Tautology and Contradiction

**Tautology** ($T_0$) is a compound statement if it is true for all truth value assignments for its component statements

**Contradiction** ($F_0$) is a compound statement if it is false for all such assignments


> $p \rightarrow (p \lor q)$

| $p$ | $q$ | $p \lor q$ | $p \rightarrow (p \lor q)$ |
| --- | --- | ---------- | -------------------------- |
| 🔴  | 🔴  | 🔴         | 🟢                         |
| 🔴  | 🟢  | 🟢         | 🟢                         |
| 🟢  | 🔴  | 🟢         | 🟢                         |
| 🟢  | 🟢  | 🟢         | 🟢                         |
-  $p \rightarrow (p \lor q)$ is a *tautology*


> $p \land (\lnot p \land q)$

| $p$ | $q$ | $\lnot p$ | $\lnot p \land q$ | $p \land (\lnot p \land q)$ |
| --- | --- | --------- | ----------------- | --------------------------- |
| 🔴  | 🔴  | 🟢        | 🔴                | 🔴                          |
| 🔴  | 🟢  | 🟢        | 🟢                | 🔴                          |
| 🟢  | 🔴  | 🔴        | 🔴                | 🔴                          |
| 🟢  | 🟢  | 🔴        | 🔴                | 🔴                          |
- $p \land (\lnot p \land q)$ is a *contradiction*


---

## Arguments

Consider an argument that contains the premises $p_1,p_2,\ldots,p_n$ and a conclusion $q$

$(p_1\land p_2 \land p_3 \land \ldots \land p_n) \rightarrow q$

If any one of $p_1,p_2,\ldots,p_n$ is 🔴, then no matter what truth value $q$ has, the implication is 🟢.
- A **valid** argument is a **tautology**