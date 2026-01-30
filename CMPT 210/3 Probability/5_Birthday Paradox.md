Lecture 6

## Birthday Paradox

Suppose there are $367$ students in a class. A maximum number of days in a year is $366$. Therefore, by the [[8_Pigeonhole Principle#Pigeonhole Principle|Pigeonhole Principle]], two students **must share** a birthday.

The [[2_Axioms#Probability Function|probability]] of this event (sharing a birthday) happening is $1$ ($100\%$).

Now, suppose there are $n$ students in the class, and we want to find the probability that two students share a birthday, given that:
- no leap years, all years have $d$ days
- each student is equally likely to be born on any day
- one's birthday is independent of each other

The [[1_Probability#Sample Space|sample space]] is the number of **possible outcomes of birthdays**. In this case, is $d^{n}$, since each student is one of $d$ options.
$$
S=d^{n}
$$

The event that **no one shares birthday** is:
$$
E_{\text{no share}}=d\times (d-1)\times (d-2)\times \dots \times (d-(n-1))
$$
and
$$
\text{Pr}[E_{\text{no share}}]=\dfrac{d\times (d-1)\times (d-2)\times \dots \times (d-(n-1))}{d^{n}}
$$

Therefore, the probability that **at least two students share** a birthday is:
$$
1-\text{Pr}[E_{\text{no share}}]
$$
$$
=1-\dfrac{d\times (d-1)\times (d-2)\times \dots \times (d-(n-1))}{d^{n}}
$$

The second term ($\text{Pr}[E_{\text{no share}}]$) can be derived as being $\leq e^{ -\frac{n(n-1)}{2d}  }$. We can rewrite the expression as:
$$
1-\text{Pr}[E_{\text{no share}}]\geq 1-\exp \left( -\dfrac{n(n-1)}{2d} \right) 
$$

### Generalizing
Therefore, if we have $n$ items and $d$ containers, the probability that two items **occupy the same container** is at least:
$$
\geq 1-\exp \left( -\dfrac{n(n-1)}{2d} \right) 
$$
