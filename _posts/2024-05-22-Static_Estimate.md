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

