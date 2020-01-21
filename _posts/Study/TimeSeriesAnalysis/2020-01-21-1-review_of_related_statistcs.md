---
title: 1. Review of Related Statistics
tags: Study_TimeSeriesAnalysis
---

# Remarks
본 글은 [한양대학교 이기천 교수님의 시계열분석 강의 1강](https://www.youtube.com/watch?v=hCl8zTYM4So&list=PLSN_PltQeOyjnE4AnJyQUlHXNwE_hVtKL&index=1)을 정리한 글입니다.

<!--more-->

---

## Time Series and Statistics Necessary
### 1. Time Series
- **Time Series** <br>
A time series is a realization of a sequence (time step) of random variables <br>
Time series $\approx$ a stochastic process of $X_1, X_2, \cdots, X_t, \cdots$ <br>

### 2. White Noise
- **White noise** <br>
A stochastic process $a_0, a_1, \cdots$ is white noise if <br>
the noise is $iid$ random variables with mean $0$ and constant variance $\sigma^2$ <br>
ex) $a_t \stackrel{iid}{\sim} N(0, \sigma^2)$

- **Notation** <br>
$a_t \sim WN(0, \sigma^2)$

### 3. Stationary time Series
모든 time signal을 분석할 수 없기 때문에 stationary time signal이라 가정하고 분석하는 것으로 시작한다.

- **Stationary** <br>
$X_t$ is stationary if its joint distribution does not change

- **Strictly stationary time series** <br>
$n$개의 variables에 대한 CDF $F_{t_1, \cdots, t_n}(x_1, \cdots, x_n) = P(X_{t_1} \leq x_1, \cdots, X_{t_n} \leq x_n)$ 에 대하여, <br>
$F_{t_1, \cdots, t_n}(x_1, \cdots, x_n) = F_{t_1+h, \cdots, t_n+h}(x_1, \cdots, x_n)$ 를 만족시키면 $X_t$가 strictly stationary

- 
