
| Rule                             | Argument                                                                          | Description                                                                                                      |
| -------------------------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Modus Ponens**<br>(Detachment) | $p → q$<br>$p$<br>$\therefore q$                                                  | If $p$ is true, then $q$ must be true for the first statement is true.                                           |
| **Modus Tollens**                | $p → q$<br>$\neg q$<br>$\therefore \neg p$                                        | If $q$ is false, then $p$ has to be false for the first statement to be true.                                    |
| **Syllogism**                    | $p → q$<br>$q → r$<br>$\therefore p → r$                                          |                                                                                                                  |
| **Conjunction**                  | $p$<br>$q$<br>$\therefore p \land q$                                              | If both $p$ and $q$ are true, then the $\land$ of the two is true.                                               |
| **Conjunctive Simplification**   | $p \land q$<br>$\therefore p$                                                     | If both $p$ and $q$ are true, then $p$ is true.                                                                  |
| **Conjunctive Amplification**    | $p$<br>$\therefore p \lor q$                                                      | If $p$ is true, then $p$ $\lor$ with anything is still true.                                                     |
| **Disjunctive**                  | $p \lor q$<br>$\lnot p$<br>$\therefore q$                                         | If either $p$ or $q$ is true, and $p$ is false, then $q$ is true.                                                |
| **Contradiction**                | $\lnot p → F_0$<br>$\therefore p$                                                 | If (something) $→ F_0$ is true, then that something must be false.                                               |
| **Conditional Proof**            | $p \land q$<br>$p → (q → r)$<br>$\therefore r$                                    | Follow the arrow: <br>If $p$ and $q$ are both true, then $r$ has to be true for the second statement to be true. |
| **Proof by Cases**               | $p → r$<br>$q → r$<br>$\therefore(p \lor q) → r$                                  |                                                                                                                  |
| **Constructive Dilemma**         | $p → q$<br>$r → s$<br>$p \lor r$<br>$\therefore q \lor s$                         |                                                                                                                  |
| **Destructive Dilemma**          | $p → q$<br>$r → s$<br>$\lnot q \lor \lnot s$<br>$\therefore \lnot p \lor \lnot r$ |                                                                                                                  |

