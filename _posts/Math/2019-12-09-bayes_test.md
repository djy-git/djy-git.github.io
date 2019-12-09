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
1. Calculate the posterior prob. for each model ($\Theta_0, \Theta_1$): $ \pi(H_0 \mid x), \pi(H_1 \mid x) $
2. Support the hypothesis that has larger posterior prob.

# 3. Calculate posterior
1. Posterior $ \pi(H_i | x) $ <br>
$$
\begin{equation}
\begin{aligned}
  \pi(H_i | x)
  &\propto p(H_i) \color{red}{f(x | H_i)} \\
  &= \color{blue}{\pi_i} f(x | H_i) \quad \cdots \quad \color{blue}{\pi_i} = p(H_i) \\
  \color{red}{f(x | H_i)}
  &= \int_{\theta \in \Theta_i} f(x | \theta, H_i) \pi(\theta | H_i) d\theta \\
  &= \int_{\theta \in \Theta_i} f(x | \theta) \pi(\theta | H_i) d\theta \quad \cdots \quad \text{Assume f(x | \theta) = f(x | \theta, H_i)} \\
  &= \int_{\theta \in \Theta_i} f(x | \theta) \color{blue}{g_i(\theta)} d\theta \quad \cdots \quad \color{blue}{g_i(\theta)} = \pi(\theta | H_i) \\
\end{aligned}
\end{equation}
$$
2. Compare posterior prob. <br>
$$
P_0 \equiv \pi(H_0 \mid x)
= \frac{f(x, H_0)}{f(x, H_0) + f(x, H_1)}
= \frac{\int_{\theta \in \Theta_0} f(x | \theta) g_0(\theta) d\theta}{\int_{\theta \in \Theta_0} f(x | \theta) g_0(\theta) d\theta + \int_{\theta \in \Theta_1} f(x | \theta) g_1(\theta) d\theta} \\
P_1 \equiv \pi(H_1 \mid x)
= \frac{f(x, H_1)}{f(x, H_0) + f(x, H_1)}
= \frac{\int_{\theta \in \Theta_1} f(x | \theta) g_1(\theta) d\theta}{\int_{\theta \in \Theta_0} f(x | \theta) g_0(\theta) d\theta + \int_{\theta \in \Theta_1} f(x | \theta) g_1(\theta) d\theta}
$$
Support $\text{argmax}_i \pi(H_i \mid x)$

# 4. Bayes factor
1.
