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

When a set of measurement vectors is given as $Z_{k} = z_{k}$, the MMSE estimator is defined as an estimator that minimizes the conditional average estimation error or conditional mean-square error as follows:

<center>

$J = \mathbb{E}[(X-\hat{x})^{T}(X-\hat{x}) \mid Z_{k} = z_{k}]$<br>
$= \int_{-\infty}^{\infty}(x-g(z_{k}))^{T}(x-g(z_{k}))p_{X \mid Z_{k}}(x\mid z_{k})dx$
</center>
<br>

To simplify, the MMSE is expressed as follows:

<center>

$\hat{x}^{MMSE} = \arg\min(\mathbb{E}[(X-\hat{x})^{T}(X-\hat{x}) \mid Z_{k} = z_{k}])$
</center>
<br>

Since $\hat{x} = g(z_{k})$ is a constant value, $J = \mathbb{E}[X^{T}x-X^{T}\hat{x} - \hat{x}^{T}X + \hat{x}^{T}\hat{x} \mid Z_{k} = z_{k}] \ = \mathbb{E}[X^{T}X \mid Z_{k} = z_{k}] - 2\hat{x}^{T}\mathbb{E}[X \mid Z_{k}=z_{k}]+\hat{x}^{T}\hat{x}$.<br>

Because the MMSE estimator is a function of a quadratic functional shape that is convex downward, we can get the minimum value when $\frac{dJ}{d\hat{x}} = 0$.

Therefore, $\frac{dJ}{d\hat{x}} = -2( \mathbb{E}[X\mid Z_{k}=z_{k}] + \hat{x})$. Note that $\frac{d\hat{x}}{d\hat{x}} = \frac{d\hat{x}^{T}}{d\hat{x}}$

<center>

$\therefore \hat{x}^{MMSE} = \mathbb{E}[x \mid Z_{k}=z_{k}]$
$= \int_{-\infty}^{\infty}xp_{X \mid Z_{k}}(x \mid z_{k})dx$
$= \frac{\int_{-\infty}^{\infty}xp_{Z_{k} \mid X}(z_{k} \mid x)p_{X}(x)dx}{\int_{-\infty}^{\infty}p_{Z_{k} \mid X}(z_{k} \mid x)p_{X}(x)dx}$
</center>

Similar to the formula above, if the measurement vectors are random vectors, the MMSE estimator is estimated as follows and the value will also be a random vector.

<center>

$\hat{X}^{MMSE} = \mathbb{E}[X \mid Z_{k}]$
</center>
<br><br>

## Check The Performance of The MMSE Estimator

<br><br>

### Mean of The MMSE Estimator

The estimation error $\tilde{X}$ is defined as follows:

<center>

$\tilde{X} = X - \hat{X}^{MMSE}$
</center>
<br>

Then, the average of $\tilde{X}$ is:

<center>

$\mathbb{E}[\tilde{X}] = \mathbb{E}[X-\hat{X}^{MMSE}]$<br>

$= \mathbb{E}[X] - \mathbb{E}[\mathbb{E}[X \mid Z_{k}]]$<br>

$= \mathbb{E}[X] - \mathbb{E}[X] = 0$
</center>

Because the mean of $\tilde{X}$ is 0, the expectation value of the estimation value of the MMSE equals the expectation value of the unknown random vector $X$. That is, the MMSE estimator is an unbiased estimator.

<br><br>

### [Covariance](https://csh970605.github.io/posts/Rand_Vector/#covariance) of The Estimation Error

The covariance of the estimation error $\tilde{X}$ is given as the mean of the conditional covariance of $X$ conditioned on the set of measurement vectors $Z_{k}$, as follows:

<center>

$P_{\tilde{X}\tilde{X}} = \mathbb{E}[(\tilde{X}-\mathbb{E}[\tilde{X}])(\tilde{X}-\mathbb{E}[\tilde{X}])^{T}]$<br>

$=\mathbb{E}[\tilde{X}\tilde{X}^{T}]$<br>

$=\mathbb{E}[\mathbb{E}[\tilde{X}\tilde{X}^{T} \mid Z_{k}]]$<br>

$=\mathbb{E}[P_{XX\mid Z_{k}}]$
</center>
<br>

If the measurement vector is given as $Z_{k} = z_{k}$, the covariance of the estimation error $\tilde{X}$ is as follows:

<center>

$P_{\tilde{X}\tilde{X}} = \mathbb{E}[\tilde{X}\tilde{X}^{T}]$<br>

$= \mathbb{E}[(X-\mathbb{E}[X \mid Z_{k}=z_{k}])(X-\mathbb{E}[X \mid Z_{k}=z_{k}])^{T}]$<br>

$=P_{XX \mid Z_{k}}$
</center>

Also, the estimation error is always orthogonal with $g_{j}$ which is composed by measurement variable. It is written as an equation as :

<center>

$\mathbb{E}[X - \hat{X}^{MMSE}g^{T}(Z)] = 0$
</center>

where $Z$ is a measurement vector.

To prove this, 
<center>

$\mathbb{E}[(x - \hat{X}^{MMSE}g^{T}(Z))] = \mathbb{E}[Xg^{T}(Z)]-\mathbb{E}[\mathbb{E}[X \mid Z]g^{T}(Z)]$<br>

$=\mathbb{E}[Xg^{T}(Z)]-\mathbb{E}[\mathbb{E}[Xg^{T}(Z) \mid Z]]$<br>

$= \mathbb{E}[Xg^{T}(Z)] - \mathbb{E}[Xg^{T}(Z)] = 0$
</center>

Then, let $g^{T}(Z) = Z$, $\mathbb{E}[X-\hat{X}^{MMSE}Z^{T}] = 0$.

According to the equation above, $\hat{X}^{MMSE}_{i}$ is given as the value of projecting $X_{i}$ into a span consisting of a linear combination of measurement variables $Z_{i}$ and the measurement error is orthogonal to this span.