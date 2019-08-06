---
layout: article
title: Ridge, Lasso regression, Elastic net
tags: Theory
sidebar:
  nav: docs-en
---

**Ridge regression (Tikhonov regularization)**은 cost funtion에 l2 regularization ($\alpha \Sigma_i \theta_i^2$)이 추가된 선형 회귀입니다.
{:.success}

<!-- more -->

---

# 1. Ridge regression
## 1) Cost function
$$
J(\theta) = \sum_{i=1}^m (y^{(i)} - \hat{y}^{(i)})^2 + \alpha \frac{1}{2}\sum_{i=1}^n\theta_i^2
\quad \text{(Bias } \theta_0 \text{ is not regularized)} \\
= ||\mathbf{y} - \mathbf{\hat{y}}||^2_2 + \alpha ||w||^2_2
$$

<br>
## 2) Normal equation
$ \hat{\theta} = (X^TX + \alpha I')^{-1}X^Ty \quad \text{(} I' \text{ is } I^{(n+1) \times (n+1)} \text{ whose bias column is 0)}$

<br>
## 3) API function

{% highlight python linenos %}

# Normal equation
from sklearn.linear_model import Ridge

ridge_reg = Ridge(alpha=1, solver='cholesky')  # solver='saga': improved stochastic average gradient
ridge_reg.fit(X, y)
ridge_reg.predict(X_test)


# Stochastic Gradient Descent
from sklearn.linear_model import SGDRegressor

sgd_reg = SGDRegressor(max_iter=1000, penalty='l2')
sgd_reg.fit(X, y.ravel())
sgd_reg.predict(X_test)

{% end highlight %}

<br>
# 2. 
