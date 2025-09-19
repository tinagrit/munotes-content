Chapter 9.1


## Complex Numbers
- consist of **imaginary** numbers
- **not** in the **set of all real numbers** $\not\in \mathbb{R}$
- $\mathbb{C}$ denotes the set of all complex numbers
 
### The i
- the imaginary number $i$ is defined as:
	- $i=\sqrt{ -1 }$
	- $i^{2}=-1$
- otherwise, $i$ has the **algebraic** properties of real numbers (treat it as a number)

### Writing complex numbers
- a complex number has the form
$$
z=a+bi
$$
- where $a,b \in \mathbb{R}$
	- $a$ is called the *"real part"*
	- $b$ is called the *"imaginary part"*
- For example, $(3+2i)$, $(9i)$

If $a=0$, the number is **pure imaginary**. 
- $(3+2i)$ is not pure imaginary
- $(9i)$ is pure imaginary


---

## Complex Number Arithmetic

### Addition
- add/subtract real and imaginary parts **separately**
- for example,
	- $(2-i)+(1+2i)$
	- $=3+i$

### Multiplication
- multiply treating $i$ like a real number
- keep in mind that $i^{2}=-1$
- for example,
	- $(2+3i)i$
	- $=2i+3i^{2}$
	- $=2i-3$

### Conjugate
- **switch the sign** for the *imaginary part*
- denoted $\bar{z}$ for the conjugate of $z$
- for example
	- $z=a+bi$
	- $\implies \bar{z}=a-bi$

### Absolute
- or **modulus** 
- defined as $|z|=\sqrt{ a^{2}+b^{2} }$
	- where $z=a+bi$

> [!important] $z\bar{z}=|z|^{2}$ where $z$ is a complex number


### Multiplicative Inverse
- denoted $z^{-1}$
- complex number such that $z^{-1}z=1$
- defined as $z^{-1}=\dfrac{1}{a+bi}$ where $z=a+bi$
- simplifying, we get:
$$
z^{-1}=\dfrac{1}{a+bi}\cdot \dfrac{(a-bi)}{(a-bi)}=\dfrac{a-bi}{a^{2}+b^{2}}=\dfrac{\bar{z}}{|z|^{2}}
$$
- therefore, $z^{-1}$ is also $=\dfrac{\bar{z}}{|z|^{2}}$

