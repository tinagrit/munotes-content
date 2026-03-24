Lectures 17 & 18

## Independence
*Also see* [[1_Conditional Probability#Independence|Independent probability]]

Two [[2_Random Variables#Random Variable|random variables]] $R_{1}$ and $R_{2}$ are **independent** if:
- for all $x_{1} \in \text{Range}(R_{1})$
- for all $x_{2} \in \text{Range}(R_{2})$
- then the events that $[R_{1}=x_{1}]$ and $[R_{2}=x_{2}]$ are independent

Knowing the value of $R_{1}$ does not give information about the value of $R_{2}$

These equalities hold due to the properties of independent events:
$$
\text{Pr}[(R_{1}=x_{1})\cap(R_{2}=x_{2})]=\text{Pr}[R_{1}=x_{1}]\cdot \text{Pr}[R_{2}=x_{2}]
$$
$$
\text{Pr}[(R_{1}=x_{1})\mid(R_{2}=x_{2})]=\text{Pr}[R_{1}=x_{1}]
$$

Using [[1_Expectation#Expectation|Expectation]], this equality also holds:
$$
\mathbb{E}[R_{1}R_{2}]=\mathbb{E}[R_{1}]\cdot \mathbb{E}[R_{2}]
$$
Proof of expectation expression using the expected value definition:
$$
\begin{align}
\mathbb{E}[R_{1}R_{2}] & =\sum_{x \in \text{Range}(R_{1}R_{2})} \text{Pr}[R_{1}R_{2}=x]\cdot x \\\\
 & = \sum_{r_{1} \in \text{Range}(R_{1})} \sum_{r_{2} \in \text{Range}(R_{2})}\text{Pr}[R_{1}=r_{1} \cap R_{2}=r_{2}]\cdot r_{1}r_{2}   \\\\
 & = \sum_{r_{1} \in \text{Range}(R_{1})} \sum_{r_{2} \in \text{Range}(R_{2})}\text{Pr}[R_{1}=r_{1}]\cdot r_{1} \cdot \text{Pr}[ R_{2}=r_{2}]\cdot r_{2}  \\\\
 & = \left( \sum_{r_{1} \in \text{Range}(R_{1})}\text{Pr}[R_{1}=r_{1}]\cdot r_{1} \right) \left( \sum_{r_{2} \in \text{Range}(R_{2})}\text{Pr}[R_{2}=r_{2}]\cdot r_{2} \right)  \\\\
 & = \mathbb{E}[R_{1}]\cdot \mathbb{E}[R_{2}]
\end{align}

$$


### Joint Distribution
The [[3_Distribution Functions#Distribution Functions|distribution functions]] can be used in joint probability, for example:
$$
\text{Pr}[(R_{1}=x_{1})\cap (R_{2}=x_{2})]
$$
Can be expressed using the [[3_Distribution Functions#Probability Mass Function (PMF)|PMF]] as:
$$
\text{PMF}_{R_{1},R_{2}}
[x_{1},x_{2}]$$
If $R_{1}$ and $R_{2}$ are independent, then:
$$
\text{PMF}_{R_{1},R_{2}}[x_{1},x_{2}]=\text{PMF}_{R_{1}}[x_{1}]\cdot \text{PMF}_{R_{2}}[x_{2}]
$$


### Marginalizing
Given a joint distribution, we can "**unjoint**" it by marginalizing over the other.

If we have $\text{PMF}_{R_{1},R_{2}}$, we can find PMF of **just** $R_{1}$ by summing over all values of $R_{2}$, since we are "fixing" $\text{Pr}[R_{1}=x_{1}]$, and iterating through all other possibilities.

$$
\text{PMF}_{R_{1}}[x_{1}]=\sum_{x_{2} \in \text{Range}(R_{2})}\text{PMF}_{R_{1},R_{2}}[x_{1},x_{2}] 
$$

