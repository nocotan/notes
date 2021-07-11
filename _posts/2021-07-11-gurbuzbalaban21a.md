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

#### Problem Setup

Focus on the case when $f$ is a quadratic, which arises in linear regression:

$$
\begin{equation}
\min_{x\in\mathbb{R}^d}F(x) \coloneqq \frac{1}{2}\mathbb{E}_{(a,y)\sim\mathcal{D}}\Big[(a^Tx - y)^2\Big],
\end{equation}
$$

The curvature, i.e. the value of second partial derivatives, of this objective around a minimum is determined by the Hessian matrix $\mathbb{E}[aa^T]$ which depends on the distribution of $a$. In this setting, SGD with batch-size $b$ leads to the iterations

$$
\begin{align}
x_k &= M_kx_{k-1} + q_k\quad \text{with}\quad M_k\coloneqq I-\frac{\eta}{b}H_k, \\
H_k &\coloneqq \sum_{i\in\Omega_k}a_ia_i^T,\quad q_k\coloneqq \frac{\eta}{b}\sum_{i\in\Omega_k}a_iy_i,
\end{align}
$$

where $\Omega_k\coloneqq \lbrace b(k-1) + 1, b(k-1) + 2,\dots bk \rbrace$ with $|\Omega_k|=b$.
The following assumptions on the data throughout the paper:

- (A1) $a_i$'s are i.i.d. with a continuous distribution supported on $\mathbb{R}^d$ with all the moments finite.
- (A2) $y_i$ are i.i.d with a continuous density whose support is $\mathbb{R}$ with all the moments finite.

$$
\begin{align}
h(s) &\coloneqq \lim_{k\to\infty}\Big(\mathbb{E}\Big[\lVert M_kM_{k-1}\dots M_1\rVert \Big]\Big)^{\frac{1}{k}}, \\
\rho &\coloneqq \lim_{k\to\infty}(2k)^{-1}\log\Big(\text{largest eigenvalue of $\prod^T_k\prod_k$}\Big)
\end{align}
$$

**_Theorem 2_** _Consider the SGD iterations. If $\rho<0$ and there exists a unique positive $\alpha$ such that $h(\alpha)=1$, then SGD admits a unique stationary solution $x_\infty$ and the SGD iterations converge to $x_\infty$ in distribution, where the distribution of $x_\infty$ satisfies_

$$
\lim_{t\to\infty}t^\alpha\Pr\Big(u^Tx_\infty > t \Big) = e_\alpha(u), \quad u\in\mathbb{S}^{d-1},
$$
for some positive and continuous function $e_\alpha$ on $\mathbb{S}^{d-1}$.


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

