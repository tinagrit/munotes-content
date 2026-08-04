Lecture 17

## Hypothesis Testing
In [[1_Point Estimation#Point Estimate|parameter estimation]], we are interested in **estimating** a parameter. Here, in hypothesis testing, we are interested in **testing a claim** about a parameter. 

A random [[1_Statistical Inference#Statistical Inference|sample]] can be used to test a particular **statistical hypothesis**, a statement about a set of parameters. 

The sample can be **consistent** or **inconsistent**.
- If the sample is inconsistent, we **reject** the hypothesis. 
- If the sample is consistent, we **fail to reject** or **accept** the hypothesis

### Testing Procedure
Consider a population with distribution parameter $\mu$ unknown. As we test a given hypothesis, the given hypothesis is called $H_{0}$, the **null hypothesis**.

The hypothesis can be:
- **simple**: $H_0:\mu=1000$
- **composite**: $H_0:\mu \geq 1000$

The null hypothesis is tested against an **alternative hypothesis**, called $H_{1}$ or $H_{a}$.

The procedure is:
1. **Claim**: state what to test
2. **Hypotheses**: formulate $H_0$ and $H_1$
3. **Significance**: choose $\alpha$
4. **Test**: calculate the test statistic, determine the p-value, then decide to accept or reject
5. **Conclusion**: answer the testing question

### P-value
The p-value is the probability that the value is **as extreme as the observed**, assuming that $H_{0}$ is true.

For example, if we assume that a coin flip is fair, the null hypothesis would be that we get heads half the time $P(\text{heads})=0.5$.

However, from the sample, if we toss 20 coins and get 18 heads, our p-value is the probability that we get **at least** 18 heads given the coin is fair:
$$
P(\geq 18\text{ heads}\mid \text{coin is fair})
$$
, which should be very small.

If the p-value is:
- **low**: data is **inconsistent** → **reject** the null hypothesis
- **high**: data is **consistent** → **accept** the null hypothesis

### Significance level
The significance level, denoted $\alpha$, is the **cutoff** for p-values to decide whether the p-value is low enough to reject the null hypothesis.

Typical values of $\alpha$ used in practice are $\alpha=0.1,0.05,0.01,0.005$.

### Critical region
The critical region is the **set of all *test statistic* values** that will cause us to reject the null hypothesis. 

Basically, all points where p-value $\leq \alpha$.

When $H_{0}$ is true, the probability that the estimator falls in that region is $\alpha$.

### Errors
When testing a null hypothesis, two types of error can result:
- **Type I error**: $H_0$ is true, but the test rejects it. $P=\alpha$
- **Type II error**: $H_0$ is false, but the test accepts it. $P=\beta$, depends on the true value of the parameter. The ***power*** of the test is defined as $1-\beta$, which is the probability that the test correctly rejects a false $H_0$.

