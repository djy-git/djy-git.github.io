---
title: Optimization methods based on gradient
tags: Theory
aside:
  toc: true
---

<!--more-->
# Remarks
이 글은 [CS231n](http://cs231n.github.io/) 강의를 기반으로 작성되었습니다.

---

## Notation
$W$: Weight vector <br>
$L(W)$: Loss function with weight $W$ <br>
$\eta$: Learning rate(step size) <br>
$\rho$: Friction rate
$N$: number of data <br>
$B$: batch size <br>

## 0. Before using Gradient Descent
비효율적인 zigzag path(jittering)로 학습되는 것을 방지하기 위하여, 모든 feature의 scale을 동일하게 맞춰주어야한다.

## 1. (Batch) Gradient Descent (GD)
전체 데이터에 대하여 gradient를 계산하고 gradient descent를 수행한다.

- **Algorithm (1 epoch)** <br>
$W_{t+1} ← W_t - \eta \nabla L(W_t)$


## 2. Stochastic Gradient Descent (SGD)
학습시킬 때마다 sample(mini-batch)을 뽑아 gradient를 계산하고 gradient descent를 수행한다.

- **Stochastic?** <br>
전체 데이터에 대한 gradient를 계산해야하나, 실제로 사용하기엔 너무 계산량이 크다. <br>
그래서 적은 개수의 sample에 대한 sample gradient를 계산하여 full gradient를 추정하는 방식을 사용하게 되었는데, <br>
Monte Carlo method와 유사하기 때문에 stochastic 이라는 이름이 붙여졌다. <br>

- **Stop in local minima / saddle point** <br>
Gradient = 0 인 지점에서 학습이 멈추는 문제점이 있다.

- **Noise from sampling(mini-batch)** <br>
Full gradient를 추정하는 과정에서 생기는 noise로 인해 최적의 학습을 하기 어렵다.

- **Algorithm (1 epoch)** <br>
while $N$ // $B$ iterations <br>
&emsp; Sample mini-batch from data <br>
&emsp; $W_{t+1} ← W_t - \eta \ \nabla L(W_t)$ <br>


## 3. SGD with Momentum (Momentum SGD)
가속도(탄력)의 개념을 추가하여 속도에 gradient를 더한 값으로 gradient descent를 수행한다.

- SGD의 문제점들(poor conditioning, local minima/saddle point, gradient noise)을 해결하는데 도움이 된다.(velocity를 구할 때, 평균을 구하는 것처럼 noise를 경감시키는 효과가 있다)

![jpg](/images/2020-01-15-optimizer/20200115_001.jpg)
![jpg](/images/2020-01-15-optimizer/20200115_002.jpg)

- 일반적으로 friction rate $\rho$를 0.9 혹은 0.99로 사용하고, velocity $v$의 초깃값으로 0를 사용한다.

- **Algorithm (1 epoch)** <br>
while $N$ // $B$ iterations <br>
&emsp; Sample mini-batch from data <br>
&emsp; $v_{t+1} ← \rho v_t + \nabla L(W_t)$ <br>
&emsp; $W_{t+1} ← W_t - \eta \ v_{t+1}$ <br>


## 4. SGD with Nesterov Momentum
현재 위치에서 gradient를 계산하는 momentum update와는 달리, velocity만으로 update한 지점에서 계산한 gradient를 사용하여 gradient descent를 수행한다.

![jpg](/images/2020-01-15-optimizer/2020011552.jpg)

- **Algorithm (1 epoch)** <br>
while $N$ // $B$ iterations <br>
&emsp; Sample mini-batch from data <br>
&emsp; $v_{t+1} ← \rho v_t - \eta \ \nabla L(W_t + \rho v_t)$ <br>
&emsp; $W_{t+1} ← W_t + v_{t+1}$ <br> <br>
이 식을 다음과 같이 현재의 velocity와 과거의 velocity 간의 오류를 수정하는 항목과의 결합으로도 생각할 수 있다. <br><br>
Let $\tilde{W}_t = W_t + \rho v_t$ <br>
while $N$ // $B$ iterations <br>
&emsp; Sample mini-batch from data <br>
&emsp; $v_{t+1} ← \rho v_t - \eta \ \nabla L(\tilde{W}_t)$ <br>
&emsp; $\tilde{W}_{t+1} ← \tilde{W}_t - \rho v_t + (1 + \rho) v_{t+1}$ <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;&nbsp; $\tilde{W}_t + v_{t+1} + \rho(v_{t+1} - v_t)$ <br>
