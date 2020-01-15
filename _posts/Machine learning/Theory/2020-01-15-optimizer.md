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
$W$: Weight vector \\
$L(W)$: 
```
# Train data
data: (X_train, y_train)  # N: number of data
W: weight vector
loss: loss function of weight vector (L(W))
```

## 1. (Batch) Gradient Descent
전체 데이터에 대하여 gradient를 계산하여 gradient descent를 수행한다.

1. $\nabla_W L(W)$ 계산
2. $W$ ← $W - \eta \cdot \nabla_W L(X)$ ($\eta$: learning rate, step size)


```python
# 1 epoch
gradient ← evaluate_gradient(loss, data, W)
W ← W - learning_rate * gradient
```
