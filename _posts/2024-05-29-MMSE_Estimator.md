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

## The Performance of The MMSE Estimator

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

Then, let $g^{T}(Z) = Z$, $\mathbb{E}[X-\hat{X}^{MMSE}Z^{T}] = 0$.<br>


According to the equation above,$\hat{X}_{i}^{MMSE}$ is given as the value of projecting $X_{i}$ into a span consisting of a linear combination of measurement variables $Z_{i}$ and the measurement error is orthogonal to this span.

<br><br>

## Joint Gaussian MMSE Estimator

Let's get the MMSE estimation value $\hat{X}^{MMSE}$ of random vector $X$ when the two random vectors $X$ and $Z$ have a [joint Gaussian distribution](https://csh970605.github.io/posts/Gaussian_Distribution/#joint-gaussian-random-vector). <br>
If the two random vectors are joint Gaussian vectors, each random vector follows a Gaussian distribution. Let $X$ and $Z$ have the following [probability density functions](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function):

<center>

$X \sim N(\mu_{X}, P_{XX}),$<br>

$Z \sim N(\mu_{Z}, P_{ZZ})$
</center>

Also, assume that the [joint probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#joint-probability-function) of two random vectors is given as:

<center>

$Y = \begin{bmatrix}
X \\
Z
\end{bmatrix} \sim N(\mu_{Y}, P_{YY})$
</center>

Then, $\mu_{Y}$ and $P_{YY}$ are:

<center>

$\mu_{Y}= \begin{bmatrix}
\mu_{X} \\
\mu_{Z}
\end{bmatrix}, P_{YY} = \begin{bmatrix}
P_{XX} & P_{XZ} \\
P_{ZX} & P_{ZZ}
\end{bmatrix}$
</center>

where $P$ represents the covariance matrix.<br>

To obtain $\hat{X}^{MMSE}$, we need the [conditional probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#conditional-probability) of $X$ given $Z = z$. The conditional probability density function $p_{X\mid Z}(x \mid z)$ is given as:

<center>

$p_{X \mid Z}(x \mid z) = \frac{p_{XZ}(x, z)}{p_{Z}(z)} = \frac{p_{Y}(y)}{p_{Z}(z)}$<br>

$= \frac{\sqrt{(2 \pi)^{p}\det{P_{ZZ}}}}{\sqrt{(2 \pi)^{n+p}\det{P_{YY}}}}\exp({-\frac{1}{2}\begin{Bmatrix}
(y-\mu_{Y})^{T}P^{-1}_{YY}(y-\mu_{Y}) \\
-(z-\mu_{Z})^{T}P^{-1}_{ZZ}(z-\mu_{Z})
\end{Bmatrix}})$<br>

$= \frac{1}{\sqrt{(2 \pi)^{n}\det{P_{XX\mid Z}}}} \exp{(-\frac{1}{2}(x-E[X \mid Z=z])^{T}P_{XX \mid Z} ^{-1}(x-E[X \mid Z=z]))}$
</center>

where

+ $E[X \mid Z=z]$ : $\mu_{X} + P_{XZ}P_{ZZ}^{-1}(z-\mu_{Z})$<br>

+ $P_{XX \mid Z}$ : $P_{XX} - P_{XZ} P_{ZZ}^{-1} P_{ZX}$

Thus, the MMSE estimation value $\hat{X}^{MMSE}$ and the estimation error covariance $P_{\tilde{X}\tilde{X}}$ are:

<center>

$\hat{X}^{MMSE}(z) = \mu_{X} + P_{XZ}P_{ZZ}^{-1}(z-\mu_{Z})$<br>

$P_{\tilde{X}\tilde{X}} = P_{XX \mid Z} = P_{XX}-P_{XZ}P_{ZZ}^{-1}P_{ZX}$
</center>

<br><br>

## Joint Gaussian MMSE Estimator for Linear Measurements

Let an unknown random vector $X$ and a measurement vector $Z$ have a linear relationship as:

<center>

$Z = HX + V$
</center>

where $X$ and $V$ which is a measurement noise are given as [Gaussian random vectors](https://csh970605.github.io/posts/Gaussian_Distribution/#gaussian-random-vector) as:

<center>

$X \sim N(\mu_{X}, P_{XX}),$<br>
$V \sim N(0, R),$<br>
$\mathbb{E}[(X-\mu_{X})V^{T}]=0$
</center>
and assume that the two random vectors are uncorrelated.<br>

Since $X$ and $V$ are uncorrelated Gaussian random vectors, and $X$ and $Z$ have a linear relationship, $X$ and $Z$ have [joint Gaussian distribution](https://csh970605.github.io/posts/Gaussian_Distribution/#joint-gaussian-random-vector). Thus, the estimation value $\hat{X}^{MMSE}$ and the estimation error covariance $P_{\tilde{X}\tilde{X}}$ of the random vector $X$ conditioned on the random vector $Z$ are:

<center>

$\hat{X}^{MMSE}(z) = \mu_{X}+P_{XX}H^{T}(HP_{XX}H^{T} + R)^{-1}(z-H\mu_{X})$<br>

$P_{\tilde{X}\tilde{X}} = (P_{XX}^{-1} + H^{T}R^{-1}H)^{-1}$
</center>

To prove this, we need to get $\mu_{Z}$ first.
<center>

$\mu_{Z} = \mathbb{E}[Z] = \mathbb{E}[HX + V] = H\mathbb{E}[X] = H\mu_{X}$
</center>

Second, get $P_{ZZ}$.
<center>

$P_{ZZ} = \mathbb{E}[(Z-\mu_{Z})(Z-\mu_{Z})^{T}]$<br>

$= \mathbb{E}[(H(X-\mu_{X})+V)(H(X-\mu_{X})+V)^{T}]$<br>

$= HP_{XX}H^{T} + \mathbb{E}[H(X-\mu_{X})V^{T}]+\mathbb{E}[V(X-\mu_{X})^{T}H^{T}]+ R$<br>

$=HP_{XX}H^{T}+R$
</center>

Third, get the cross-covariance $P_{XZ}$.
<center>

$P_{XZ} = \mathbb{E}[(X-\mu_{X})(Z-\mu_{Z})]$<br>

$= \mathbb{E}[(X-\mu_{X})(H(X-\mu_{X})+V)^{T}]$<br>

$= P_{XX}H^{T} + \mathbb{E}[(X-\mu_{X})V^{T}]$<br>

$= P_{XX}H^{T}$
</center>

Finally, to get $\hat{X}^{MMSE}(z)$ and $P_{\tilde{X}\tilde{X}}$, use the equations of joint Gaussian MMSE estimator above.

<center>

$\hat{X}^{MMSE}(z) = \mu_{X}+P_{XX}H^{T}(HP_{XX}H^{T} + R)^{-1}(z-H\mu_{X})$<br>

$P_{\tilde{X}\tilde{X}} = P_{XX\mid Z}$ <br>

$= P_{XX}-P_{XX}H^{T}(HP_{XX}H^{T}+R)^{-1}HP_{XX}$<br>

$(P_{XX}^{-1} + H^{T}R^{-1}H)^{-1}$
</center>