### Arithmetic Properties
For any two complex numbers $w$ and $z$:
1. $\overline{w+z}=\overline{w}+\overline{z}$
2. $\overline{w-z}=\overline{w}-\overline{z}$
3. $\overline{wz}=\bar{w}\bar{z}$
4. $\overline{\bar{z}}=z$
5. $|\bar{z}|=z$
6. $\overline{\left( \dfrac{w}{z} \right)}=\dfrac{\bar{w}}{\bar{z}}$
7. $|wz|=|w|\cdot|z|$
8. $\left\lvert  \dfrac{w}{z}  \right\rvert=\dfrac{|w|}{|z|}$
9. $|w+z|\leq |w|+|z|$ (See [[3_Length and Angles#Triangle Inequality|Triangle Inequality]])


---

## Complex Plane

In a complex number $z=a+bi$, think of $a$ and $b$ as magnitudes of **a vector** in $\mathbb{R}^{2}$ where $\vec{v}=\begin{bmatrix}a\\b\end{bmatrix}$.
- the $x$-axis ($a$) is the real axis
- the $y$-axis ($b$) is the imaginary axis

 These complex operations **work as vectors**:
- adding and subtracting
- scalar multiplication
- norm of a vector = modulus of a complex number
- reflection over the real axis = the conjugate of a complex number

Multiplying two complex numbers is **DIFFERENT** than doing a dot product or cross product.


### Polar Coordinates

Let $\theta$ be the angle from the real axis to the vector/complex number $(a,b)$.
The real and imaginary parts of $z$ can be written as:
$$
\begin{align}
a & =|z|\cos\theta \\
b & =|z|\sin\theta
\end{align}
$$
Therefore, $z$ can be rewritten as:
$$
\begin{align}
z & =a+bi \\
z & =|z|\cos\theta +|z|\sin\theta i \\
z & =|z|(\cos\theta+i\sin\theta)
\end{align}
$$


### Multiplication and Division

To **multiply** two complex numbers in polar form, **multiply** their moduli and **add** their arguments
$$\begin{align}
z_{1}=|z_{1}|(\cos\theta_{1}+i\sin\theta_{1}) &  & z_{2}=|z_{2}|(\cos\theta_{2}+i\sin\theta_{2})
\end{align}

$$
$$
z_{1}z_{2}=|z_{1}|\cdot|z_{2}|\cdot\left( \cos(\theta_{1}+\theta_{2})+i\sin(\theta_{1}+\theta_{2}) \right) 
$$

> [!important] This means that multiplying a complex number $z$ by:
> - $i$, will **rotate** the vector counterclockwise by $\dfrac{\pi}{2}$
> - $\sqrt{ i }$, will **rotate** the vector counterclockwise by $\dfrac{\pi}{4}$

To **divide** two complex numbers in polar form, **divide** their moduli and **subtract** their arguments
$$
\begin{align}
z_{1}=|z_{1}|(\cos\theta_{1}+i\sin\theta_{1}) &  & z_{2}=|z_{2}|(\cos\theta_{2}+i\sin\theta_{2})
\end{align}

$$
$$
\dfrac{z_{1}}{z_{2}}=\dfrac{|z_{1}|}{|z_{2}|}\cdot \left( \cos(\theta_{1}-\theta_{2})-i\sin(\theta_{1}-\theta_{2}) \right) 
$$

> [!important] This means that multiplying a complex number $z$ by:
> - $i$, will **rotate** the vector clockwise by $\dfrac{\pi}{2}$
> - $\sqrt{ i }$, will **rotate** the vector clockwise by $\dfrac{\pi}{4}$


### Exponents (de Moivre's Formula)
- if we have a complex number in polar form
$$
z=|z|(\cos\theta+i\sin\theta)
$$
- then we can take $z$ to **the power of** $n$ by
$$
z^{n}=|z|^{n}(\cos n\theta+i\sin n\theta)
$$

### Euler's formula
- derived using *Taylor's series*, for all $\theta$:
$$
e^{i\theta}=\cos\theta+i\sin\theta
$$
- By taking $\theta=\pi$ we can show that:
$$
\begin{align}
e^{i\pi} & =\cos \pi+i\sin \pi \\
e^{i\pi} & =-1 \\
e^{i\pi}+1 & =0
\end{align}
$$
- Using Euler's formula, we can also rewrite the polar form as:
$$
z=|z|e^{i\theta}
$$

### The nth root
- allowing complex numbers, the $n$th root of a number has $n$ **different roots**

For example, finding the *cube (3) root of 27*, there are 3 answers.
- Writing $x^{3}-27=0$, we can **technically** factor this into 3 brackets
- $x^{3}-27=0$
- $\implies (x-3)(x^{2}+3x+9)$
- $\implies x=3,x=\dfrac{-3\pm \sqrt{ 9^{2}-(4)(1)(9) }}{2}$
  by the quadratic formula
- $\implies x=3,x=-\dfrac{3}{2}\pm\dfrac{3}{2}i$

We can also use Euler's formula:
$$
r^{1/n}=\left[ re^{i(\theta+2\pi k)} \right]^{1/n} 
$$
where $k=0,1,\dots,n-1$

To find the *cube (3) root of 27*, put 3 on the real axis ($\theta=0$)
$$
27^{1/3}=\left[ 27e^{i(2\pi k)} \right]^{1/3} 
$$
- at $k=0$, we get $3$
- at $k=1$, we get $3e^{i2\pi/3}$
- at $k=2$, we get $3e^{i 4\pi/3}$

Therefore, the cube root of 3 includes $\left\{ 3,3e^{i 2\pi/3},3e^{i 4\pi/3} \right\}$
These are the same answers as above $x=3,x=-\dfrac{3}{2}\pm\dfrac{3}{2}i$
