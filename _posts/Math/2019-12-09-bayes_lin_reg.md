---
title: Bayesian linear regression
tags: Math
aside:
  toc: true
---

<!--more-->

# 1. Notations
$ \text{Target vector } Y = (Y_1, \cdots, Y_n)^T \in \mathbb{R}^n $ <br>
$ \text{Input vector (considered as const.) } X = (x_{ij}) \in \mathbb{R}^{n \times p} $ <br>
$ \text{Coefficient vector } \beta = (\beta_1, \cdots, \beta_p)^T \in \mathbb{R}^p $ <br>
$ \text{Variance } \sigma^2 \in \mathbb{R} $

# 2. Model
$ Y \mid \beta, \sigma^2 \sim N_n(X\beta, \sigma^2 I_n) $

# 3. Priors
## 1) Zellner's g-prior
1. Prior
$$
\beta \mid \sigma^2 \sim N_p(\beta_0, \color{blue}{g} \sigma^2 (X^T X)^{-1}) \quad\quad \cdots \quad\quad g \in \mathbb{R}^+
$$

2. Posterior
$$
\beta \mid \sigma^2, y \sim N_p(\frac{1}{g+1}\beta_0 + \frac{g}{g+1}\hat{\beta}, \frac{g}{g+1}\sigma^2 (X^T X)^{-1}) \\
$$
