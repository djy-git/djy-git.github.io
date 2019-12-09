---
title: Bayesian linear regression
tags: Math
aside:
  toc: true
---

<!--more-->

# I. Notations
$ \text{Target vector } Y = (Y_1, \cdots, Y_n)^T \in \mathbb{R}^n $ <br>
$ \text{Input vector (considered as const.) } X = (x_{ij}) \in \mathbb{R}^{n \times p} $ <br>
$ \text{Coefficient vector } \beta = (\beta_1, \cdots, \beta_p)^T \in \mathbb{R}^p $ <br>
$ \text{Variance } \sigma^2 \in \mathbb{R} $

# II. Model
$ Y \mid \beta, \sigma^2 \sim N_n(X\beta, \sigma^2 I_n) $

# III. Priors
## 1. Zellner's g-prior
### 1) Prior
$$
\beta \mid \sigma^2 \sim N_p(\beta_0, \color{blue}{g} \sigma^2 (X^T X)^{-1}) \quad\quad \cdots \quad\quad \color{blue}{g} \in \mathbb{R}^+ \\
\sigma^2 \sim \pi(\sigma^2) = \frac{1}{\sigma^2} \quad\quad \cdots \quad\quad \text{Jeffreys' prior}
$$

### 2) Posterior
$$
\beta \mid \sigma^2, y \sim N_p(\frac{1}{g+1}\beta_0 + \frac{g}{g+1}\hat{\beta}, \frac{g}{g+1}\sigma^2 (X^T X)^{-1}) \\
\sigma^2 \mid y \sim IG(\frac{n}{2}, \frac{n \hat{\sigma}^2}{2} + \frac{1}{2(g+1)} (\hat{\beta}-\beta_0)^TX^TX(\hat{\beta}-\beta_0))
$$
Posterior 계산이 용이하기에 Bayesian linear regression에서 가장 많이 사용됩니다.

### 3) Choice of $g$
다음과 같은 3가지 문제가 발생하지 않도록 $g$를 선택해야 합니다. <br>

$ B(M_\gamma, M_{null}) = \frac{(1 + g)^{\frac{n - p_\gamma - 1}{2}}}{(1 + g(1 - R_\gamma^2))^{\frac{n - 1}{2}}} = (\frac{1 + g}{1 + g[1 - R_\gamma^2]})^{\frac{n-1}{2}} (1+g)^{\frac{-p_\gamma}{2}}$

1. $ B(M_\gamma, M_{null}) \to 0 \quad \text{as} \quad g \to \infty $ <br>
$g$가 커질수록 $ M_\gamma $와 무관하게 $ M_{null} $을 선호하는 문제가 발생할 수 있습니다. <br>
⇒ **Lindley's paradox**: $H_1$ 하에서의 prior balance($g$)를 너무 크게 만들어버리면 항상 $H_0$를 지지하게 되는 현상
<br><br>
2. $ B(M_\gamma, M_{null}) \to \infty \quad \text{as} \quad n \to \infty \quad \text{with a fixed } g $ <br>
$n$이 커질수록 $M_\gamma$와 무관하게 $M_\gamma$를 선호하는 문제가 발생할 수 있습니다. <br>
⇒ **Model selection consistency**: If $M_\ast$ is the true model, $ B(M_\ast, M_{null}) \to \infty \quad \text{as} \quad n \to \infty $ for any other $M_\gamma$
<br><br>
3. $ B(M_\gamma, M_{null}) \to (1+g)^\frac{n-p_\gamma-1}{2} \quad \text{as} \quad R_\gamma^2 \to 1 \quad \text{with a fixed } g $ <br>
$R_\gamma^2$이 1에 가까워질수록 Bayes factor가 발산하는 것이 아니라 특정값으로 수렴하는 문제가 발생할 수 있습니다. <br>
⇒ **Information paradox**: $R_\gamma^2$이 1에 수렴한다는 정보가 있음에도 Bayes factor가 계속 증가하지 않는 현상

따라서, 이러한 문제가 발생하지 않도록 $g$를 data에 의존하는 fully Bayesian approach를 통해 정할 수 있습니다. <br>
즉, hyp. $g$에 다시 prior(hyper prior)를 주는 방법입니다. <br>

1.
