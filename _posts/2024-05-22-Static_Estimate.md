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

A static estimation estimates the constant parameters which don't change over time. On the contrary, a dynamic estimation estimates the [state variables](https://csh970605.github.io/posts/Kalman_Filter/#state-variables) which change over time.

Then, let's see what the static estimation is.<br>

Let there be two unknown vectors, a constant vector $X \in \mathbb{R}^{n}$ and a measurement vector $Z \in \mathbb{R}^{p}$. Since these two vectors are related to each other, if you measure $Z$, you can obtain information about $X$. And it can be expressed as a general non-linear equation, additional measurement noise and linear eqaultion as follows respectively.:

<center>

$Z = h(X, V)$

$Z = h(X) + V$

$Z = HX + V$
</center>

where $V$ is a [random vector](https://csh970605.github.io/posts/Rand_Vector/#random-vector) of sensor measurement noise and $H \in \mathbb{R}^{p \times n}$. 
Since $V$ is a random vector, Z is a random vector also.

For example, think about a simple system that estimates the 2D location of something with radar. Assume that the object is fixed at $(x, y)$ and radar can estimate the distance $R$ and azimuth $\Psi$. Then, $R$ and $\Psi$ are given as follows respectively:

<center>

$R = \sqrt{x^{2} + y^{2}}$

$\Psi = tan ^{-1}(\frac{y}{x})$
</center>

Since there are measurement noises always, the values of $R$ and $\Psi$ that radar estimates are mixed with noises. So, the measurement equations are :

<center>

$Z_{1} = R + V_{r} = \sqrt{x^{2} + y^{2}} + V_{r}$

$Z_{2} = \Psi + V_{\Psi} = tan^{-1}(\frac{y}{x}) + V_{\Psi}$
</center>

where $V_{r}$ and $V_{\Psi}$ are the measurement noises of distance and azimuth respectively.<br>

Making those formulas as vector:

<center>

$Z = \begin{bmatrix}
Z_{1} \\
Z_{2}
\end{bmatrix} = h([x \ y]^{T})+V$

$= \begin{bmatrix}
\sqrt{x^{2} + y^{2}} \\
tan^{-1}(\frac{1}{2})
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

Since measurements are measured independently, the measurement noises are independent or uncorrelated to time.<br>

The combination of measurement vectors that collect all random measurement vectors from $k=0$ to $k$ is expressed as follows:

<center>

$Z_{k} = \{Z(0), Z(1), ..., Z(k) \}$
</center><br>

And the combination of the measured values of random measurement vectors are expressed as follows:

<center>

$z_{k} = \{z(0), z(1), ..., z(k) \}$

</center>

where <center>

$Z_{k} = z_{k}:\{Z(0)=z(0), Z(1) = z(1), ..., Z(k) = z(k) \}$
</center><br><br>

## Static Estimation Problem

A static estimation problem is a problem that designs a estimator of a constant vectors which as a function of a combination of measurement vectors $z_{k}$ as follows:

<center>

$\hat{x}(k) = g(z_{k})$
</center>
<br>

If the measurement vectors are given as $Z_{k}=z_{k}$, the estimation values are deterministcic values, however if the measurement vectors are given as random vectors, the estimation values are random vectors also as follows:

<center>

$\hat{X}(k) = g(Z_{k})$
</center>
<br>

Depending on what unkown nature X is defined, the estimator is divided into two methods:

+ Bayesian approach

+ non-Bayesian approach

<br><br>

### Bayesian Approach

In a bayesian approach, $X$ is a random vector. Therefore, assume that we know a priori probability information of $X$.<br>

A measurement vector $Z$ reinforce the probability information of $X$ more precisely.<br>

[MAP estimator](https://csh970605.github.io/posts/MAP_Estimator) and [MMSE estimator](https://csh970605.github.io/posts/MMSE_Estimator) are a bayesian approach estimator.
<br><br>

### non-Bayesian Approach

In a non-bayesian approach, $X$ is a unknown deterministic value. Therefore, asume that there is no a priori probability information, and the information of $X$ can only be obatined by a measurement vector $Z$.

[ML estimator](https://csh970605.github.io/posts/ML_Estimator) and [WLS estimator](https://csh970605.github.io/posts/WLS_Estimator) are a bayesian approach estimator.



