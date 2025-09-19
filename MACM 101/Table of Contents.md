
### Chapter 1
- 1.1: [[Combinatorics Introduction|Sum and Product Rules]]
- 1.2: [[Permutations|Permutations]]
- 1.3: [[Combinations with no repetition|Combinations with no repetition]]
	- [[Combinations with no repetition#The Binomial Theorem|The Binomial Theorem]]
- 1.4: [[Combinations with repetition]]

### Chapter 2
- 2.1: [[Connectives and Truth Table]]
- 2.2: [[Logical Equivalence|Logical Equivalence]]
	- [[Logical Equivalence#The Laws of Logic|The Laws of Logic]]
	- [[Implications and Argument]]
- 2.3: [[Inference rules|Rules of Inference]]
- 2.4: [[Quantifiers|Quantified logic statements]]
- 2.5: Quantifiers and the Proofs of Theorem
	- [[The Proof of Theorems#Rule of Universal Specification|Rules of universal specification/generalization]]
	- [[The Proof of Theorems|Conventional proof]]

### Chapter 3
- 3.1 and 3.2: Sets, Set Operations, and the Laws of Set Theory
	- [[Sets and Subsets|Sets]] and [[1_Operations of Set|operators]]
	- Proving theorems using the [[2_The Laws of Set Theory|laws of set theory]]
- 3.3: [[3_Venn Diagrams|Counting and Venn Diagrams]]
- 3.4: [[4_Probability|Probability]]

### Chapter 4
- 4.1: Well-Ordering Principle
	- [[1_Induction|Mathematical Induction]]
	- [[1_Induction#Alternate form (strong induction)|Strong induction]]
- 4.2: Recursive Definitions
	- Using induction to prove theorems involving [[2_Recursion|recursive definitions]]
- 4.3: [[1_Integer division|Division Algorithm]]
	- [[1_Integer division#Prime numbers|Prime numbers]]
	- [[1_Integer division#"The Theorem"|The Theorem (7 part division theorem)]]
	- [[1_Integer division#Lemma|Lemma]]
	- [[1_Integer division#Euclid's theorem|Euclid's Theorem]]
- 4.4: [[2_Greatest common divisor|Greatest common divisor]]
- 4.5: [[1_Arithmetic|Theorem of Arithmetic]]

### Chapter 5
- 5.1: Relations
	- [[1_Relations#Cartesian product|Cartesian product]]
	- [[1_Relations#Relations|Relations]]
- 5.2: [[2_Functions|Functions]]
	- [[2_Functions#One-to-one functions|One-to-one functions]]
	- [[2_Functions#Images of subsets|Images of subsets]]
- 5.3: [[2_Functions#Onto functions|Onto functions]]
- 5.4: [[3_Special Functions|Special functions]]
- 5.5: [[2_Pigeonhole Principle|The Pigeonhole Principle]]
- 5.6: Function operations
	- [[1_Composition and Inverse#Composite functions|Composition]]
	- [[1_Composition and Inverse#Invertible functions|Inverse]]
	- [[1_Composition and Inverse#Associativity|Function associativity]]


---

## Review questions

### From Midterm 2

> Prove that if $x$ and $y$ are positive integers and $x<y$, then $x^2<y^2$

> [!example]- Answer key
> - Using [[The Proof of Theorems#Direct proof|Direct proof]]:
> - With the assumption of $x<y$:
>	- Since $x$ is a positive integer by assumption, multiplying both sides of the inequality by $x$ will maintain the inequality
>		- $\implies x\cdot x<x\cdot y$
>		- $\implies x^2 < xy$
>	- Since $y$ is a positive integer by assumption, multiplying both sides of the inequality by $y$ will maintain the inequality
>		- $\implies x\cdot y < y\cdot y$
>		- $\implies xy<y^2$
>- Since $x<y$ implies that $x^2 < xy$ and $xy<y^2$ are true, it follows that:
>	- $\implies x^2<xy<y^2$
>	- $\implies x^2<y^2$
>- Therefore, if $x,y$ are positive integers such that $x<y$, then $x^2<y^2$


> Using induction, prove that a set with $n$ elements has $2^n$ subsets

> [!example]- Answer key
> - **Basis**:
> 	- $n=1$, i.e. $S=\{a\}$ has 2 subsets, $a$ and $\varnothing$
> 	- $2^n=2^1=2$
> - **Induction**:
> 	- Assume $S(k)$:
> 		- A set of size $k$ has $2^k$ subsets
> 	- Show that $S(k+1)$ is true
> 		- A set of size $k+1$ has $2^{k+1}$ subsets
> 	- Let $|A|=k$. $A$ has $2^k$ subsets by the assumption
> 	- Let $B=A+$ an extra element that is not already in the $A$ 
> 	- $|B|=k+1$
> 	- All the subsets of $A$ are also subsets of $B$
> 	- Add the extra element to each subset of $A$
> 	- Therefore, the number of subsets for $B=2\cdot$ number of subsets of $A$ 
> 	- $\implies$ Number of subsets of $B=2\cdot 2^{k}$
> 	- $\implies$ Number of subsets of $B=2^{k+1}$
> 	- Therefore, a set of size $k+1$ has $2^{k+1}$ subsets 
> - Since $S(k)\implies S(k+1)$, $S(n)$ is true for all $n\in Z^+$
> 	- A set with $n$ elements has $2^n$ subsets
