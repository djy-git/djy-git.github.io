---
layout: article
title: Markdown / LaTex notes
tags: Markdown
sidebar:
  nav: docs-en
aside:
  toc: true
---

### 1. Code block
다음과 같이 적어주면 예쁜 syntax highlight를 볼 수 있는데, markdown이 먹히질 않는다..

**markdown**

    {% highlight python linenos %}
    # Code here
    {% endhighlight %}

<br>
### 2. LaTex
- Bold체에도 몇 가지 종류가 있어서 목적에 맞는 문법을 사용하면 원하는 모양을 볼 수 있다.

**Latex**

    \bf{}: 사용 이후에도 적용이 지속된다
    \textbf{}: Text
    \mathbf{}: Vector
    \mathbb{}: Special set (Real set)
    \mathcal{}: Laplace, Fourier transform의 그것

- Color, bold, underline을 동시에 사용할 때 순서를 맞춰주어야 한다.

**Latex**

    \bf{\underline{\color{red}}}

- Some Tex
$ \stackrel{i.i.d.}{\sim} \overset{above}{main} $

**Latex**

    \stackrel{i.i.d.}{\sim}
    \overset{above}{main}


<br>
### 3. Jekyll(kramdown) styles
highlight theme을 tomorrow로 사용할 떄만 사용할 수 있는 것 같다.
- Alert
<br>Class: success, info, warning, error

**markdown**

    Success Text.
    {:.success}

- Tag
<br>Class: success, info, warning, error

**markdown**

    `_`{:.success}

<br>
### 4. Matrix
$$
\begin{aligned}
A =
\begin{pmatrix}
\\
\mathbf{a}_1 & \cdots & \mathbf{a}_n\\
\\
\end{pmatrix} =
\begin{pmatrix}
\\
\mathbf{b}_1 & \cdots & \mathbf{b}_r\\
\\
\end{pmatrix}
\begin{pmatrix}
c_{11} & \cdots & c_{1n}\\
\vdots & \ddots & \vdots\\
c_{r1} & \cdots & c_{rn}\\
\end{pmatrix}
= BC
\end{aligned}
$$

**Latex**

    $$
    \begin{aligned}
    A =
    \begin{pmatrix}
    \\
    \mathbf{a}_1 & \cdots & \mathbf{a}_n\\
    \\
    \end{pmatrix} =
    \begin{pmatrix}
    \\
    \mathbf{b}_1 & \cdots & \mathbf{b}_r\\
    \\
    \end{pmatrix}
    \begin{pmatrix}
    c_{11} & \cdots & c_{1n}\\
    \vdots & \ddots & \vdots\\
    c_{r1} & \cdots & c_{rn}\\
    \end{pmatrix}
    = BC
    \end{aligned}
    $$
<br>

# 5. Image
<img src="https://raw.githubusercontent.com/djy-git/djy-git.github.io/master/_posts/assets/threshold.png">

**markdown**

    <img src="https://raw.githubusercontent.com/djy-git/djy-git.github.io/master/_posts/assets/threshold.png" width="100" height="100">
    ![Image](https://raw.githubusercontent.com/djy-git/djy-git.github.io/master/_posts/assets/prcurve.png){: width="300" height="300"}{:.border}
    ![png](/images/vis_files/vis_3_0.png)

<br>
# 6. Equation aligned
$$
\begin{equation}
\begin{aligned}
    p(x_k | Y_k) &= p(x_k | Y_{k-1}, y_k) \\
    &∝ p(y_k | Y_{k-1}, x_k) p(x_k | Y_{k-1}) \\
    &= p(y_k | x_k) p(x_k | Y_{k-1})
\end{aligned}
\end{equation}
$$

**Latex**

    \begin{equation}
    \begin{aligned}
        p(x_k | Y_k) &= p(x_k | y_k, Y_{k-1}) \\
        &∝ p(y_k | Y_{k-1}, x_k) p(x_k | Y_{k-1}) \\
        &= p(y_k | x_k) p(x_k | Y_{k-1})u
    \end{aligned}
    \end{equation}
