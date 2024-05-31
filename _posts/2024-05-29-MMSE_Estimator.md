---
title: MMSE Estimator
author: SeHoon
date: 2024-05-22 09:03:00 +0900
categories: [Mathematics, Estimator]
tags: [Mathematics, Statistics, Kalman Filter, Estimator]
math: true
mermaid: true
---

# MMSE(Minimum Mean-Square error) Estimator

When a set of measurment vectors is given $Z_{k} = z_{k}$, MMSE estimator is defined as a estimator that makes conditional average estimation error or conditional mean-square error minimum as follows:

<center>

$J = E[(X-\hat{x})^{T}(X-\hat{x}) \mid Z_{k} = z_{k}]$<br>
$= \int_{-\infty}^{\infty}(x-g(z_{k}))^{T}(x-g(z_{k}))p_{X \mid Z_{k}}(x\mid z_{k})dx$
</center><br>

To make it shorter, MMSE is expressed as follows:

<center>

$\hat{x}^{MMSE} = argmin(E[(X-\hat{x})^{T}(X-\hat{x}) \mid Z_{k} = z_{k}])$
</center><br>

Since $\hat{x} = g(z_{k})$ is a constant value, $J = E[X^{T}x-X^{T}\hat{x} - \hat{x}^{T}X + \hat{x}^{T}\hat{x} \mid Z_{k} = z_{k}] \ = E[X^{T}X \mid Z_{k} = z_{k}] - 2\hat{x}^{T}E[X \mid Z_{k}=z_{k}]+\hat{x}^{T}\hat{x}$.<br>

Because MMSE estimator is a function of a quadratic functional shape that is convex downward, we can get the minimum value when $\frac{dJ}{d\hat{x}} = 0$.

Therefore, $\frac{dJ}{d\hat{x}} = -2( E[X\mid Z_{k}=z_{k}] + \hat{x})$. Note that $\frac{d\hat{x}}{d\hat{x}} = \frac{d\hat{x}^{T}}{d\hat{x}}$

<center>

$\therefore \hat{x}^{MMSE} = E[x \mid Z_{k}=z_{k}]$
$= \int_{-\infty}^{\infty}xp_{X \mid Z_{k}}(x \mid z_{k})dx$
$= \frac{\int_{-\infty}^{\infty}xp_{Z_{k} \mid X}(z_{k} \mid x)p_{X}(x)dx}{\int_{-\infty}^{\infty}p_{Z_{k} \mid X}(z_{k} \mid x)p_{X}(x)dx}$
</center>

Same as formula above, 