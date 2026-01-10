Lecture 2

## Bijection Counting
- Mapping a problem to an easier set, then count the set
- Create **all possible sequences** from the problem
- Use **binary** [[3_Sequences#Sequences|sequences]] where components are $\in \left\{ 0,1 \right\}$

> Consider buying 10 donuts with 5 different flavours. We can use:
> - $0$s to count the number of donuts
> - $1$s to separate each flavour

For example, the sequence $0000$ $1$ $00$ $1$ $0$ $1$ $00$ $1$ $0$
- Translated as $4/2/1/2/1$ (number of $0$s separated by $1$s)
- Number of donuts for each flavour

A sequence contains exactly 1 **unique** mapping, making it a [[2_Functions#Bijective|bijective]] mapping
- The above sequence can only mean:
- "4 donuts of the first flavour, 2 of the second flavour, 1 of the third flavour, 2 of the fourth flavour, 1 of the fifth flavour"
- and cannot mean anything else

When we have a **bijective mapping**, we know that the domain $|A|$ is **equal to** the codomain $|B|$, and we can **count the sequences** instead.

To count the number of possible sequences,
- In this case, there are 14 spots in the sequence (10 donuts + 4 separators)
- We only need to insert 4 $1$s anywhere on the sequence
- We can "**choose**" 4 spots out of 14 for the $1$s to be placed on, a combination problem

*Read more on Combinations at* [MACM 101 > Combinations with no repetition](https://munotes.tinagrit.com/MACM101/unit-1-combinatorics/week-2-combinations-and-repetition/combinations-with-no-repetition.html)
The answer is:
$$
\dbinom{14}{4}=\dfrac{14!}{4!(14-4)!}=1,001
$$


### Generalizing
In general, to select $n$ elements with $k$ options, count the number of:
- sequences of length $(n+k-1)$
- with $(k-1)$ number of $1$s

Therefore, the answer is:
$$
\dbinom{n+k-1}{k-1}
$$
