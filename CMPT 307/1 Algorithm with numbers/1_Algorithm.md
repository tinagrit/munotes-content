Lecture 2

## Algorithm
The term "algorithm" goes back to honour ***Al-Khwarizmi*** from Baghdad who laid out basic methods for adding, multiplying, dividing numbers, extracting square roots, and calculating digits of $\pi$. They were precise, unambiguous, efficient, and correct. They were **algorithms**.

***Leonardo Fibonacci*** saw the potential of the positional (decimal) system and developed it further.

An algorithm is a **well-defined** procedure to solve a specific problem. Whenever we have an algorithm, we want to always ask:
1. Is it correct?
2. How much time does it take?
3. Can we do better?

### Fibonacci Numbers
Fibonacci is known for his sequence of numbers
$$
0,1,1,2,3,5,8,13\dots
$$
Each number is the sum of its 2 immediate predecessors.
$$
F_{n}=\begin{cases}
F_{n-1}+F_{n-2} & \text{if }n>1 \\
1 & \text{if }n=1 \\
0 & \text{if }n=0
\end{cases}
$$
The Fibonacci numbers grow **almost** as fast as the powers of 2. To calculate what $F_{100}$ is, for example, we need **an algorithm**.

**Exponential**
We can implement the recursive definition of $F_{n}$ directly:
```
function fib(n):
	if (n=0): return 0
	if (n=1): return 1
	
	return fib(n-1) + fib(n-2)	
```

Back to the 3 questions earlier:
1. **Yes**, it is correct by definition
2. The running time of this function is: $T(n)=T(n-1)+T(n-2)+O(1)$ for $n>1$

An observation to this running time is that $T(n)\geq F_{n}$ and the running time is **exponential** to the Fibonacci numbers. This algorithm is **impractical** and **slow**.

> [!tip] Improvements in computer technology do not help
> *Moore's Law* states that computers get 1.6 times faster every year. This algorithm has running time $2^{0.694n}\approx 1.6^{n}$, meaning that it takes 1.6 times longer to calculate $F_{n+1}$ compared to $F_{n}$.
> 
> With this logic, improvements to computer technology only allow us to compute 1 more Fibonacci number per year.


**Polynomial**
Many of the calculations in the original algorithm are **repeated**. We can store intermediate results to avoid the repeat.
```
function fib(n):
	if (n=0): return 0
	f[0..n] = [0]
	f[0] = 0
	f[1] = 1
	
	for i = 2..n:
		f[i] = f[i-1] + f[i-2]
	
	return f[n]
```

1. This is **also correct** by definition
2. The running time of this function is linear in $n$


