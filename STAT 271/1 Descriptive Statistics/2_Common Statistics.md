Lecture 1

> [!fail] This note is partially complete.

## Common Statistics
Information in large [[1_Statistics and Data#Population and data|datasets]] can be summarized **numerically** by statistics. A **statistic** is a numerical quantity whose value is determined by data.

Types of common statistics include:
- [[#Central Tendency|Central Tendency]]
- Dispersion

---
## Central Tendency
Summarizing the **location** of a set of values. With $n$ values:

### Sample mean
Arithmetic average of all values, labelled $\bar{x}$ (x-bar), calculated with:
$$
\bar{x}=\dfrac{1}{n}\sum_{i=1}^{n}x_{i} 
$$
Add up all the values and divide by the number of values.

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
