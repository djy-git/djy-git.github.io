---
title: Quadratic form
tags: Math
---

# Remarks
이 글은 [https://en.wikipedia.org/wiki/Quadratic_form#Introduction](https://en.wikipedia.org/wiki/Quadratic_form#Introduction) 등을 참고하여 작성되었습니다.

<!--more-->

---

## 1. Introduction
**Quadratic form**은 homogeneous quadratic polynomial을 의미한다.(모든 항의 차수가 동일) <br>

- 다음과 같이 변수의 개수에 따라 이름이 붙여지기도 한다. <br>
**Unary** <br>
$q(x) = ax^2$ <br><br>
**Binary** <br>
$q(x, y) = ax^2 + bxy + cy^2$ <br><br>
**Ternary** <br>
$q(x, y, z) = ax^2 + bxy + cy^2 + dyz + ez^2 + fzx$ <br>

- 다음과 같은 notation을 사용하기도 한다. <br>
$q(x) = \langle a_1, \cdots, a_n \rangle = a_1x_1^2 + \cdots + a_nx_n^2$

## 2. Real quadratic forms
임의의 $n \times n$ real symmetric matrix $A$는 $n$개의 변수를 가진 quadratic form $q_A$를 다음의 식으로 결정할 수 있다. <br>
$$
\begin{equation}
\begin{aligned}
  q_A(x_1, \cdots, x_n) &= \sum_i \sum_j a_{ij} x_i x_j \\
  &= \mathbf{x}^T A \mathbf{x} \\
  &=
  \begin{pmatrix}
  x_1 & \cdots & x_n \\
  \end{pmatrix}
  \begin{pmatrix}
  a_{11} & \cdots & a_{n1} \\
  \vdots & \ddots & \vdots \\
  a_{n1} & \cdots & a_{nn} \\
  \end{pmatrix}
  \begin{pmatrix}
  x_1 \\
  \vdots \\
  x_n \\
  \end{pmatrix}
\end{aligned}
\end{equation}
$$
