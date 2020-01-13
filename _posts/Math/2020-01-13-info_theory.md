---
title: Information theory
tags: Math
aside:
  toc: true
---

이 글은 [https://ratsgo.github.io/statistics/2017/09/22/information/](https://ratsgo.github.io/statistics/2017/09/22/information/), [https://reniew.github.io/17/](https://reniew.github.io/17/) 등을 참고하여 작성되었습니다.

<!--more-->

---

## 1. Introduction
### 1) Information theory
- Signal에 내재된 정보의 양을 측정하는 응용수학의 한 갈래
- 정보 이론은 최적의 code를 디자인하고, message의 기대 길이를 계산하는데 도움이 된다.
- ML에서는 확률분포의 특성을 알아내거나, 확률분포 간의 유사성을 정량화하는 데 사용된다.
- **Claude Elwood Shannon (1916~2001)** 이라는 전설적인 분께서 처음 도입하였다. <br>
![jpg](https://media.newyorker.com/photos/5909765cc14b3c606c1089f4/master/w_1023,c_limit/Roberts-Claude-Shannon.jpg){: width="100"}
### 2) Key idea
- 자주 발생하지 않는 사건은 자주 발생하는 사건보다 정보량이 많다. (informative)
- 독립 사건은 추가적인 정보량 (additive information)을 가진다.

<br>

## 2. Shannon Entropy
### 1) Information
- 위의 idea를 만족시키면서 어떤 사건의 정보량을 나타낼 수 있는 함수이다.
- **확률변수 X의 값이 x인 사건의 정보량 $I(X=x)$** <br>
$I(X=x) = log \frac{1}{P(x)} = -log P(x)$
- 예를 들어, <br>
동전을 던져 앞면이 나오는 사건의 정보량 $= -log \frac{1}{2} = 1$ <br>
주사위를 던져 1이 나오는 사건의 정보량 $= -log \frac{1}{6} = 2.58$
- 정보량 $I(X=x)$ 에서 $log$ 의 밑이 2인 경우, 단위를 shannon(혹은 bit)라고 부르고, 자연상수 $e$를 밑으로 하는 경우 nat(내트)라고 부른다.

### 2) Shannon entropy(Entropy)
- 모든 사건에 대한 정보량의 기댓값을 의미한다.
- **확률변수 X의 분포 p(X)에 대한 Shannon entropy H(p)** <br>
$H(p) = H(X) = E_{X \sim P}[I(X)] = E_{X \sim p}[-log \ p(X)] = \Sigma_x p(x) (-log \ p(x)) \textit{ or } \int p(x) (-log \ p(x)) dx$
- Shannon entropy는 전체 사건의 확률분포에 대한 불확실성을 정량화한 값으로 사용된다.
- 서로 독립인 두 확률변수는 Shannon entropy는 각 확률변수의 entropy의 합과 같다.
- 아래의 그래프는 동전을 한 번 던졌을 때 Shannon entropy의 값을 나타낸다. $Pr(X=1)=0.5$ 인 경우 가장 큰 entropy를 가지므로 최대 1bit 만으로도 동전 던지기의 결과값을 전송할 수 있다는 것을 알 수 있다. <br>
![jpg](https://upload.wikimedia.org/wikipedia/commons/thumb/2/22/Binary_entropy_plot.svg/450px-Binary_entropy_plot.svg.png){: width="100"}

### 3) KL Divergence
- Kullback-Leibler Divergence(KLD): 두 확률분포의 차이를 계산하는 함수
- 어떤 데이터 분포 $P(X)$ 와 또다른 데이터 분포 $Q(X)$ 간의 차이를 KLD를 활용해 구할 수 있다. <br>
$D_{KL}(P \parallel Q) = E_{X \sim p}[log \frac{p(X)}{q(X)}] = E_{X \sim p}[log \ p(X) - log \ Q(X)]$
- $p(X)$와 $q(X)$가 동일한 확률분포라면 KLD는 0이 된다. $D_{KL}(p \parallel q) \neq D_{KL}(q \parallel p)$ 이기 때문에 distance 대신 divergence 라고 한다.
- KLD는 어떤 확률분포 p(X)에 대하여, sampling 과정에서
