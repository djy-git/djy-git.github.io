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
$W$: Weight vector \
$L(W)$: Loss function with weight $W$ \
$\eta$: Learning rate(step size)

```
# Pseudocode
N: number of data
B: batch size

data: (X_train, y_train)
W: weight vector
loss: loss function of weight vector
```

## 1. (Batch) Gradient Descent (GD)
전체 데이터에 대하여 gradient를 계산하고 gradient descent를 수행한다.

### Algorithm
1. $\nabla_W L(W)$ 계산
2. $W$ ← $W - \eta \cdot \nabla_W L(X)$

```python
# 1 epoch
gradient ← evaluate_gradient(loss, data, W)
W ← W - learning_rate * gradient
```

## 2. Stochastic Gradient Descent (SGD)
학습시킬 때마다 sample(mini-batch)을 뽑아 gradient를 계산하고 gradient descent를 수행한다. \
- 전체 데이터에 대한 gradient를 계산해야하나, 실제로 사용하기엔 너무 계산량이 크다. \
이에따라 적은 개수의 sample에 대한 sample gradient를 계산하여 full gradient를 추정하는 방식을 사용하게 되었는데, \
Monte Carlo method와 유사하기 때문에 stochastic 이라는 이름이 붙여졌다.

```python
# 1 epoch
while N // B iterations
    sample mini-batch from data
    gradient ← evaluate_gradient(loss, mini-batch, W)
    W ← W - learning_rate * gradient
```

## 3.
