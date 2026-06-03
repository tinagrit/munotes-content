Lecture 5

## Conditional Distribution
We can have a [[3_Distribution Functions#Probability Mass Function (PMF)|probability mass function]] that is **conditioned** on another random variable, like [[1_Probability#Conditional Probability|conditional probability]], using the [[4_Joint Distribution#Jointly Distributed Random Variables|joint distribution]].

The **conditioned PMF** of $X$ given that $Y=y$ is:
$$
p_{X\mid Y}(x\mid y)=P(X=x \mid Y=y)=\dfrac{P(X=x,Y=y)}{P(Y=y)}=\dfrac{p(x,y)}{p_{Y}(y)}
$$
$$
\boxed{ p_{X\mid Y}(x\mid y)=\dfrac{p(x,y)}{p_{Y}(y)} }
$$

Similarly, the **conditioned PDF** of $X$ given that $Y=y$ is:
$$
\boxed{ f_{X\mid Y}(x\mid y)=\dfrac{f(x,y)}{f_{Y}(y)} }
$$

