Lecture 6

## Uniform Probability Space

A [[2_Axioms#Probability Function|probability space]] is **uniform** if the outcome (result of $\text{Pr}[w]$) is the same for all $w \in S$.

Therefore, each outcome probability is simply:
$$
\text{Pr}[w]=\dfrac{1}{|S|}
$$

Similarly, for an event $E \subseteq S$:
$$
Pr[E]=\dfrac{|E|}{|S|}
$$

For example, rolling a 6-sided die, every face is equally as likely to show. Therefore, the probability space **is uniform***.
- The probability for each face outcome is $\dfrac{1}{|S|}=\dfrac{1}{6}$
- The probability to roll 2 of the faces, for example, 5 and 6, is $\dfrac{2}{|S|}=\dfrac{2}{6}=\dfrac{1}{3}$


> Consider an exam with $m$ mathematics students and $n$ non-mathematics students. Ranking their performances with no ties, find the probability that all mathematics students are the top $m$.

Finding the sample space, the total number of rankings is the [[3_Permutations#Permutation|permutations]], $(m+n)!$

Finding the events, we "lock" the first 4 spots for mathematics students ($m!$) in their permutation, and the rest 6 spots for non-mathematics students ($n!$) in their permutation. Using the [[3_Permutations#Product Rule Counting|product rule]], the total number of events is $m!n!$.

Therefore, the probability is $\dfrac{m!n!}{(m+n)!}$.


> Consider the same exam, find the probability that $t$ mathematics students are the top $t$.

We need to first select $t$ students from $m$ mathematics students to be the top. Using [[4_Combinations#Combinations|Combinations]], we can do so by $\dbinom{m}{t}$.

For each way, we can arrange the top $t$ students $t!$ ways, and the rest of the students $(m+n-t)!$ ways.

Using the same sample space from above, the probability is $\dfrac{\binom{m}{t}t!(m+n-t)!}{(m+n)!}$

