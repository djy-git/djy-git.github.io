---
layout: article
title: Bias-Variance Tradeoff
tags: Theory
sidebar:
  nav: docs-en
aside:
  toc: true
---

**Bias-variance tradeoff** <br> 모델의 일반화 오차는 모델의 편향의 제곱과 분산과 데이터의 노이즈의 합으로 표현된다.
{:.success}

<!-- more -->

# Remarks
본 포스팅은 **[https://www.datacamp.com/community/tutorials/tutorial-ridge-lasso-elastic-net](https://www.datacamp.com/community/tutorials/tutorial-ridge-lasso-elastic-net)** 을 참고하여 작성되었습니다.

---

1. 다음과 같은 linear regression model을 생각해보겠습니다.
$$
Y = X \beta + \epsilon \\
\epsilon \sim N(0, \sigma^2)
$$

<br>
2. 구하고자 하는 true parameter $\beta$를 알지 못하기 때문에 sample들로부터 $\beta$를 추정해야합니다.

<br>
3.

---

![Image](https://res.cloudinary.com/dyd911kmh/image/upload/f_auto,q_auto:best/v1543418451/bias_vs_variance_swxhxx.jpg){:.border}
