---
title: Information theory
tags: Math
aside:
  toc: true
---

이 글은 [https://en.wikipedia.org/wiki/Information_theory](https://en.wikipedia.org/wiki/Information_theory), [https://ratsgo.github.io/statistics/2017/09/22/information/](https://ratsgo.github.io/statistics/2017/09/22/information/), [https://reniew.github.io/17/](https://reniew.github.io/17/) 등을 참고하여 작성되었습니다.

<!--more-->

---

## 1. Introduction
### 1) Information theory
- Signal에 내재된 정보의 양을 측정하는 응용수학의 한 갈래
- 정보 이론은 최적의 code를 디자인하고, message의 기대 길이를 계산하는데 도움이 된다.
- ML에서는 확률분포의 특성을 알아내거나, 확률분포 간의 유사성을 정량화하는 데 사용된다.
- **Claude Elwood Shannon (1916~2001)** 이라는 전설적인 분께서 처음 도입하였다. <br>
![jpg](https://media.newyorker.com/photos/5909765cc14b3c606c1089f4/master/w_1023,c_limit/Roberts-Claude-Shannon.jpg){: width="200"}
### 2) Key idea
- 자주 발생하지 않는 사건은 자주 발생하는 사건보다 정보량이 많다. (informative)
- 독립 사건은 추가적인 정보량 (additive information)을 가진다.

<br>

## 2. Shannon Entropy
### 1) Information content(self-information, surprisal)
- 위의 idea를 만족시키면서 어떤 사건의 정보량을 나타낼 수 있는 함수이다.
- **$x$의 값을 가지는 확률변수 $X$(pmf: $p(X=x)$)의 information content $I_X(x)$** <br>
$I(X=x) = I_X(x) \equiv log \frac{1}{p(x)} = -log \ p(x)$
- **발생할 확률이 $P$인 사건 $E$에 대한 information content** <br>
$I(E) \equiv log \frac{1}{P} = -log \ P$
- 예를 들어, <br>
동전을 던져 앞면이 나오는 사건의 정보량 $= -log \frac{1}{2} = 1$ <br>
주사위를 던져 1이 나오는 사건의 정보량 $= -log \frac{1}{6} = 2.58$
- $I_X(x)$에서 $log$의 밑이 2인 경우, 단위를 Shannon(Sh 혹은 bit)이라 부르고, 자연상수 $e$를 밑으로 하는 경우 nat(내트), 10인 경우 hartleys(Hart, ban, dit)라고 부른다.


### 2) Entropy(information entropy, Shannon entropy)
- 모든 사건에 대한 정보량의 기댓값을 의미한다.
- **확률변수 $X$(pmf: $p(X)$, pdf: $f(X)$)에 대한 entropy $H(X)$** <br>
$H(X) \equiv E[I(X)] = E[-log \ p(X)] = -\sum_x p(x) \ log \ p(x) \textit{ or } -\int f(x) \ log \ f(x) dx$
- Shannon entropy는 전체 사건의 확률분포에 대한 불확실성을 정량화한 값으로 사용된다.
- 서로 독립인 두 확률변수는 Shannon entropy는 각 확률변수의 entropy의 합과 같다.
- 아래의 그래프는 동전을 한 번 던졌을 때 Shannon entropy의 값을 나타낸다. $Pr(X=1)=0.5$ 인 경우 가장 큰 entropy를 가지므로 최대 1bit 만으로도 동전 던지기의 결과값을 전송할 수 있다는 것을 알 수 있다. <br>
![jpg](https://upload.wikimedia.org/wikipedia/commons/thumb/2/22/Binary_entropy_plot.svg/450px-Binary_entropy_plot.svg.png){: width="300"}

### 3) Kullbak-Leibler divergence(KL divergence, relative entropy, information divergence, information gain)
- **Kullback-Leibler divergence(KLD)**: 두 확률분포의 차이를 계산하는 함수
- KLD는 sampling 과정에서 임의의 확률분포 $q(X)$를 "true" 확률분포 $p(X)$ 대신 사용할 경우 나타나는 entropy의 차이로 해석할 수 있다.
- **확률분포 $p(X)$와 $q(X)$ 간의 차이 $D_{KL}(p(X) \parallel q(X))$(KL divergence of $q(X)$ w.r.t. $p(X)$)** <br>
$D_{KL}(p(X) \parallel q(X)) \equiv E_{X \sim p}[log \frac{p(X)}{q(X)}] = \sum_x p(x) \ log \frac{p(x)}{q(x)} = (-\sum_x p(x) \ log \ p(x)) - (-\sum_x p(x) \ log \ q(x))$
- KLD는 항상 0 이상의 실수이며(Gibb's inequality) $p(X)$와 $q(X)$가 동일한 확률분포일 때 최솟값인 0이 된다.
- KLD는 symmetric 하지 않고($D_{KL}(p \parallel q) \neq D_{KL}(q \parallel p)$), triangle inequality를 만족시키지 않기 때문에 distance라고 하지 않고 divergence(discrimination information)라고 부른다.

### 4) Cross entropy
- **Cross entropy**: 두 확률분포 $p(X)$와 $q(X)$에 대하여, $p(X)$ 대신 $q(X)$를 사용하여 $p(X)$를 설명할 때 필요한 정보량
- **Cross entropy H(p, q)** <br>
$H(p, q) = H(p) + D_{KL}(p \parallel q) = E_{X \sim p}[-log \ q(X)] = \sum_x p(x) (-log \ q(x)) \textit{ or } \int p(x) (-log \ q(x)) dx$
- 데이터 분포 $p(X)$를 고정시켰을 때, cross entropy를 최소화시키는 분포 $q(X)$를 찾는다는 것은 KLD를 최소화시키는 분포 $q(X)$를 찾는다는 것과 동일한 의미이다.
