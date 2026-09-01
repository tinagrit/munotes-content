Lecture 21

## Analysis of Variance
The analysis of [[2_Sample Mean Distribution#Variance|variance]] (***ANOVA***) is a test used to **compare the means** of 3+ groups to see if at least one group is significantly different.

Suppose we have $mn$ values in $m$ groups. Let $X_{ij}$ be a value $j=1,2,\dots,n$ in group $i=1,2,\dots,m$. This is a ***balanced design*** since the group sizes are the same ($n$).

Testing the [[1_Hypothesis Testing#Hypothesis Testing|hypothesis]]:
$$
\begin{cases}
H_{0}: & \mu_{1}=\mu_{2}=\dots=\mu_{m} \\
H_{1}: & \text{not all }\mu \text{'s are equal}
\end{cases}
$$

There is a method called **two-sample t-test** that can test this hypothesis, but can only compare **two** groups at a time. With $m$ groups, we need $\binom{m}{2}$ tests, which can get large.

### One-way ANOVA
This method can be used to **simultaneously compare** many group means. Assume the $X_{ij}$ are independent with $X_{ij}\sim N(\mu_{i},\sigma^{2})$. These groups have a common but unknown variance $\sigma^{2}$.

The test statistic ($TS$), a value calculated from dataset that gives us an indication about $H_{0}$ likely true, is defined as:
$$
\boxed{ TS=\dfrac{SS_{b}/(m-1)}{SS_{w}/(nm-m)}\sim F_{m-1,nm-m} }
$$
where $SS_{b}$, the ***sum of squares between***
$$
\boxed{ SS_{b}=n\sum_{i=1}^{m} (\overline{X_{i}}-\overline{X})^{2} }
$$
and $SS_{w}$, the ***sum of squares within***
$$
\boxed{ SS_{w}=\sum_{i=1}^{m} \sum_{j=1}^{n} X_{ij}^{2}-nm\overline{X}^{2}-SS_{b} }
$$
The $TS$ follows the ***F-distribution***.

### Hypothesis test
Compare the $TS$ value that we calculated with $F_{\alpha,m-1,nm-m}$, where $\alpha$ is the [[1_Hypothesis Testing#Significance level|significance level]].

**Reject** $H_{0}$ if:
$$
\boxed{ TS>F_{\alpha,m-1,nm-m} }\implies \text{reject}
$$
