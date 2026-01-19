Lecture 4

## Inclusion-Exclusion Principle

For $A,B$ [[1_Sets#Set operations|disjoint]] [[1_Sets#Sets|sets]], $|A\cup B|=|A|+|B|$.
Since nothing shares, the size of both sets is simply the size of each set added up.

If they are not disjoint, however:
![[chart14.png|350]]

Notice that if we do the addition above, the middle part ($A\cap B$) is counted twice. We can remove the part that they share, to subtract the overcounting.
$$
|A\cup B|=|A|+|B|-|A\cap B|
$$

If there are 3 sets, notice that if we subtract ($A \cap C$), ($A\cap B$), ($B \cap C$) from ($|A|+|B|+|C|$), the very middle part ($A\cap B\cap C$) is subtracted completely.
![[chart15.png|350]]

We can add it back after the subtraction.
$$
|A\cup B\cup C|=|A|+|B|+|C|-|A\cap B|-|A\cap C|-|B\cap C|+|A\cap B\cap C|
$$


> Suppose there are:
> - $60$ Math majors ($M$)
> - $200$ Engineering majors ($E$)
> - $40$ Physics majors ($P$)
> 
> Out of the students, there are:
> - $4$ Math-Engineering only students
> - $3$ Math-Physics only students
> - $11$ Engineering-Physics only students
> - $2$ triple majors
> 
> Find the total number of students

Using the three-set inclusion-exclusion rules, we can find $|M\cup E\cup P|$ with:
$$
=|M|+|E|+|P|-|M\cap E|-|M\cap P|-|E\cap P|+|M\cap E\cap P|
$$

Note that for the double major students, for example, the $4$ Math-Engineering **ONLY** students do not include the $2$ triple majors. Therefore, the total of all Math-Engineering students ($M\cup E$) is $4+2=6$. This is the case for all double majors.

![[chart16.png|500]]

Substituting:
$$
=60+200+40-(4+2)-(3+2)-(11+2)+2
$$
$$
=278
$$
 


### Generalization
For $n$ sets (as opposed to 2,3), we can compute the size of the union by:
$$
\sum_{i}^{}|A_{i}|-\sum_{i,j}^{}|A_{i}\cap A_{j}|+\sum_{i,j,k}^{}|A_{i}\cap A_{j}\cap A_{k}|+\dots+(-1)^{n-1} |A_{1}\cap A_{2} \cap \dots \cap A_{n}|  
$$

