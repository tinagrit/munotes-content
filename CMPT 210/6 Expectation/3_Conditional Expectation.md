Lecture 17

## Conditional Expectation
*Also see* [[1_Conditional Probability#Conditional Probability|Conditional Probability]]

For a [[2_Random Variables#Random Variable|random variable]] $R$, the [[1_Expectation#Expectation|expected value]] of $R$ **conditioned on** an event $E$ is given by:
$$
\mathbb{E}[R\mid E]=\sum_{x \in \text{Range}(R)}\text{Pr}[R=x \mid E]\cdot x 
$$

Note that using the definition of [[1_Conditional Probability#Conditional Probability|conditional probability]]:
$$
\text{Pr}[R=x\mid E]=\dfrac{\text{Pr}[(R=x)\cap E]}{\text{Pr}[E]}
$$

For example, rolling a 6-sided die, and $R$ be the number that is rolled. Look for the expected value given that **the number is at most 4**.

Let $E$ be the event that the number is at most 4

We can split this into 2 cases:
- where $x \in \left\{ 1,2,3,4 \right\}$
	- then $\text{Pr}[(R=x)\cap E]=\text{Pr}[R=x]$
	- and $\text{Pr}[R=x]=\dfrac{1}{6}$
	- therefore $\text{Pr}[R=x \mid E]=\dfrac{1/6}{4/6}=\dfrac{1}{4}$
- where $x \in \left\{ 5,6 \right\}$
	- then $\text{Pr}[(R=x)\cap E]=0$

The conditional expectation is then:
$$
\begin{align}
\mathbb{E}[R\mid E] & =\sum_{x \in \left\{ 1,2,3,4,5,6 \right\} }\text{Pr}[R=x \mid E] \cdot x  \\ \\

 & = \dfrac{1}{4}(1+2+3+4)+0(5+6) \\ \\

 & =2.5
\end{align}
$$


### Total Expectation
*Also see* [[6_Total Probability#Law of Total Probability|Total Probability]]

If $R$ is a random variable on a sample space $S$, and letting each $E_{i}$ mutually exclusive, then:
$$
\mathbb{E}[R]=\sum_{i=1}^{n} \mathbb{E}[R\mid E_{i}]\cdot \text{Pr}[E_{i}]
$$
When $S$ is split into $n$ mutually exclusive events, the overall expected value is the weighted **average of each subgroup** expectations.

For example, finding the expected height of a random person given:
- $49.6\%$ of people are male $\to \text{Pr}[M]$
- $50.4\%$ of people are female $\to \text{Pr}[F]$
- expected height of a random male is $180 \text{ cm}$ $\to \mathbb{E}[H\mid M]$
- expected height of a random female is $165\text{ cm}$ $\to \mathbb{E}[H\mid F]$

Let:
- $H$ be the **random variable** equal to the height 
- $M$ be the event that the person is a male
- $F$ be the event that the person is a female

Computing $\mathbb{E}[H]$, we have:
$$
\begin{align}
\mathbb{E}[H] & =\mathbb{E}[H\mid M]\cdot \text{Pr}[M]+\mathbb{E}[H\mid F]\cdot \text{Pr}[F] \\
 & =(180)(0.496)+(165)(0.504) \\
 & = 172.44\text{ cm}
\end{align}
$$


**Proof**:
By definition, the expected value of $R$ is:
$$
\begin{align}
\mathbb{E}[R]=\sum_{x \in \text{Range}(R)}\underbrace{ \text{Pr}[R=x] }_{  }\cdot x  & & (1)
\end{align}
$$
We apply the [[6_Total Probability#Law of Total Probability|law of total probability]] to expand $\text{Pr}[R=x]$, we get:
$$
\begin{align}
\text{Pr}[R=x]=\sum_{i=1}^{n}\text{Pr}[R=x \mid E_{i}]\cdot\text{Pr}[E_{i}]  &  & (2)
\end{align}
$$
Substituting $(2)$ into $(1)$, we get:
$$
\begin{align}
\mathbb{E}[R] & =\sum_{x \in \text{Range}(R)} \left( \sum_{i=1}^{n}\text{Pr}[R=x \mid E_{i}]\cdot\text{Pr}[E_{i}] \right)\cdot x   \\\\
 & = \sum_{i=1}^{n}\text{Pr}[E_{i}]\left( \sum_{x \in \text{Range}(R)} \text{Pr}[R=x \mid E_{i}] \cdot x  \right)\\\\
 & =  \sum_{i=1}^{n} \text{Pr}[E_{i}]\cdot \mathbb{E}[R\mid E_{i}]
\end{align}
$$

