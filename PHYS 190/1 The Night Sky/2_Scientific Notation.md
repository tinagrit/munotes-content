Lecture 2

## Using Logarithmic Scale
The logarithmic scale is **more useful** in astronomy than linear scale, since measurements range from very small to very large.

![[Screenshot 2026-01-12 at 6.17.47 PM.png|600]]

## Scientific Notation
Graphs with logarithmic scale, in astronomy, is usually represented as **powers of ten**. Expressions are written in **scientific notation**.

Write $n \times 10^{m}$ where:
- $n$ is a constant such that $1\leq n <10$
- $m$ is an integer ($\in \mathbb{Z}$)

> [!tip] Note
> For numbers with $n=1$, such as (1,000), (10,000), (1,000,000), $m$ is:
> - the number of zeroes following 1, or
> - (negative) the number of zeroes preceding 1 (including the one before the dot)

| English     | Number            | Scientific Notation |
| ----------- | ----------------- | ------------------- |
| 1 thousand  | 1,000             | $10^{3}$            |
| 1 million   | 1,000,000         | $10^{6}$            |
| 1 billion   | 1,000,000,000     | $10^{9}$            |
| 1 trillion  | 1,000,000,000,000 | $10^{12}$           |
| 1 tenth     | 0.1               | $10^{-1}$           |
| 1 hundredth | 0.01              | $10^{-2}$           |

### Multiplying
For:
$$
(n_{1}\times 10^{m_{1}})\times(n_{2}\times 10^{m_{2}})
$$
Do:
$$
(n_{1}\times n_{2})\times(10^{m_{1}+m_{2}})
$$
Then adjust exponents according to the rules above.

### Dividing
For:
$$
(n_{1}\times 10^{m_{1}})\div(n_{2}\times 10^{m_{2}})
$$
Do:
$$
(n_{1}\div n_{2})\times(10^{m_{1}-m_{2}})
$$
Then adjust exponents according to the rules above.


## Astronomy Estimation
- Most of astronomy is **not known** to great precision
- Usually **1 or 2** significant digits
- Astronomers round to nearest factor of 10
	- For example, the speed of the fastest aircraft with grav assist is $163 \text{ m/s}\approx 100 \text{ m/s}=10^{2} \text{ m/s}$ 

### Astronomical Unit
The Astronomical Unit (**AU**) is the distance between the Earth and the Sun
$$
1 \text{ AU}=1.5\times 10^{11} \text{ m}
$$

### Speed of light
The speed that light travels universally
$$
c=3\times 10^{8} \text{ m/s}
$$

### Example Calculation

> How long does it take for light to travel from the Sun to Earth?

Using:
$$
\begin{align}
\text{speed}=\dfrac{\text{distance}}{\text{time}} &&
v=\dfrac{s}{t}
\end{align}
$$
In this case, we have $v=c$ and $s=1\text{ AU}$, substituting:
$$
c=\dfrac{1 \text{ AU}}{t}
$$
It follows that:
$$
3\times 10^{8} \text{ m/s}=\dfrac{1.5\times 10^{11} \text{ m}}{t}
$$
$$
t=\dfrac{1.5\times 10^{11}}{3\times 10^{8}}
$$
$$
t=0.5\times 10^{3}=5\times 10^{2} \text{ s}
$$
$5\times 10^{2}$ seconds is $\approx 8$ minutes


> If it takes a spacecraft 1 year  to reach the Sun from Earth, how fast is it going?

Using:
$$
\begin{align}
\text{speed}=\dfrac{\text{distance}}{\text{time}} &&
v=\dfrac{s}{t}
\end{align}
$$
In this case, we have $s=1\text{ AU}$ and $t=1 \text{ year}$

Converting $1 \text{ year}$ into seconds:
$$
1 \cancel{ \text{ year} }\times\dfrac{365\cancel{ \text{ days} }}{1 \cancel{ \text{ year} }}\times\dfrac{24 \cancel{ \text{ hours} }}{1 \cancel{ \text{ day} }}\times\dfrac{3,600\text{ seconds}}{1 \cancel{ \text{ hour} }}
$$
$$
=365\times 24 \times 3,600=31,536,000\approx 3\times 10^{7} \text{ s}
$$
Substituting:
$$
v=\dfrac{1.5\times 10^{11} \text{ m}}{3\times 10^{7} \text{ s}}
$$
It follows that:
$$
v=0.5 \times 10^{4}=5\times 10^{3} \text{ m/s}
$$
