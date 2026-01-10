Lecture 2

## Sum Rule Counting
*Read more at* [MACM 101 > Combinatorics Introduction](https://munotes.tinagrit.com/MACM101/unit-1-combinatorics/week-1-fundamental-principles-of-counting/combinatorics-introduction.html)

If we have [[1_Sets#Set operations|disjoint sets]], then the sum of all elements is the [[1_Sets#Sets|cardinality]] of each set added up

Formally, for $A_{1},A_{2},\dots,A_{n}$ disjoint:
$$
|A_{1} \cup A_{2}\cup \dots\cup A_{n}|=\sum_{i=1}^{m}|A_{i}|
$$
$$
 = |A_{1}|+|A_{2}|+\dots+|A_{n}|
$$


> Consider a bad day being either snowy, rainy, or hot. Let:
> - $S$ be the set of snowy days in 2025
> - $R$ be the number of rainy days in 2025
> - $H$ be the number of hot days in 2025
> Assume one day can have one weather

To count the total number of bad days,
- Since $S$, $R$, $H$ are disjoint, we can add the cardinality of each set up
- Therefore, the number of bad days is $|S|+|R|+|H|$

The number of good days is simply $365-(|S|+|R|+|H|)$



