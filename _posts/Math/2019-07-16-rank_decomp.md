---
layout: article
title: Rank factorization
tags: Math
sidebar:
  nav: docs-en
aside:
  toc: true
---

이번에 살펴볼 내용은 neural network를 구축할 때 기본적으로 머릿속에 담고 있어야하는 내용인 ***rank factorization*** 에 대해서 알아보겠습니다.  
자세한 내용은 [https://en.wikipedia.org/wiki/Rank_factorization](https://en.wikipedia.org/wiki/Rank_factorization ) 을 참조하세요.
<br>

*For all* $A$, there are $B$ and $C$ such that <br> - $A = BC$
<br> - $A \in \mathbb{R^{m \times n}}$, *rank $A$ = $r$*
<br> - $B \in \mathbb{R^{m \times r}}$, *rank $B$ = $r$*
<br> - $C \in \mathbb{R^{r \times n}}$, *rank $C$ = $r$*
{:.success}

1. *Let $\mathbf{b}_i \doteq$ i'th basis of $\mathbb{C}(A)$ <br> $\mathbf{a}_j \doteq$ j'th column vector of $A$*

2. *$\mathbf{a}_j = \sum_{i=1}^r c_{ij} \mathbf{b}_i$*
*$\mathbf{a}_j $*