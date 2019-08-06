---
layout: article
title: Bias-Variance Tradeoff
tags: Theory
sidebar:
  nav: docs-en
---

**Bias-variance tradeoff** <br> 모델의 일반화 오차는 모델의 편향의 제곱과 분산과 데이터의 노이즈의 합으로 표현된다.
{:.success}

<!-- more -->

# Remarks
본 포스팅은 **[https://www.datacamp.com/community/tutorials/tutorial-ridge-lasso-elastic-net](https://www.datacamp.com/community/tutorials/tutorial-ridge-lasso-elastic-net)** 을 참고하여 작성되었습니다.

---

1. 데이터 X와 Y가 어떠한 target function (true function) $f(X)$와 noise $\epsilon$에 대하여, $Y = f(X) + \epsilon$ 의 관계를 가진다고 가정합니다. <br>
$f(X): \text{target function} \\
\hat{f}(X): \text{estimate of target function} \\
\bar{f}(X): \text{expectation of } \hat{f}(X)$ <br>

2. Target function을 구하기 위해 알고 있는 sample들(train data)로부터 target function를 추정해야합니다. <br>

3. Estimator에 대해서 고려해야할 2가지 중요한 성질로 **bias**와 **variance**가 있습니다. <br>

- **Bias**
Difference between the true population parameter and the expected Estimator. <br>
**Estimate들의 accuracy**를 측정합니다. <br>
$Bias(\hat{\beta}_{OLS}) = E(\hat{\beta}_{OLS}) - \beta$

- **Variance**
**Estimate들의 spread 혹은 uncertainty**를 측정합니다. <br>

$Var(\hat{\beta}_{OLS}) = \sigma^2(X'X)^{-1}$
$\hat{\sigma}^2 = \frac{e'e}{n - m}, \ e = \mathbf{y} - X\hat{\beta}$

5. 다음은 4개의 다른 성질을 가진 estimator들로부터 나온 estimates를 파란색 shot으로 나타낸 그림입니다. <br>
과녁 가운데 bull's eye는 true population parameter $\beta$를 나타냅니다.

![Image](https://res.cloudinary.com/dyd911kmh/image/upload/f_auto,q_auto:best/v1543418451/bias_vs_variance_swxhxx.jpg){:.border}

6. **모델의 오차 (prediction error)**는 3가지 부분으로 나누어집니다. <br>

$$
E(e) = E[(Y - \hat{Y})^2] \\
= E[(f(X) + \epsilon - \hat{f}(X))^2] \\
= E[(f(X) - \hat{f}(X))^2 + \purple{\epsilon^2} + \green{2\epsilon(f(X) - \hat{f}(X))]} \\
= E[(f(X) - \hat{f}(X))^2] + \purple{\sigma^2} + \green{0} \\
= E[(f(X) - \bar{f}(X) + \bar{f}(X) - \hat{f}(X))^2] + \purple{\sigma^2} \quad \cdots \quad \text{let } \bar{f}(X) = E[\hat{f}(X)]\\
= E[(f(X) - \bar{f}(X))^2] + E[(\hat{f}(X) - \bar{f}(X))^2] + E[2(f(X) - \bar{f}(X))\green{(\bar{f}(X) - \hat{f}(X))}] + \purple{\sigma^2}\\
= \blue{(f(X) - \bar{f}(X))^2} + \red{E[(\hat{f}(X) - \bar{f}(X))^2]} + \purple{\sigma^2} \\
= \blue{Bias^2} \ + \ \red{Variance} \ + \ \purple{irreducible \ error}
$$

<br>

$f(X)$가 $X\beta$에 해당하는 linear regression의 경우는 결국 다음과 같이 됩니다.

$ E(e) = \blue{[X\beta - E(X\hat{\beta})]^2} \ + \ \red{E[X\hat{\beta} - E(X\hat{\beta})]^2} \ + \ \purple{\sigma^2} \\ $

7. **OLS estimator는 unbiased estimator**이지만, variance는 클 수 있습니다. <br>
특히 feature들이 크게 연관되어 있거나, feature의 개수가 sample의 개수가 비슷할 정도로 많으면 variance는 거의 무한대에 다다를 수 있습니다. <br>
이를 해결하기 위해 약간의 bias를 추가하여 variance를 낮추는 방법을 사용할 수 있는데, 이러한 방법을  **regularization**이라고 부릅니다. 아래의 그림에서, bias가 0가 되는 오른쪽 끝자락에서부터 bias를 추가하여 왼쪽으로 이동하면 total error가 가장 낮은 *Optimum Model Complexity*에 도달할 수 있는 것을 확인할 수 있습니다.

![Image](https://res.cloudinary.com/dyd911kmh/image/upload/f_auto,q_auto:best/v1543418451/tradeoff_sevifm.png){:.border}
