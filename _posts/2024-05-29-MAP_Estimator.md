---
title: MAP Estimator
author: SeHoon
date: 2024-05-29 09:02:30 +0900
categories: [Mathematics, Estimator]
tags: [Mathematics, Statistics, Kalman Filter, Estimator]
math: true
mermaid: true
---

# MAP(Maximum A Posteriori) Estimator

According to the [Bayes Theorem](https://csh970605.github.io/posts/Bayes_Theorem/), a [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) of an unknown [random vector](https://csh970605.github.io/posts/Rand_Vector/#random-vector) $X$ conditioned on a measurement vector $Z_{k} = z_{k}$ is given as follows:

<center>

$p_{X \mid Z_{k}}(x \mid z_{k}) = \frac{p_{Z_{k} \mid X}(z_{k} \mid x) p_{X}(x)}{p_{Z_{k}}(z_{k})}$
</center>

where

+ $p_{X}(x)$ : A probability density function of $X$ known a priori before a vector $Z_{k}$ is measured as $z_{k}$


+ $p_{Z_{k}}(z_{k})$ : A probability density function of the set of measurement vectors $Z_{k}$, representing the probability information of the measurement process.

+ $p_{Z_{k} \mid X}(z_{k} \mid x)$ : A [conditional probability](https://csh970605.github.io/posts/Probability_RandomVector/#conditional-probability) density function of $Z_{k}$ conditioned on $X=x$. It is a likelihood function that represents how often a specific set of measurement vectors $z_{k}$ appears depending on $x$.

+ $p_{X \mid Z_{k}}(x \mid z_{k})$: A conditional probability density function of X given as $Z_{k} = z_{k}$ post-measurement.
<br><br>


MAP estimator is defined as the estimation value of $X$ when the conditional probability density function of the unknown random vector $X$ is at its maximum value.
As an image:
<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/d0ef1ffa-ad62-430d-baa9-58d5a9057220">
</center><br><br>

As a formula:

<center>

$\hat{x}^{MAP} = \arg\max \ (p_{X \mid Z_{k}}(x \mid z_{k}))$

$= \arg\max \ (p_{Z_{k}\mid X}(z_{k} \mid x)p_{X}(x))$
</center>