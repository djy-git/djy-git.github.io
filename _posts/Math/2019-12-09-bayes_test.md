---
title: Bayesian hypothesis testing
tags: Math
aside:
  toc: true
---

<!--more-->

# 1. Hypothesis testing problem
$ H_0 : \theta \in \Theta_0 \quad \text{vs} \quad H_1: \theta \in \Theta_1 \quad (\Theta_0 ∪ \Theta_1 = \Theta = \text{whole parameter space})$

# 2. Bayesian approach
1. Calculate the posterior prob. for each model ($\Theta_0, \Theta_1$): $ \pi(H_0 | x), \pi(H_1 | x) $
2. Support the hypothesis that has larger posterior prob.

# 3. Calculate posterior
1. Posterior $ \pi(H_i | x) $
$$
\begin{equation}
\begin{aligned}
  \pi(H_i | x)
  &\propto p(H_i) f(x | H_i) \\
  &\propto p(H_i) \int_{\theta \in \Theta_i} f(x | \theta, H_i) \pi(\theta | H_i) d\theta \\
  &= p(H_i) \int_{\theta \in \Theta_i} f(x | \theta) \pi(\theta | H_i) d\theta \\
  &= \color{blue}{\pi_i} \int_{\theta \in \Theta_i} f(x | \theta) \color{blue}{g_i(\theta)} d\theta \\
\end{aligned}
\end{equation}
$$
2. 
