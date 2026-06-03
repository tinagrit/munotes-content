Lecture 5

## Jointly Distributed Random Variables
For some experiments, we are interested in more than one [[2_Random Variables#Random Variables|random variable]], for example, **number** of cigarettes and the **age** that cancer is diagnosed.

### Joint and Marginal CDF
This relationship can be specified by the **joint** [[3_Distribution Functions#Cumulative Distribution Function (CDF)|cumulative distribution function]], denoted $F(x,y)$ of $X$ and $Y$:
$$
\boxed{ F(x,y)=P(X\leq x,Y\leq y) }
$$

Since
$$
F_{X}(x)=P(X\leq x)=P(X\leq x,Y<\infty)=F(x,\infty)
$$
and
$$
F_{Y}(y)=P(Y\leq y)=P(X<\infty, Y\leq y)=F(\infty,y)
$$

This means that if we have the joint CDF $F(x,y)$, we can plug $\infty$ into one and **find the marginal** CDF for each random variable.
$$
F(x,y) \implies F(x)\text{ and }F(y)
$$

However, the reverse is not true. If we know each marginal CDF, we cannot find the joint CDF.
$$
F(x)\text{ and }F(y) \centernot\implies F(x,y)
$$

If $X$ and $Y$ are [[2_Random Variables#Independence|independent]], then $F(x,y)=F_{X}(x)F_{Y}(y)$

### Joint and Marginal PMF
If we have [[2_Random Variables#Types of Random Variables|discrete]] random variables $X$, $Y$, then their **joint** [[3_Distribution Functions#Probability Mass Function (PMF)|probability mass function]], denoted $p(x,y)$ is:
$$
\boxed{ p(x_{i},y_{j})=P\left\{ X=x_{i},Y=y_{j} \right\}  }
$$

Using [[1_Probability#Axioms and Propositions|Axiom 3]], we can **find the marginal** PMF by summing the function over $i$ or $j$.
$$
\begin{align}
P\left\{ X=x_{i} \right\}  & =P\left( \bigcup_{j}\left\{ X=x_{i},Y=y_{j} \right\}  \right)  \\\\
 & =\sum_{j} P\left\{ X=x_{i},Y=y_{j} \right\} \\\\
 & =\sum_{j} p(x_{i},y_{j}) 
\end{align}
$$

To find $P\left\{ X=x_{i} \right\}$, we sum over $j$ because we want the total probability where $X=x_{i}$ but $Y$ can be anything in the $j$. 

Therefore, the marginal PMFs are:
- $P\left\{ X=x_{i} \right\}=\sum_{j}p(x_{i},y_{j})$
- $P\left\{ Y=y_{i} \right\}=\sum_{i}p(x_{i},y_{j})$

If $X$ and $Y$ are [[2_Random Variables#Independence|independent]], then $p(x,y)=p_{X}(x)p_{Y}(y)$

### Joint and Marginal PDF
For [[2_Random Variables#Types of Random Variables|continuous]] random variables $X$, $Y$, they are **jointly continuous** if there exists the **joint** [[3_Distribution Functions#Probability Density Function (PDF)|probability density function]], denoted $f(x,y)$.

Recall that in a marginal PDF, for one continuous random variable:
$$
\boxed{ P\left\{ X \in C \right\}=\int_{x \in C}f(x)\,dx  }
$$
For two variables, the function is integrated **over both** variables. 
$$
P\left\{ (X,Y)\in C \right\} =\int \int _{(x,y)\in C}f(x,y)\,dx\,dy
$$
Instead of finding the **area** under the curve, we find the **volume** under the surface.

For example, if we have $C$ as:
$$
C=\left\{ (x,y)\mid x \in A,y\in B \right\} 
$$
Then the joint PMF is:
$$
\begin{align}
P\left\{ (X,Y)\in C \right\} & =P\left\{ X \in A,Y\in B \right\}  \\
 & =\int_{B}\int_{A}f(x,y)\,dx\,dy
\end{align}
$$

Recall that the PDF is the **derivative** of the CDF
$$\dfrac{d}{dx}F(x)=f(x)$$
The **joint** PDF is the **partial derivative** over $x$ and $y$ of the **joint** CDF:
$$
\boxed{ \dfrac{\partial^{2}}{\partial x\partial y}F(x,y)=f(x,y) }
$$

Using a similar method from [[#Joint and Marginal PMF]], we can find the **marginal PDF** using the **joint PDF**.

To find the $f_{X}(x)$ out of $f(x,y)$, we let $y$ be anything, therefore we integrate it with respect to $y$, and the other way around:
- $\displaystyle f_{X}(x)=\int_{-\infty}^{\infty}f(x,y)\,dy$
- $\displaystyle f_{Y}(y)=\int_{-\infty}^{\infty}f(x,y)\,dx$

If $X$ and $Y$ are [[2_Random Variables#Independence|independent]], then $f(x,y)=f_{X}(x)f_{Y}(y)$

