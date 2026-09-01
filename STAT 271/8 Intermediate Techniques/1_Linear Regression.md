Lectures 19-20

## Linear Regression
Linear regression **determines a linear relationship** between a set of variables.

The regression line is defined as
$$
Y=\beta_{0}+\beta_{1}x_{1}+\beta_{2}x_{2}+\dots+\beta_{k}x_{k}+e
$$
where
- $Y$ is the **response** or **dependent variable**
- $x_{i}$ with $i=1,2,\dots,k$ are the **explanatory** or **independent** variables
- $e$ is the error.

### Simple Model
The simple linear regression model ($k=1$) is:
$$
Y=\alpha+\beta x+e
$$

When we have a paired dataset (see [[3_Normal and Paired Datasets#Paired Datasets|scatterplot]]), we want to find the **line of best fit**, a linear line closest to all the data points.

We use the **Least Square** (*LS*) approach to minimize the **sum of the squared differences** between the estimated responses and the actual responses.
$$
SS_{R}=\sum_{i=1}^{n} [Y_{i}-(A+Bx_{i})]^{2}
$$
where $SS_{R}$ is the sum of square residuals, and $A$ and $B$ are the **LS estimators** of $\alpha$ and $\beta$.

Therefore, the line
$$
y=A+Bx
$$
is the **estimated** or **fitted regression line**.

### Using R
The programming language R can help find the linear fit.

If we have a dataset in `x` and `y`, we can use the `fit` command to find the line of best fit, "predict `y` using `x`":
```r
> fit = lm(y~x)
> fit
```
```shell
Coefficients:
(Intercept)            x
    -4.4727       0.4964
```

In this case, the output gives the estimated line:
$$
Y=-4.4727+0.4964x
$$

More information about the estimated linear model can be found using:
```r
> summary(fit)
```
```shell
Coefficients:
               Estimate     Std. Error   t value   Pr(>|t|)
(Intercept)    -4.47273     5.63433      -0.794    0.45
x              0.49636      0.03812      13.022    1.15e-06

Residual standard error: 3.462 on 8 degrees of freedom
Multiple R-squared: 0.9549, Adjusted R-squared: 0.9493
F-statistic: 169.6 on 1 and 8 DF, p-value: 1.147e-06
```

This means that the intercept estimate was with standard deviation $\approx 5.63$, and the slope estimate was with standard deviation $\approx0.038$.

The smaller the standard deviation, the **more confident** in the estimate.

The $\text{Pr}(>|t|)$ column is the [[1_Hypothesis Testing#P-value|p-value]] of the estimate.

In R, we can plot the values on to a graph using:
```r
> plot(x,y)
> abline(fit)
```

### Hypothesis test
Using the p-value, we can set up a [[1_Hypothesis Testing#Hypothesis Testing|hypothesis test]] where:
- The null hypothesis $H_{0}$: there is no linear relationship $\beta=0$
- The alternate hypothesis $H_{1}$: there is a linear relationship $\beta\neq 0$

Since the p-value of $x$ is $1.15\times 10^{-6}$, which is very small, **reject the null hypothesis**.

### R-squared
The $R^{2}$ or the **coefficient of determination** is a way to evaluate the *goodness-of-fit* of the line to the data.

$R^{2}$ can be interpreted as:
- the square of the correlation between $Y$ and $x$
- the fraction of the **variation** in the $Y$ values that is explained by the estimated line

In the R example above, the "Multiple R-squared" is measured as $95.49\%$, which means that almost all of the variation in $Y$ is explained by the linear regression, demonstrating a **good fit**.

### Multiple Linear Regression
In many applications, the response variable $Y$ is related to many independent variables $x_{1},x_{2},\dots,x_{k}$.

The multiple linear regression model is:
$$
Y=\beta_{0}+\beta_{1}x_{1}+\beta_{2}x_{2}+\dots+\beta_{k}x_{k}+e
$$
where $e\sim N(0,\sigma^{2})$ (see [[4_Normal Distribution#Normal Random Variable|normal distribution]])

The least square estimators $B$ are **unbiased**.

This estimation can also be done in R with datasets in `x1`, `x2`, and `y`:
```r
> fit = lm(y~x1+x2)
> fit
```
```shell
Coefficients:
(Intercept)           x1           x2
   150.1414       0.3621   -3163.5648
```

In this case, the output gives the estimated line:
$$
Y=150.14+0.362x_{1}-3163.56x_{2}
$$

