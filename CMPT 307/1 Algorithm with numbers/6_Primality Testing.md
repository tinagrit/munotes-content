Lectures 5-6

## Fermat's little theorem
We can decide if an integer $p$ is prime without factoring the number. 

If $p$ is prime, then for every integer $a\in[1,p)$:
$$
a^{p-1}\equiv 1 \bmod p
$$

For example, if $p=7$ ($p$ is prime), then it must hold that:
$$
1^{6}\equiv 2^{6}\equiv 3^{6}\equiv 4^{6} \equiv 5^{6}\equiv 6^{6}\equiv 1\bmod 7
$$

If $p=8$ ($p$ is composite), we can observe that:
$$
2^{7}=128 \not\equiv 1 \bmod 8
$$
and therefore $8$ is not prime.

### Fermat test
We can pick $a\in[1,p)$ at **random**, and use it to decide whether a number is prime. 

For example, in the $p=8$ example, we chose $a=2$ to decide whether $8$ is prime.

This algorithm is fast. However, Fermat's theorem requires ***for all*** $a\in[1,p)$ for $p$ to be prime. A composite can *pass* the test for some bases, and *fail* the test for some bases.

For example, testing $p=341$ ($p$ is composite):
$$
2^{340}\equiv 1\bmod 341
$$
Therefore, $p=341$ passes the Fermat test although being a composite. This is called a **Fermat liar**. 

We hope that for a composite, most bases $a$ will fail the test. It is important to **pick** $a$ **at random**.

> [!tip] Carmichael numbers
> These are *extremely rare* composite numbers that **pass** the Fermat test **for all**  $a\in[1,p)$. 
> 
> For example, the smallest Carmichael number is $561=3\cdot 11\cdot 7$, a composite that will pass the Fermat test.

### Lemma and Reducing Error
A non-Carmichel composite will fail a Fermat test for some value of $a$. This lemma proves that at least half the choices of $a$ will also fail the test.

If $a^{p-1}\not\equiv 1\bmod p$ for some $a$ with $\text{gcd}(a,p)=1$, then it must also hold for **at least half** the choices of $a\in[1,p)$.

Proof:
We fix a value of $a$ such that it fails the test: $a^{p-1}\not\equiv 1\bmod p$.

For all $b$'s that pass the test: $b^{p-1}\equiv 1\bmod p$, there is a twin, $a\cdot b$, that fails the test.
$$
(a\cdot b)^{p-1}\equiv a^{p-1}b^{p-1}\equiv a^{p-1} \not\equiv 1\bmod p
$$
This means that **as many elements that fail the test pass** it.

Therefore, for any non-Carmichel number, the probability that the algorithm:
- correctly identifies a prime: $1$
- incorrectly identifies a composite as a prime: $\leq \dfrac{1}{2}$

While this error rate is high, we can reduce it by **picking many** $a$**'s**. Instead of running Fermat test for one random $a\in[1,p)$, run it for all $a_{1},a_{2},\dots,a_{k}\in[1,p)$, choosing an appropriate value of $k$. 

For instance, at $k=100$, the probability that the algorithm incorrectly identifies a composite as a prime is at most $2^{-100}$, which is very small.

### Lagrange's prime number theorem
Prime numbers are **abundant**. It is not difficult to generate a large prime number. 

Lagrange's prime number theorem shows how abundant prime numbers are.

Let $\pi(x)$ be the number of prime numbers $\leq x$, then:

$$
\boxed{ \pi(x)\approx \dfrac{x}{\ln x} }
$$
or
$$
\lim_{ x \to \infty } \dfrac{\pi(x)}{(x/\ln x)}=1
$$

To generate a random large prime number, we can simply:
1. **Pick a random** $n$-bit number $p$
2. Run a primality test on $p$
3. If it passes the test, output $p$, if not, pick another

This procedure will halt on average within $\boxed{ O(n) }$ steps.

> [!tip] Randomized algorithms
> There are two varieties of randomized algorithms.
> - **Monte Carlo** algorithms always run fast with a small chance of being incorrect
> - **Las Vegas** algorithms are always correct with a high chance of being fast

