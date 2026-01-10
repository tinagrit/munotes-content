Lecture 2

## Product Rule Counting
*Read more at* [MACM 101 > Combinatorics Introduction](https://munotes.tinagrit.com/MACM101/unit-1-combinatorics/week-1-fundamental-principles-of-counting/combinatorics-introduction.html)

Counting [[3_Sequences#Sequences|sequences]] of $k$ components where:
- the first entry can be selected from $n_{1}$ ways
- the second entry can be selected from $n_{2}$ ways
- $\dots$
- the $k$th entry can be selected from $n_{k}$ ways

The sum of all sequences is the **product** of all $n$s
$$
|A|=n_{1}\times n_{2}\times\dots \times n_{k}
$$


> Consider course selection, where a student needs to choose
> - 1 course from the set of $S$ statistics courses
> - 1 course from the set of $C$ computing courses
> - 1 course from the set of $M$ mathematics courses

The total number of ways to select 3 courses is:
$$
|S|\times |C|\times |M|
$$


> Consider creating a password of length $n$, where each character is a lowercase letter $c \in \left\{ a,b,c,d,\dots,y,z \right\}$

The total number of passwords is:
$$
26^{n}
$$


> Consider distributing $p$ prizes to $n$ students, where no student receives more than one prize

- The first prize can be given out to one of $n$ students
- The second prize to one of $n-1$ students (first chosen one excluded)
- The third prize to one of $n-2$ students
- $\dots$
- The $p$th prize to one of $n-p+1$ students

Therefore, the total number of ways to distribute is:
$$
n\times (n-1)\times (n-2)\times\dots (n-p+1)
$$


> Consider an 8-digit serial number that is only valid if a digit does not appear more than once. 

- The first digit can be one of $10$ numbers $(0,1,2,3,\dots,9)$
- The second digit can be one of $9$ numbers (first chosen one excluded)
- The third digit can be one of $8$ numbers
- $\dots$
- The eighth digit can be one of $3$ numbers

Therefore, the total number of valid serial numbers is:
$$
10\times 9\times 8\times \dots \times 3
$$

The fraction of valid serial numbers (out of all serial numbers) is:
$$
\dfrac{10\times 9\times 8\times \dots \times 3}{10^{8}}
$$


### Permutation
The permutation of a [[1_Sets#Sets|set]] $A$ is a [[3_Sequences#Sequences|sequence]] of length $|A|$ that contains all elements of $A$ exactly once

For example, for $A=\left\{ a,b,c \right\}$, the permutations of $A$ are:
- $(a,b,c)$, $(a,c,b)$, $(b,c,a)$, $(b,a,c)$, $(c,a,b)$, $(c,b,a)$

We can find the total number of permutations with the Product Rule

> Consider the set $A=\left\{ a_{1},a_{2},\dots,a_{n} \right\}$

- The first spot in the sequence can be one of $n$ options
- The second spot can be one of $n-1$ options (first chosen one excluded)
- The third spot can be one of $n-2$ options
- $\dots$
- The $n$th (last) spot can be $1$ option (the last unchosen)

Therefore, the total number of permutations is:
$$
n\times(n-1)\times(n-2)\times\dots \times 1
$$
This is equal to the **factorial** of $n$, and therefore, we have
$$
n!
$$
permutations.

> [!tip] By convention, $0! =1$

