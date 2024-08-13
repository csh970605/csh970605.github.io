---
title: Estimating The State of a Static System
author: SeHoon
date: 2024-05-22 09:02:30 +0900
categories: [Mathematics, Statistics]
tags: [Mathematics, Statistics, Kalman Filter]
math: true
mermaid: true
---

# Static Estimation

Static estimation estimates constant parameters that don't change over time. In contrast, dynamic estimation estimates   [state variables](https://csh970605.github.io/posts/Kalman_Filter/#state-variables) that change over time.

Now, let's examine what static estimation is.<br>

Let there be two unknown vectors, a constant vector $X \in \mathbb{R}^{n}$ and a measurement vector $Z \in \mathbb{R}^{p}$. Since these two vectors are related, measuring $Z$ provides information about $X$. They can be expressed as a general non-linear equation, an additional measurement noise, and a linear equation as follows, respectively:
<center>

$Z = h(X, V)$

$Z = h(X) + V$

$Z = HX + V$
</center>

where $V$ is a [random vector](https://csh970605.github.io/posts/Rand_Vector/#random-vector) of sensor measurement noise, and $H \in \mathbb{R}^{p \times n}$. Since $V$ is a random vector, $Z$ is also a random vector.

For example, consider a simple system that estimates the 2D location of an object using radar. Assume that the object is fixed at $(x, y)$ and the radar can estimate the distance $R$ and azimuth $\Psi$. Then, $R$ and $\Psi$ are given as follows, respectively:

<center>

$R = \sqrt{x^{2} + y^{2}}$

$\Psi = \tan^{-1}(\frac{y}{x})$
</center>

Since there are always measurement noises, the values of $R$ and $\Psi$ that the radar estimates are mixed with noises. Therefore, the measurement equations are:

<center>

$Z_{1} = R + V_{r} = \sqrt{x^{2} + y^{2}} + V_{r}$

$Z_{2} = \Psi + V_{\Psi} = \tan^{-1}(\frac{y}{x}) + V_{\Psi}$
</center>

where $V_{r}$ and $V_{\Psi}$ are the measurement noises of distance and azimuth respectively.<br>

Expressing these formulas as vectors:

<center>

$Z = \begin{bmatrix}
Z_{1} \\
Z_{2}
\end{bmatrix} = h([x \ y]^{T})+V$

$= \begin{bmatrix}
\sqrt{x^{2} + y^{2}} \\
tan^{-1}(\frac{y}{x})
\end{bmatrix} + \begin{bmatrix}
V_{r} \\
V_{\Psi}
\end{bmatrix}$
</center>

If the measurement is repeated several times, all the measurements are expressed as:

<center>

$Z(k) = h(X, V(k), k)$ : non-linear

$Z(k) = h(X, k) + V(k)$ : additional

$Z(k) = H(k)X + V(k)$ : linear
</center>
<br>

Where $k$ is time index.
<br>

Since measurements are taken independently, the measurement noises are independent and uncorrelated over time.<br>

The combination of measurement vectors that collect all random measurement vectors from $k=0$ to $k$ is expressed as follows:

<center>

$Z_{k} = \{Z(0), Z(1), \ldots , Z(k) \}$
</center><br>

And the combination of the measured values of random measurement vectors are expressed as follows:

<center>

$z_{k} = \{z(0), z(1), \ldots , z(k) \}$

</center>

where 

<center>

$Z_{k} = z_{k}:\{Z(0)=z(0), Z(1) = z(1), \ldots , Z(k) = z(k) \}$
</center>

<br><br>

## Static Estimation Problem

A static estimation problem is a problem that designs an estimator of constant vectors as a function of a combination of measurement vectors $z_{k}$ as follows:

<center>

$\hat{x}(k) = g(z_{k})$
</center>
<br>

If the measurement vectors are given as $Z_{k}=z_{k}$, the estimation values are deterministic; however, if the measurement vectors are given as random vectors, the estimation values are also random vectors as follows:
<center>

$\hat{X}(k) = g(Z_{k})$
</center>
<br>

Depending on the unknown nature of $X$, the estimator is divided into two methods:

+ Bayesian approach

+ non-Bayesian approach

The evaluation elements of an estimator are:

+ Bias

+ Consistency

+ Covariance of estimation errors

<br><br>

### Bayesian Approach

In a Bayesian approach, $X$ is a random vector. Therefore, assume that we know a priori probability information of $X$.<br>

A measurement vector $Z$ reinforces the probability information of $X$ more precisely.<br>

[MAP estimator](https://csh970605.github.io/posts/MAP_Estimator) and [MMSE estimator](https://csh970605.github.io/posts/MMSE_Estimator) are a Bayesian approach estimators. The basic form of Bayesian approach estimator is :

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3fc974d3-2cad-4134-959d-4cf4de672689">
</center>
<br><br>

### non-Bayesian Approach

In a non-Bayesian approach, $X$ is an unknown deterministic value. Therefore, assume that there is no a priori probability information, and the information of $X$ can only be obtained by a measurement vector $Z$.

[ML estimator](https://csh970605.github.io/posts/ML_Estimator) and [WLS estimator](https://csh970605.github.io/posts/WLS_Estimator) are non-Bayesian approach estimators. The basic form of non-Bayesian approach estimators is:

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/f5353493-76eb-4e99-bfcd-e5eba47d2f80">
</center>
<br><br><br><br>

# Bias

When an unknown constant vector $X$ is a random vector and probability information is given as a [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) $p_{X}(x)$, if there is an estimator such that $\mathbb{E}[\hat{X}] = \mathbb{E}[X]$, it is called an **unbaised estimator**. Alternatively, if the estimator is $\mathbb{E}[\hat{X}] = x$ where $X$ is an unknown constant vector which is $x$, it is also called an **unbaised estimator**.<br>
When $k \rightarrow \infty$, if $\mathbb{E}[\hat{X}] = \mathbb{E}[X]$ or $\mathbb{E}[\hat{X}] = x$ are established, it is called an **asymptotically unbiased estimator**.

<br><br><br><br>

# Consistency

When an unknown constant vector $X$ is a random vector, if there is an estimator such that $\lim_{k \rightarrow \infty}\mathbb{E}[(X-\hat{X}(k))^{T}(X-\hat{X}(k))] = 0$, it is called a **consistent estimator**. Alternatively, if the estimator is $\lim_{k \rightarrow \infty}\mathbb{E}[(x-\hat{X}(k))^{T}(x-\hat{X}(k))] = 0$ where $X$ is an unknown constant vector which is $x$, it is also called a **consistent estimator**.

<br><br><br><br>

# Covariance of Estimation Errors

Covariance of estimation errors is used to evaluate the quality of an estimator. That is, the smaller the covariance value, the better the estimate.

When an unknown constant vector $X$ is a random vector, the covariance of estimation errors of an unbiased estimator is given as:

<center>

$\mathbb{E}[(X-\hat{X})(X-\hat{X})^{T}]$
</center>

When $X$ is an unknown constant vector which is $x$, the covariance of estimation errors of an unbiased estimator is given as:

<center>

$\mathbb{E}[(x-\hat{X})(x-\hat{X})^{T}]$
</center>

<br><br><br><br>