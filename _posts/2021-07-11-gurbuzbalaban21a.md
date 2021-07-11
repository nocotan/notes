---
title:  "The Heavy-Tail Phenomenon in SGD"
layout: post
mathjax: true
permalink: "/papers/gurbuzbalaban21a"
---

![](https://user-images.githubusercontent.com/10952293/125183255-07241b80-e250-11eb-978f-37425a5c7fa2.png)

- [paper link](http://proceedings.mlr.press/v139/gurbuzbalaban21a.html)
- ICML2021

### TL;DR

- Some of the popular notions of SGD that correlate well with the performance on unseen data are
  -  the ‘flatness’ of the local minimum found by SGD (eigenvalues of the Hessian);
  -  the ratio of the stepsize $\eta$ to the batch-size $b$;
  -  the ‘tail-index’, which measures the heaviness of the tails of the network weights at convergence.
- In this paper, the authors argue that these three perspectives are deeply linked to each other.

### Preliminaries

Consider the following stochastic gradient descent (SGD) procedure:

$$
\begin{align}
x_k &= x_{k-1} - \eta\nabla\tilde{f}_k(x_k - 1), \\
\nabla\tilde{f}_k(x) &\coloneqq \frac{1}{b}\sum_{i\in\Omega_k}\nabla f^{(i)}(x).
\end{align}
$$

### Main Results

### Experimental Results

<div style="text-align: center;">
<img src="https://user-images.githubusercontent.com/10952293/125183331-bfea5a80-e250-11eb-8f3f-1f6e02c50654.png" width="70%">
</div>

<div style="text-align: center;">
<img src="https://user-images.githubusercontent.com/10952293/125183338-caa4ef80-e250-11eb-89b9-35117aea37e5.png" width="70%">
</div>

<div style="text-align: center;">
<img src="https://user-images.githubusercontent.com/10952293/125183425-8e25c380-e251-11eb-98fd-b37fb25283eb.png" width="100%">
</div>