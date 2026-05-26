Lectures 2 & 3

## Common Statistics
Information in large [[1_Statistics and Data#Population and data|datasets]] can be summarized **numerically** by statistics. A **statistic** is a numerical quantity whose value is determined by data.

Ways of summarizing data includes:
- [[#Central Tendency|Central Tendency]]
- [[#Dispersion|Dispersion]]
- [[#Percentiles and Box plots|Percentiles and Box plots]]

---
## Central Tendency
Summarizing the **location** of a set of values. With $n$ values:

### Sample mean
Arithmetic average of all values, labelled $\bar{x}$ (x-bar), calculated with:
$$
\bar{x}=\dfrac{1}{n}\sum_{i=1}^{n}x_{i} 
$$
Add up all the values and divide by the number of values.

This uses all values, and is affected by extreme values.

If we have a frequency table with $k$ distinct values on $n$ values, we can use:
$$
\bar{x}=\dfrac{1}{n}\sum_{i=1}^{k}f_{i}v_{i} 
$$
where $f_{i}$ is the frequency of the distinct value $v_{i}$. All of $f_{i}$ added up should equal $n$.

**Property** of sample mean:
$$
y_{i}=ax_{i}+b \implies \bar{y}=a \bar{x}+b
$$

### Sample median
The middle value of the dataset, labelled $\tilde{x}$.

Let $x_{(i)}$ (x at i) be the $i^{\text{th}}$ smallest value in the dataset after it is sorted, then the sample median is:
$$
\tilde{x}=\begin{cases}
x_{\left(\frac{n+1}{2} \right)} & n\text{ is odd} \\ \\
0.5\left( x_{\left( \frac{n}{2} \right) }+x_{\left( \frac{n}{2}+1 \right) } \right)  & n\text{ is even}
\end{cases}
$$

This only uses the **middle** value, not affected by extreme values.

### Sample mode
The value that occurs with the largest frequency. If many values have the same most frequency, they are called **modal values**.


---
## Dispersion
Also known as "spread" or "variability". With $n$ values:

### Sample variance
The average of the squares of the distances between the values and their [[#Sample mean|mean]], denoted $s^{2}$.
$$
s^{2}=\dfrac{1}{n-1}\sum_{i=1}^{n}(x_{i}-\overline{x})^{2} 
$$

> Property: show that$$\sum_{i=1}^{n}(x_{i}-\overline{x})^{2}=\sum_{i=1}^{n} (x_{i})^{2}-n\overline{x}^{2}$$
> 

### Sample standard deviation
The positive square root of [[#Sample variance|variance]], denoted $s$. This is more easily understandable since it uses the same unit as the data.
$$
s=\sqrt{ s^{2} }
$$


---
## Percentiles and Box plots

### Percentiles
The sample $100p$ percentile (for example: $80^{\text{th}}$ percentile, then $p=0.8$) is the value that satisfies:
1. at least $100p\%$ of the values are $\leq$ to it
2. at least $100(1-p)\%$ of the values are $\geq$ to it

If we are finding the $80^\text{th}$ percentile, then we need a value that at least $80\%$ of all values are $\leq$ it, and at least $20\%$ of all values are $\geq$ it.

If two values satisfy this condition, then the percentile is the **average** of the two values.

Let $x_{(i)}$ (x at i) be the $i^{\text{th}}$ smallest value in the dataset after it is sorted:
$$
100p\text{ percentile}=\begin{cases}
x_{(\lfloor np+1 \rfloor )} & np\text{ is not an integer} \\\\
0.5(x_{(np)}+x_{(np+1)}) & np\text{ is an integer}
\end{cases}
$$

The [[#Sample median|median]] is the $50^{\text{th}}$ percentile.

The special percentile cases include:
- $25^{\text{th}}$ percentile: **first quartile**
- $50^{\text{th}}$ percentile: **second quartile** (median)
- $75^{\text{th}}$ percentile: **third quartile**

### Box plot
A box plot can be used to show the three quartiles, along with the minimum and maximum values.

![[Screenshot 2026-05-25 at 1.25.25 PM.png|500]]

The part in the box (first to third quartile) is the **middle 50%** of the data.

The part on the line, called whiskers, is the rest of the data.

