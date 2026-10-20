Lecture 3

## Addition
In basic addition, there is a rule:
> The sum of any 3 single-digit numbers is at most two digits long.

For instance, the highest single digit number is $9$, and $9+9+9=27$, two digits long.

This rule works in binary as well: $1_{2}+1_{2}=10_{2}$, two bits long.

> [!tip] Binary
> A base 2 number (binary) consists of $0$s and $1$s. Where it is not obvious, a subscript $_{2}$ is placed under the number.

When we add numbers, we can stack the two numbers on top of each other, and add each digit. If there is an overflow, we take the **carry** and add it to the next digit. This diagram shows the process in base 2:
![[Screenshot 2026-10-19 at 3.01.44 AM.png|350]]

Back to the [[1_Algorithm#Algorithm|3 questions]] we ask about algorithms:
1. This is **correct** by definition.
2. For the running time, adding 2 $n$-bit numbers will require at most $n+1$ steps. Therefore, the [[2_Big O Notation#Big O Notation|Big O]] is:
$$
\boxed{ T(n)=O(n) }
$$

3. At minimum, we must read 2 $n$-bit numbers and write down the answer. That already requires a linear running time. The addition algorithm **is optimal**.


---
## Multiplication
When we multiply numbers, we multiply each digit of the first number to a digit of the second number, one at a time. For each digit of the second number, the intermediate values are **shifted** so that they are added later. This diagram shows the process in base 2:

![[Screenshot 2026-10-19 at 3.07.28 AM.png|400]]

1. This is **correct** by definition.
2. For the running time, we have $n$ intermediate rows with lengths up to $2n$ bits due to the shifts. Adding takes $O(n)$ for $n-1$ times.
$$
\boxed{ T(n)=O(n^{2}) }
$$

### Alternative algorithm
Al-Khwarizmi came up with an alternative algorithm. 
- Write the two numbers next to each other
- For each iteration
	- Divide the left column by 2, rounding down
	- Multiply the right column by 2
- Keep going until the left column gets down to 1
- Strike out rows where the left column is even
- Add up the right column

![[Screenshot 2026-10-19 at 3.12.51 AM.png|300]]

This algorithm is **essentially the same** as the algorithm above. It also has the same runtime $T(n)=O(n^{2})$.


### Division
To divide an integer $x$ by another integer $y\neq 0$, we need the **quotient** $q$ and the **remainder** $r$, where $x=yq+r$ and $r<y$.

Division, just like multiplication, takes quadratic time $\boxed{ T(n)=O(n^{2}) }$.

See more about quotient and remainder in [[4_Modular Arithmetic|Modular Arithmetic]].