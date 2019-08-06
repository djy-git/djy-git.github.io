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
J(\theta) = \sum_{i=1}^m (y^{(i)} - \hat{y}^{(i)})^2 + \alpha \sum_{i=1}^n\theta_i^2
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
# 2. Lasso regression
## 1) Cost function
$$
J(\theta) = \frac{1}{2}\sum_{i=1}^m (y^{(i)} - \hat{y}^{(i)})^2 + \alpha \sum_{i=1}^n|\theta_i|
\quad \text{(Bias } \theta_0 \text{ is not regularized)} \\
= \frac{1}{2}||\mathbf{y} - \mathbf{\hat{y}}||^2_2 + \alpha ||w||_1 \\
$$

## 2) Ridge vs Lasso
Ridge와 달리 lasso는 덜 중요한 feature의 가중치를 완전히 제거하는 feature selection을 자동으로 하여 sparse model을 만듭니다.

## 3) API function

{% highlight python linenos %}

# Coordinate descent
from sklearn.linear_model import Lasso

ridge_reg = Lasso(alpha=1)
ridge_reg.fit(X, y)
ridge_reg.predict(X_test)


# Stochastic Gradient Descent
from sklearn.linear_model import SGDRegressor

sgd_reg = SGDRegressor(max_iter=1000, penalty='l1')
sgd_reg.fit(X, y.ravel())
sgd_reg.predict(X_test)

{% end highlight %}


<br>
# 3. Elastic net
## 1) Cost function
$$
J(\theta) = \frac{1}{2}\sum_{i=1}^m (y^{(i)} - \hat{y}^{(i)})^2 + r \alpha \sum_{i=1}^n|\theta_i| + (1-r) \alpha \frac{1}{2}\sum_{i=1}^n\theta_i^2
\quad \text{(Bias } \theta_0 \text{ is not regularized)} \\
= \frac{1}{2}||\mathbf{y} - \mathbf{\hat{y}}||^2_2 + r \alpha ||w||_1 + (1-r) \alpha \frac{1}{2}||w||^2_2 \\
$$

## 2) Ridge vs Lasso vs Elastic net
1. 기본: ridge
2. 실사용 feature의 개수가 적다: lasso / elastic net
3. # features > # samples: elastic net
4. 몇 개의 feature가 강하게 연관되어 있다: elastic net
