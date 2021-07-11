---
title:  "Limits of Sequences"
layout: post
mathjax: true
permalink: "/math/functional_analysis/limits_of_sequences"
---

**_Definition 1.1_** _Suppose we are given a sequence_ $(a_n)^\infty_{n=1}$ _and some_ $\alpha\in\mathbb{R}$. _A sequence_ $(a_n)^\infty_{n=1}$ _is said to converge to_ $\alpha$ _if there exists some_ $N(\epsilon)\in\mathbb{N}$ _for any positive number_ $\epsilon$ _and the following holds:_

$$
N(\epsilon)\leq n \Rightarrow |a_n - \alpha| < \epsilon. \tag{1.1}
$$

_In this case, one can be write as follows._

$$
\lim_{n\to\infty}a_n = \alpha \quad \text{or}\quad a_n\to\alpha\ (n\to\infty).
$$

**_Axiom 1.1 (Weierstrass' axiom)_**
1. _For any subset_ $A\subset\mathbb{R}$ _bounded above, there exists an upper bound_ $\sup A\in\mathbb{R}$.
2. _Similarly, for any subset_ $B\subset\mathbb{R}$ _bounded below, there exists a lower bound_ $\inf B\in\mathbb{R}$.

In the following, we will review some fundamental facts about the convergence of sequences.

**_Proposition 1.1_** _If a sequence_ $(a_n)^\infty_{n=1}$ _converges to some real number_ $\alpha\in\mathbb{R}$, then $(a_n)^\infty_{n=1}$ is bounded.

**_Proof._** For $\epsilon=1$, there exists $N_1\in\mathbb{N}$ such that $N_1<n \Rightarrow \lvert a_n-\alpha \rvert<1$. Then, we have

$$
N_1 < n \Rightarrow \alpha - 1 < a_n < \alpha + 1.
$$

Since both $b\coloneqq \min\lbrace a_1,a_2,\dots,a_{N_1}\rbrace >-\infty$ and $c\coloneqq \max\lbrace a_1,a_2,\dots,a_{N_1}\rbrace < \infty$ are real numbers, for any $n\in\mathbb{N}$, we have

$$
\min\{\alpha-1, b\} \leq a_n \leq \max\{\alpha+1, c\}. \quad\quad \square
$$

**_Definition 1.2 (Limit superior and limit inferior)_** For any $(a_n)^\infty_{n=1}$,

a. Limit superior $\limsup_{n\to\infty} a_n$ is defined as follows:

  - if $(a_n)^\infty_{n=1}$ is unbounded above,

   $$
    \limsup_{n\to\infty} a_n \coloneqq +\infty.
   $$

   - if $(a_n)^\infty_{n=1}$ is bounded above,

   $$
   \limsup_{n\to\infty} a_n \coloneqq \begin{cases}
   \lim_{p\to\infty}\hat{a}_p & (\text{$(\hat{a}_p)^\infty_{p=1}$ is bounded below}), \\
   -\infty & (\text{$(\hat{a}_n)^\infty_{n=1}$ is unbounded below}), \tag{1.2}
   \end{cases}
   $$

   where, $\hat{a}\_{p}\coloneqq \sup \lbrace a_n \mid n\geq p \rbrace =\sup \lbrace a_p,a_{p+1},\dots \rbrace$.

b. Limit inferior $\liminf_{n\to\infty} a_n$ is defined as follows:

  - if $(a_n)^\infty_{n=1}$ is unbounded below,

  $$
  \liminf_{n\to\infty} a_n \coloneqq -\infty.
  $$

  - if $(a_n)^\infty_{n=1}$ is bounded below,

  $$
  \liminf_{n\to\infty} a_n \coloneqq \begin{cases}
   \lim_{p\to\infty}\check{a}_p & (\text{$(\check{a}_p)^\infty_{p=1}$ is bounded above}), \\
   +\infty & (\text{$(\check{a}_n)^\infty_{n=1}$ is unbounded above}), \tag{1.3}
   \end{cases}
  $$

  where, $\check{a}\_{p}\coloneqq \inf \lbrace a_n \mid n\geq p \rbrace =\inf \lbrace a_p,a_{p+1},\dots \rbrace$.