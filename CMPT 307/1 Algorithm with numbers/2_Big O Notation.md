Lectures 2-3

## Big O Notation
Big O notation allows us to **be precise** in measuring runtime, but also **not overly detailed**. It is also independent to computer/architecture, as a function of $n$ (the input size).

For example, if we have
$$
T(n)=5n^{3}+4n+3
$$
As $n$ grows large, the second and third terms $(4n+3)$ become insignificant, since $n^{3}$ will dominate. Here, we say that
$$
T(n)=O(n^{3})
$$

Formally,
> Let $f(n)$ and $g(n)$ be functions $\mathbb{Z}^{+}\to \mathbb{R}$
> $f=O(g)$ if there is a constant $c>0$ such that:
> $$f(n)\leq c\cdot g(n)$$
> 
> This means that $f$ **grows no faster than** $g$

For example, if we have:
$$
\begin{align}
f_{1}(n)=n^{2} &  & f_{2}(n)=2n+20
\end{align}
$$
We can conclude that:
$$
f_{2}=O(f_{1})
$$
since
$$
\dfrac{f_{2}(n)}{f_{1}(n)}=\dfrac{2n+20}{n^{2}}\to 0\text{ as }n\to \infty
$$
and therefore $f_{1}$ grows faster than $f_{2}$.

The reverse is not true.
$$
\dfrac{f_{1}(n)}{f_{2}(n)}=\dfrac{n^{2}}{2n+20}\to \infty\text{ as }n\to \infty
$$

### Big Omega and Big Theta
Just as $O(\cdot)$ is an analog of $\leq$, there are notations for $\geq$ and $=$ as well.

We can say that:
$$
f=\Omega(g)
$$
if $g=O(f)$ and there exists a constant $c>0$ such that $f(n)\geq c\cdot g(n)$

We can say that:
$$
f=\Theta(g)
$$
if $f=O(g)$ and $g=O(f)$. $f$ is **bounded** by $g$.