For laws of logic, see [[Logical Equivalence#The Laws of Logic]]

---
### Examples

See more on arguments: [[Implications and Argument#Argument]]

> Rita is baking a cake ($p$)
> If Rita is baking a cake, then she is not practicing her flute ($p → \lnot q$)
> If Rita is not practicing her flute, then her father will not buy her a car ($\lnot q → \lnot r$)
> Therefore, Rita's father will not buy a car ($\therefore \lnot r$)

| Steps | Expression               | Reasons                        |
| ----- | ------------------------ | ------------------------------ |
| 1     | $p → \lnot q$            | Premise                        |
| 2     | $\lnot q → \lnot r$      | Premise                        |
| 3     | $\therefore p → \lnot r$ | Step 1, 2 and Law of Syllogism |
| 4     | $p$                      | Premise                        |
| 5     | $\therefore \lnot r$     | Step 4, 3 and Modus Ponens     |



> $[(p → r)\land(r → s)\land(t \lor \lnot s)\land(\lnot t \lor u)\land(\lnot u)]→ \lnot p$

| Argument             |
| -------------------- |
| $p → r$              |
| $r → s$              |
| $t \lor \lnot s$     |
| $\lnot t \lor u$     |
| $\lnot u$            |
| $\therefore \lnot p$ |

| Steps | Expression                  | Reasons                              |
| ----- | --------------------------- | ------------------------------------ |
| 1     | $p → r$                     | Premise                              |
| 2     | $r → s$                     | Premise                              |
| 3     | $\therefore p → s$          | Steps 1, 2 and Law of Syllogism      |
| 4     | $t \lor \lnot s$            | Premise                              |
| 5     | $\therefore \lnot s \lor t$ | Step 4 and Commutative Law (flipped) |
| 6     | $\therefore s → t$          | Step 5 and Logical Equivalence       |
| 7     | $\therefore p → t$          | Steps 3, 6 and Law of Syllogism      |
| 8     | $\lnot t \lor u$            | Premise                              |
| 9     | $\therefore t → u$          | Step 8 and Logical Equivalence       |
| 10    | $\therefore p → u$          | Steps 7, 9 and Law of Syllogism      |
| 11    | $\lnot u$                   | Premise                              |
| 12    | $\therefore \lnot p$        | Steps 10, 11 and Modus Tollens       |




> If Margaret Thatcher is the prime minister of Canada, then she is at least 35 years old ($p → q$)
> Margaret Thatcher is at least 35 years old ($q$)
> Therefore, Margaret Thatcher is the prime minister of Canada ($p$)

| Argument       |
| -------------- |
| $p → q$        |
| $q$            |
| $\therefore p$ |

This is a **fallacy** because $[(p → q)\land q] → p$ is not a tautology.





> If 2+3=6, then 2+4=6 ($p → q$)
> 2+3 is not 6 ($\lnot q$)
> Therefore, 2+4 is not 6 ($\lnot q$)

| Argument             |
| -------------------- |
| $p → q$              |
| $\lnot q$            |
| $\therefore \lnot q$ |
This is also a **fallacy**.




> Establish the validity of the following:

| Argument                               |
| -------------------------------------- |
| $(\lnot p \lor \lnot q) → (r \land s)$ |
| $r → t$                                |
| $\lnot t$                              |
| $\therefore p$                         |

| Steps | Expression                             | Reasons                                                                                                                         |
| ----- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 1     | $r → t$                                | Premise                                                                                                                         |
| 2     | $\lnot t$                              | Premise                                                                                                                         |
| 3     | $\therefore \lnot r$                   | Steps 1, 2 and Modus Tollens                                                                                                    |
| 4     | $\lnot r \lor \lnot s$                 | Step 3 and Rule of Disjunctive Amplification<br>*Since $\lnot r$ is true, it can be $\lor$ with anything. $\lnot s$ is chosen.* |
| 5     | $\lnot (r \land s)$                    | Step 4 and DeMorgan's law                                                                                                       |
| 6     | $(\lnot p \lor \lnot q) → (r \land s)$ | Premise                                                                                                                         |
| 7     | $\lnot(\lnot p \lor \lnot q)$          | Steps 6, 5 and Modus Tollens                                                                                                    |
| 8     | $p \land q$                            | Step 7 and DeMorgan's law and Law of Double Negation                                                                            |
| 9     | $\therefore p$                         | Step 8 and Rule of Conjunctive Simplification<br>*If $p$ and $q$ are true, then $p$ must be true.*                              |





> Establish the validity of the following using proof by contradiction

| Argument                    |
| --------------------------- |
| $\lnot p \leftrightarrow q$ |
| $q → r$                     |
| $\lnot r$                   |
| $\therefore p$              |

| Argument<br>(contradiction) |
| --------------------------- |
| $\lnot p \leftrightarrow q$ |
| $q → r$                     |
| $\lnot r$                   |
| $\lnot p$                   |
| $\therefore F_0$            |
An extra premise, which is the negation of the conclusion, is added. If this results as a **contradiction**, this argument is valid.

| Step | Expression                        | Reason                                                                                                  |
| ---- | --------------------------------- | ------------------------------------------------------------------------------------------------------- |
| 1    | $\lnot p \leftrightarrow q$       | Premise                                                                                                 |
| 2    | $(\lnot p → q)\land(q → \lnot p)$ | Step 1 and Logical Equivalence                                                                          |
| 3    | $(\lnot p → q)$                   | Step 2 and Rule of Conj. Simpl.<br>*If the $\land$ is true, each statement is true*                     |
| 4    | $q → r$                           | Premise                                                                                                 |
| 5    | $\lnot p → r$                     | Steps 3, 4 and Law of Syllogism                                                                         |
| 6    | $\lnot p$                         | Premise                                                                                                 |
| 7    | $r$                               | Steps 5, 6 and Modus Ponens                                                                             |
| 8    | $\lnot r$                         | Premise                                                                                                 |
| 9    | $r \land \lnot r$                 | Steps 7, 8 and Rule of Conjunction<br>*If two things are true, then $\land$ of the two things are true* |
| 10   | $F_0$                             | Contradiction function                                                                                  |
| 11   | $\therefore p$                    | Original conclusion is true                                                                             |






> Establish the validity of the following

| Argument                   |
| -------------------------- |
| $u → r$                    |
| $(r \land s) → (p \lor t)$ |
| $q → (u \land s)$          |
| $\lnot t$                  |
| $\therefore q → p$         |

| Argument (modified)        |
| -------------------------- |
| $u → r$                    |
| $(r \land s) → (p \lor t)$ |
| $q → (u \land s)$          |
| $\lnot t$                  |
| $q$                        |
| $\therefore p$             |
This modification works because: $x → y → z \Leftrightarrow (x \land y) → z$

| Step | Expression                 | Reason                                                                                         |
| ---- | -------------------------- | ---------------------------------------------------------------------------------------------- |
| 1    | $q$                        | Premise                                                                                        |
| 2    | $q → (u \land s)$          | Premise                                                                                        |
| 3    | $u\land s$                 | Steps 1, 2 and Modus Ponens                                                                    |
| 4    | $u$                        | Step 3 and Rule of Conj. Simpl.<br>*If $u$ and $s$ are true, then $u$ is true and $s$ is true* |
| 5    | $u → r$                    | Premise                                                                                        |
| 6    | $r$                        | Step 4, 5 and Modus Ponens                                                                     |
| 7    | $s$                        | Step 4 and Rule of Conj. Simpl.                                                                |
| 8    | $r \land s$                | Steps 6, 7 and Rule of Conjunction                                                             |
| 9    | $(r \land s) → (p \lor t)$ | Premise                                                                                        |
| 10   | $p\lor t$                  | Step 9 and Modus Ponens                                                                        |
| 11   | $\lnot t$                  | Premise                                                                                        |
| 12   | $\therefore p$             | Steps 10, 11 and Rule of Disjunctive Syllogism                                                 |






> Show that the following is an **invalid** argument

| Argument                       |
| ------------------------------ |
| $p$                            |
| $p \lor q$                     |
| $q → (r → s)$                  |
| $t → r$                        |
| $\therefore \lnot s → \lnot t$ |
Rules of inference are not used. 
Only need to find one set of $p$, $q$, $r$, and $s$ where the conclusion is false. 
- All the premises have to be **true**
- This only works when showing that an argument is invalid.

 $p$ is a premise, then $p=1$

When is the conclusion false?
- since $1 → 0$ is false
- $\lnot s$ has to be $1$
	- $s=0$
- $\lnot t$ has to be $0$
	- $t=1$

The premise $t → r$ has to be true, so since $t=1$, $r=1$

For the premise $q → (r → s)$:
- since $r=1$ and $s=0$, then $r → s=0$
- $q → 0$ has to be true
- $q=0$

A set of all variables which make all premises true and the conclusion false is:
- $p=1$
- $q=0$
- $r=1$
- $s=0$

**This is an invalid argument.**






> What can we say about the validity or invalidity of the following argument?

| Argument             |
| -------------------- |
| $p → q$              |
| $q → s$              |
| $r → \lnot s$        |
| $\lnot p \oplus r$   |
| $\therefore \lnot p$ |
Assume it is either valid or invalid. 
In this case, **assume it is invalid**. 
- Find a set of variable that makes all the premises true but the conclusion false.

Making the conclusion false, $p=1$

From the premise $p → q$, since $p=1$, then $q=1$

From the premise $q → s$, since $q=1$, then $s=1$

From the premise $r → \lnot s$, since $s=1$, then $\lnot s=0$, then $r=0$

If $p=1$ ($\lnot p=0$) and $r=0$, then $\lnot p \oplus r$ is **false**.

We have failed to show that this argument is invalid.


Then, **assume** this **argument is valid**. 
Prove by contradiction:

| Argument           |
| ------------------ |
| $p → q$            |
| $q → s$            |
| $r → \lnot s$      |
| $\lnot p \oplus r$ |
| $\lnot \lnot p$    |
| $\therefore F_0$   |

Prove by contradiction

| Step | Expression                                      | Reason                                |
| ---- | ----------------------------------------------- | ------------------------------------- |
| 1    | $p → q$                                         | Premise                               |
| 2    | $p$                                             | Premise                               |
| 3    | $q$                                             | Steps 1, 2 and Modus Ponens           |
| 4    | $q → s$                                         | Premise                               |
| 5    | $s$                                             | Steps 3, 4 and Modus Ponens           |
| 6    | $r → \lnot s$                                   | Premise                               |
| 7    | $\lnot r$                                       | Steps 5, 6 and Modus Tollens          |
| 8    | $\lnot p \oplus r$                              | Premise                               |
| 9    | $(\lnot p \lor r)\land \lnot (\lnot p \land r)$ | Step 8 and Logical Equivalence        |
| 10   | $(\lnot p \lor r)\land (p \lor \lnot r)$        | Step 9 and DeMorgan's Law             |
| 11   | $\lnot p \lor r$                                | Step 10 and Conjunctive Amplification |
| 12   | $r$                                             | Steps 11, 2 and Disjunctive           |
| 13   | $r \land \lnot r$                               | Step 12 and Conjunction               |
| 14   | $F_0$                                           | Contradiction function                |
| 15   | $\therefore \lnot p$                            | Original conclusion is true           |

**This argument is valid.**

