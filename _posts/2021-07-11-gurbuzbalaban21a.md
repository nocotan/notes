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

**Remark:** One peculiar property of SGD is that depending on the choice of $\eta$ and $b$, the algorithm can exhibit significantly different behaviors in terms of the performance on unseen test data.

The important properties of SGD that are currently known are as follows
- larger $\eta/b$ yields better generalization;
- the flat-minima argument, they concluded that the ratio η/b determines the flatness of the minima found by SGD;
- a power law distribution to the empirical spectral density of individual layers and illustrated that heaviertailed weight matrices indicate better generalization.

### Main Results

In this paper, the authors argue that these three seemingly unrelated perspectives for generalization are deeply linked to each other.

**Claim:** depending on the choice of the algorithm parameters $\eta$ and $b$, the dimension $d$, and the curvature of $f$, SGD exhibits a heavy-tail phenomenon, meaning that the law of the iterates converges to a heavy-tailed distribution.


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

### References
- Gurbuzbalaban, M., Simsekli, U. &amp; Zhu, L.. (2021). The Heavy-Tail Phenomenon in SGD. <i>Proceedings of the 38th International Conference on Machine Learning</i>, in <i>Proceedings of Machine Learning Research</i> 139:3964-3975 Available from http://proceedings.mlr.press/v139/gurbuzbalaban21a.html.

