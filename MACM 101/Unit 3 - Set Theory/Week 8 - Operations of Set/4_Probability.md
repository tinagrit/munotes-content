Section 3.4

## Sample space

If we perform an **experiment** such as tossing a single fair coin, rolling a single fair die, or selecting two students at random from a class of 20, 

The [[Sets and Subsets|set]] of *all possible outcomes* for each situation is called a **sample space**.

The sample spaces for each of the above are:
- Tossing a coin: $\{H,T\}$
- Rolling a die: $\{1,2,3,4,5,6\}$
- Choosing 2 students out of 30: $\{(a_i,a_j)|1\leq i \leq 30, 1 \leq j \leq 30, i \neq j \}$

$\Omega$  denotes the sample space

---
## Probability definition

Let $\Omega$ be the sample space for an experiment. Each subset $A$ of $\Omega$, including $\varnothing$, is called an **event**. Each element of $\Omega$ is called an **outcome**.

If $|\Omega|=n$,  $a\in \Omega$,  $a\subseteq \Omega$, then:
- $Pr(a)$  = The probability that $\{a\}$ occurs
	- $\dfrac{|\{a\}|}{|\Omega|}=\dfrac{1}{n}$
- $Pr(A)$  = The probability that $A$ occurs
	- $\dfrac{|A|}{|\Omega|}=\dfrac{|A|}{n}$

### Examples

> When Daphne tosses a fair coin, what is the probability she gets a head?

$\Omega = \{H,T\}$
$A=\{H\}$

$Pr(A)=\dfrac{|A|}{|\Omega|}=\dfrac{1}{2}$



> If Daphne rolls a die, what is the probability she gets a 5 or a 6?

$\Omega = \{1,2,3,4,5,6\}$
$A=\{5,6\}$

$Pr(A)=\dfrac{|A|}{|\Omega|}=\dfrac{2}{6}=\dfrac{1}{3}$

> What is the probability she gets an even number?

$\Omega = \{1,2,3,4,5,6\}$
$A=\{2,4,6\}$

$Pr(A)=\dfrac{|A|}{|\Omega|}=\dfrac{3}{6}=\dfrac{1}{2}$

Other results:

$Pr(\Omega)=\dfrac{|\Omega|}{|\Omega|}=1$

$Pr(\overline A)=\dfrac{|\{1,2,3,4\}|}{|\Omega|}=\dfrac{4}{6}=\dfrac{2}{3}=1-\dfrac{1}{3}=1-Pr(A)$



> Suppose a teacher wants to choose 2 students out of 20 to take care of the class rabbit. What is the sample space of making this choice?

$\Omega=\{(a_i,a_j)|1\leq i \leq 20, 1 \leq j \leq 20, i \neq j\}$

$|\Omega|=\dbinom{20}{2}=190$

> Suppose Kyle and Cody are two students in the 20. Let $A$ be the event that Kyle is one of the students selected, and $B$ be the event that Cody is one of the students selected. When the teacher chooses two students at random, what is the probability that both Kyle and Cody are chosen?

$Pr(A\cap B)$

$=\dfrac{|A\cap B|}{|\Omega|}=\dfrac{\dbinom{2}{2}}{190}=\dfrac{1}{190}$

> What is the probability that neither Kyle nor Cody are chosen?

$Pr(\overline A \cap \overline B)$

$=\dfrac{\dbinom{18}{2}}{190}=\dfrac{153}{190}$

> What is the probability that Kyle is chosen but not Cody?

$Pr(A\cap \overline B)$

$=\dfrac{\dbinom{1}{1}*\dbinom{18}{1}}{190}=\dfrac{18}{190}=\dfrac{9}{95}$

