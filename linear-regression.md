# Linear Regression Equation
$$Y = \beta_0 + \beta_1 X_1 + ... + \beta_p X_p + \epsilon$$
* Estimates "true" relationships with $p + 1$ parameters
* $\epsilon$ is the error

$$Y_i = \beta_0 + \beta_1 X_{i1} + ... + \beta_p X_{ip} + \epsilon_i$$
$$\leftrightarrow \mathbf{Y} = \mathbf{X \beta} + \epsilon$$
$$
  \mathbf{Y} =
  \begin{pmatrix}
  Y_1 \\
  Y_2 \\
  \vdots \\
  Y_n
  \end{pmatrix}
  $$

$$
   \mathbf{X} =
   \begin{pmatrix}
   1 & X_{11} & X_{12} & \dots & X_{1p} \\
   1 & X_{21} & X_{22} & \dots & X_{2p} \\
   \vdots & \vdots & \vdots & \ddots & \vdots \\
   1 & X_{n1} & X_{n2} & \dots & X_{np}
   \end{pmatrix}
   $$

$$
   \boldsymbol{\beta} =
   \begin{pmatrix}
   \beta_0 \\
   \beta_1 \\
   \beta_2 \\
   \vdots \\
   \beta_p
   \end{pmatrix}
   $$

$$
  \boldsymbol{\epsilon} =
  \begin{pmatrix}
  \epsilon_1 \\
  \epsilon_2 \\
  \vdots \\
  \epsilon_n
  \end{pmatrix}
  $$

# Ordinary Least Squares (OLS)
* Residual is difference between response and predicted value, OLS minimizes this
$$\hat\beta_{OLS} = (X^TX)^{-1}X^Ty,\ \exists (X^TX)^{-1}$$

# 1. Find if exists relationship between response and predictors
## F-statistic
* TSS = total sum of squares (total variance in response variable $Y$ with respect to mean $\bar Y$)
* RSS = residual sum of squares (measures the variance that remains unexplained after fitting the regression model)
* $F \approx 1$ means that there is probably no relationship, and $F > 1$ means there is probably a relationship

$$TSS = \sum_{i = 1}^n (Y_i - \bar Y)^2$$
$$RSS = \sum_{i = 1}^n (Y_i - \hat Y_i)^2$$
$$F = \frac{(TSS - RSS) / p}{RSS / (n - p - 1)}$$

## t-statistic
$$H_0: \beta_j = 0,\ H_a: \beta_j \neq 0$$
$$t = \frac{\hat\beta_j}{SE(\hat\beta_j)}$$

Note: $SE(\hat\beta_j)$ is standard error of $\hat\beta_j$

$$H_0: t \sim t_{n - p - 1}$$

# 2. Deciding on important variables
Variable selection: determine which predictors associated with response
* $2^p$ possible models for $p$ predictors

# 3. Model fit potential problems
1. If no linear association, use non-linear transformations for $X$
2. Errors are assumed not correlated, but if they are correlated, estimated standard errors tend to underestimate true standard errors. These usually only occur when observations are analyzed over time.
3. Standard errors, CIs, and hypothesis testing require constant variances in error terms. If not (when visualizing residual plot), a solution is to transform $Y$.
4. Outliers might inflate the variance or RSE
5. Collinearity: Two or more predictors might be closely related, making coefficient estimates uncertain.
$$VIF(\hat\beta_j) = \frac{1}{1 - R^2_j}$$
* $R^2_j$ is the $R^2$ predictor from regression of $X_j$
* A $VIF \geq 5$ is large, and we should drop or combine the $j$-th predictor

# Estimate the variance
