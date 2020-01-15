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

```
# Pseudocode
N: number of data
B: batch size

data: (X_train, y_train)
W: weight vector
loss: loss function of weight vector
```

## 0. Before using Gradient Descent
비효율적인 zigzag path(jittering)로 학습되는 것을 방지하기 위하여, 모든 feature의 scale을 동일하게 맞춰주어야한다.

## 1. (Batch) Gradient Descent (GD)
전체 데이터에 대하여 gradient를 계산하고 gradient descent를 수행한다.

```python
# 1 epoch
gradient ← compute_gradient(loss, data, W)
W ← W - learning_rate * gradient
```

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

```python
# 1 epoch
while N // B iterations
    sample mini-batch from data
    gradient ← compute_gradient(loss, mini-batch, W)
    W ← W - learning_rate * gradient
```

## 3. SGD with Momentum (Momentum SGD)
가속도(탄력)의 개념을 추가하여 속도에 gradient를 더한 값으로 gradient descent를 수행한다.

- SGD의 문제점들(poor conditioning, local minima/saddle point, gradient noise)을 해결하는데 도움이 된다.(velocity를 구할 때, 평균을 구하는 것처럼 noise를 경감시키는 효과가 있다)

![jpg](/images/2020-01-15-optimizer/20200115_001.jpg)
![jpg](/images/2020-01-15-optimizer/20200115_002.jpg)

- 일반적으로 $\rho$로 0.9 혹은 0.99를 사용하고, velocity의 초깃값으로 0를 사용한다.


```python
while N // B iterations
    sample mini-batch from data
    gradient ← compute_gradient(loss, mini-batch, W)
    velocity ← friction_rate * velocity + gradient
    W ← W - learning_rate * velocity
```

## 4. SGD with Nesterov Momentum
현재 위치에서 gradient를 계산하는 momentum update와는 달리, velocity만으로 update한 지점에서 계산한 gradient를 사용하여 gradient descent를 수행한다.

![jpg](/images/2020-01-15-optimizer/2020011552.jpg)

```python
# 1 epoch
while N // B iterations
    sample mini-batch from data
    velocity ← friction_rate * velocity + gradient
    gradient ← compute_gradient(loss, mini-batch, W + velocity)
    W ← W - learning_rate * velocity
```
