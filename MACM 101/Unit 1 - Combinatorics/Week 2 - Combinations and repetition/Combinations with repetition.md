The number of selections, **with repetitions**, of $r$ objects from $n$ distinct objects are:$$\frac{(n+r-1)!}{r!(n-1)!}$$ which is equivalent to $C(n+r-1,r)$ or $\dbinom{n+r-1}{r}$

---

### Examples

> Distributing $1000 in units of $100 to 4 people. Since there are only 4 people for 10 notes, each person can be chosen more than once

- $n$ = $4$
- $r$ = $10$

- The total number of combinations is $\dbinom{4+10-1}{10}=286$ ways


> A message is made up of 12 different symbols and is to be transmitted through a communication channel. The transmitter will send the total number of 45 blank spaces between the symbols, with at least three blank spaces between each pair of consecutive symbols. How many ways can the transmitter send such a message?

- **Arranging the letters**
	- The total number of ways to arrange the letters is $P(12,12)=12!$

- **Arranging the spaces**
	- There would be 11 positions of spaces between the 12 symbols
		- With at least 3 blank spaces between each pair, $11*3=33$ blank spaces have to be used up.
	- Choosing the position, $n=11$ and $r=45-33=12$
		- The are $\dbinom{11+12-1}{12}$ ways to distribute the remaining spaces

Using the [[Combinatorics Introduction#The Product Rule|product rule]], there are $12!*\dbinom{11+12-1}{12}$ ways to send the message.


> Determine all integer solutions to the equation
> $x_1+x_2+x_3+x_4=7$
> where $x_i\geq0$ for all $1\leq{i}\leq{4}$

- Distributing the 7 into all X's
- $n=4$ and $r=7$
- There are $\dbinom{4+7-1}{7}=120$ solutions

#### Inequality

> Determine all non-negative integer solutions to the **inequality**
> $x_1+x_2+x_3+\ldots+x_6<10$

$x_7$ is added such that $x_7=10-(x_1+x_2+x_3+\ldots+x_6)$

The **equation** is now: $x_1+x_2+x_3+x_4+x_5+x_6+x_7=10$
for all $x_i\geq0$,        $1\leq i\leq6$,        $x_7>0$  (since the sum can't be 10)

Since $x_7$ cannot be 0, the combination with repetition formula doesn't work right away.
- $1$ will be subtracted from both sides so that $x_7$ can be $0$

$y_1+y_2+y_3+y_4+y_5+y_6+y_7=9$
for all $x_i=y_i$,        $1\leq i\leq6$,        $y_7=x_7-1 \geq0$

- $n=7$ and $r=9$
- There are $\dbinom{7+9-1}{9}=5,005$ solutions

---

### Compositions

> Find all the different ways to write the number **4** as a sum of positive integers, where the order of the summands is considered relevant. The "composition of 4"

The compositions of 4 include:
- $4$
- $3+1$
- $1+3$
- $2+2$
- $2+1+1$
- $1+2+1$
- $1+1+2$
- $1+1+1+1$

There are $8$ compositions of 4


> How many compositions are there for the number **7**

**Case 1**: 1 summand
- $1$ composition (just 7)
	- same as $\dbinom{6}{6}$

**Case 2**: 2 summands
- $w_1+w_2=7$ where $w_i>0$
- Since $w_1$ and $w_2$ cannot be 0, the same trick from [[#Inequality]] has to be used.
	- $1$ will be subtracted from both $w_1$ and $w_2$
- $x_1+x_2=5$ where $x_i\geq0$ ($x_1=w_1-1,x_2=w_2-1$)
- There are $\dbinom{2+5-1}{5}=\dbinom{6}{5}$ compositions

**Case 3**: 3 summands
- $y_1+y_2+y_3=7$ where $y_i>0$
- Then: $z_1+z_2+z_3=4$ where $z_i\geq0$
- There are $\dbinom{3+4-1}{4}=\dbinom{6}{4}$ compositions

[[Combinatorics Introduction#The Sum Rule|Sum rule]] is used since options are not chosen one after the other.
The total number of compositions is
$\displaystyle{6\choose6}+{6\choose5}+{6\choose4}+{6\choose3}+{6\choose2}+{6\choose1}+{6\choose0}$ = $\displaystyle\sum_{k=0}^{6}{6\choose k}$

According to the [[Combinations with no repetition#Corollaries|corollaries]], this answer is just:
- $2^6$

---

### Runs

> Find the total number of ways 5 E’s and 10 O’s can determine 7 runs
> For example:
> $OO$   $E$   $OOOO$   $EEE$   $OOO$   $E$   $O$
> A run refers to a chuck of identical letters followed and preceded by different or no entries at all

If the first run is $O$, there are 4 runs of O's and 3 runs of E's
If the first run is $E$, there are 3 runs of O's and 4 runs of E's

**Case 1**: first run is $E$
- For the 4 E's: $t_1+t_3+t_5+t_7=5$ where $t_i>0$
	- $T_1+T_3+T_5+T_7=1$ where $T_i\geq0$
	- There are $\dbinom{4+1-1}{1}=\dbinom{4}{1}=4$ ways
- For the 3 O's: $t_2+t_4+t_6=10$ where $t_i>0$
	- $T_2+T_4+T_6=7$ where $T_i\geq0$
	- There are $\dbinom{3+7-1}{7}=\dbinom{9}{7}=36$ ways
- There are $4*36=144$ total ways for this case

**Case 2**: first run is $O$
- For the 4 O's: $t_1+t_3+t_5+t_7=10$ where $t_i>0$
	- $T_1+T_3+T_5+T_7=6$ where $T_i\geq0$
	- There are $\dbinom{4+6-1}{6}=\dbinom{9}{6}=84$ ways
- For the 3 E's: $t_2+t_4+t_6=5$ where $t_i>0$
	- $T_2+T_4+T_6=2$ where $T_i\geq0$
	- There are $\dbinom{3+2-1}{2}=\dbinom{4}{2}=6$ ways
- There are $84*6=504$ total ways for this case

The total number of ways is $144+504=648$.

