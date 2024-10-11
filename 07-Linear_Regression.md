# Linear Regression

## 1. Regression

### The correlation coefficient

$$
\rho=\frac{1}{n}\sum_{i=1}^{n}(\frac{x_i-\mu_x}{\sigma_x})(\frac{y_i-\mu_y}{\sigma_y})
$$
$\mu_x$, $\mu_y$ are the averages of $x_1,x_2,...,x_n$ and $y_1,y_2,...,y_n$, and $\sigma_x$ and $\sigma_y$ are the standard deviations.

Standardization shows the degree and direction of deviation of the sample from the mean.

```r
rho <- mean(scale(x) * scale(y))

rho <- cor(x, y)
```

`var`, `sd`, `cor` use $n-1$ as their denominator

**Sample correlation is a random variable**

because the sample correlation is an average of independent draws, the central limit actually applies. Therefore, for large enough $N$, the distribution of _sample correlation_ is approximately normal with expected value $\rho$. The standard deviation, which is somewhat complex to derive, is $\sqrt{\frac{1-r^2}{N-2}}$.

**Correlation is not always a useful summary**

###  Conditional expectations

The statistical notation for the conditional expectation is:

$$
E(Y|X=x)
$$

However, a challenge when using this approach to estimating conditional expectations is that, for continuous data, we don’t have many data points matching exactly one value in our sample.

A practical way to improve these estimates of the conditional expectations is to define strata of observations with similar value of x. Stratification followed by **boxplots** lets us see the distribution of each group

### The regression line

$$
\begin{aligned}
&\left(\frac{\hat{Y}-\mu_Y}{\sigma_Y}\right) = \rho\left(\frac{x-\mu_X}{\sigma_X}\right) \\
&\hat{Y}=\mu_Y + \rho\left(\frac{x-\mu_X}{\sigma_X}\right)\sigma_Y \\
&\hat{Y}=b + mx,\ b=\mu_Y - m\mu_X,\ m=\rho\frac{\sigma_Y}{\sigma_X}
\end{aligned}
$$

**Regression improves precision**: We use a Monte Carlo simulation

lower standard error than conditional expectations

### Bivariate normal distribution

A more technical way to define the bivariate normal distribution is the following: if $X$ is a normally distributed random variable, $Y$ is also a normally distributed random variable, and the conditional distribution of $Y$ for any $X=x$ is approximately normal, then the pair is approximately bivariate normal.

if our data is approximately bivariate, then the conditional expectation, the best prediction of $Y$ given we know the value of $X$, is given by the regression line.

### There are two regression lines

If we reverse the predict order, this is not determined by computing the inverse function of $E(Y|X=x)$. We need to compute $E(X|Y=y)$

### Linear models

$$
Y_i=\beta_0+\beta_1 x_i+\varepsilon_i,\ i=1,...N
$$

For the interpretability of intercept $\beta_0$, we can rewrite the formula:

$$
Y_i=\beta_0+\beta_1 (x_i - \bar{x})+\varepsilon_i,\ i=1,...N,\ \bar{x}=\frac{1}{N}\sum_{i=1}^{N}x_i
$$

### Least Squares Estimates

Find $\beta_S$ to minimize the distance of the fitted model to the data: residual sum of squares (RSS).

$$
RSS=\sum_{i=1}^{n}\{y_i-(\beta_0+\beta_1x_i)\}^2
$$

I `R` we use `lm` to fit this model.

The most common way we use `lm` is by using the character `~` to let `lm` know which is the variable we are predicting (left of `~`) and which we are using to predict (right of `~`). The intercept is added automatically to the model that will be fit.

 We can use the function `summary` to extract more of this information

**LSE are random variables**

**Predicted values are random variables**

### Diagnostic plots

The function `plot` applied to an `lm` object automatically plots six plots, and the argument `which` let’s you specify which you want to see.