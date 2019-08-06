---
layout: article
title: Early stopping
tags: Theory
sidebar:
  nav: docs-en
---

**Early stopping**은 iterative algorithm에서 사용할 수 있는 regularization 방법으로 validation error가 최솟값에 도달하였다고 판단되면 바로 학습을 중지하는 방법입니다.
{:.success}

Epoch에 따른 error 그래프를 그려보면 일반적으로 다음과 같은 형태를 보이게 됩니다. <br>

![Image](https://raw.githubusercontent.com/djy-git/djy-git.github.io/master/_posts/assets/es_1.jpg){:.border} <br>
