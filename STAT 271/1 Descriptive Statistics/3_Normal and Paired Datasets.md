Lecture 3

## Normal Datasets
Some large datasets have [[1_Statistics and Data#Histogram|histograms]] that are **bell-shaped**, they are **normal**.

The histogram would **peak** at the [[2_Common Statistics#Sample median|sample median]], and they are **symmetric**.
When the histogram is not symmetric, it is **skewed**.

![[chart02.png]]

**Left skewed** dataset means that the **tail** is to the left. There are a lot of values to the **left** of the [[2_Common Statistics#Central Tendency|centre]].

**Right skewed** dataset is the opposite, and is **more common** than left skewed, such as datasets like salaries and house prices where there can be extremely high values.


---
## Paired Datasets
Some datasets consist of pairs of **related values**, such as the relations between:
- income and years of education
- temperature and sales of ice cream

The $i^{\text{th}}$ data value is denoted by $(x_{i},y_{i})$

This kind of dataset can be displayed in a **scatterplot**, where each individual value is plotted on the 2 dimensional x-y plane.

![[Screenshot 2026-05-25 at 2.16.13 PM.png|300]]

### Correlation
A [[2_Common Statistics#Common Statistics|statistic]] that measures the **strength and direction** of the **linear** relationship between the paired values, denoted $r$.

> [!tip] Correlation measures **association**, not **causation**.

A positive $r$ means a general **positive slope**, and a negative $r$ means a general **negative slope**.

As $r$ gets closer to $1$ or $-1$, the relationship is **stronger**.

Some properties of $r$ include:
1. $r \in [-1,1]$
2. $r$ is unitless
3. For a correlation between $x$ and $y$: $r_{x,y}$, a **linear transformation** can be done to $x,y$ and keep the correlation:
$$
r_{a+bx,c+dy}=\text{sign}(bd)r_{x,y}
$$
	where:
$$
\text{sign}(bd)=\begin{cases}
-1 & \text{for }bd<0 \\
0 & \text{for }bd=0 \\
1 & \text{for }bd>0
\end{cases}
$$

4. For a correlation between $x$ and $y$: $r_{x,y}$, if $y$ is a linear transformation of $x$:
$$
y_{i}=a+bx_{i}
$$
	then we have:
$$
r=\begin{cases}
-1 & \text{if }b<0 \\
0 & \text{if }b=0 \\
1 & \text{if }b>0
\end{cases}
$$

> [!warning] Note
> Correlation only measures **linear relationship**. For a relationship that is not linear (for example, quadratic), we will not get information of the relationship.
> 
