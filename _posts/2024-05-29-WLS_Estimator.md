---
title: WLS Estimator
author: SeHoon
date: 2024-05-22 09:04:00 +0900
categories: [Mathematics, Estimator]
tags: [Mathematics, Statistics, Kalman Filter, Estimator]
math: true
mermaid: true
---

# WLS(Weighted Least-Squares) Estimator

A Least-Squares(LS) estimator is defined as follows when the measurement equation is given as $Z(k)=h(x,k(+V(k)))$ and a measurement vectors are given by $z_{k}=\{z(0),z(1), \ldots,z(k)\}$.

<center>

$J(k) = \sum_{n=0}^{k}(z(n)-h(\hat{x}^{LS},n))^{T}(z(n)-h(\hat{x}^{LS},n))$
</center>

Since the LS estimator minimizes the sum of squared errors, it can be considered a non-Bayesian version of the [MMSE estimator](https://csh970605.github.io/posts/MMSE_Estimator/).

Additionally, the LS estimator does not make any assumptions about the probabilistic characteristics of the measurement noise. Thus, measurement noise is not treated as a [random vector](https://csh970605.github.io/posts/Rand_Vector/); rather, it is considered an arbitrary deterministic value.

The Weighted Least-Squares (WLS) estimator is then defined as an estimator that minimizes the weighted sum of squared errors, as follows when the measurement equation is given by $Z(k)=H(k)x+V(k)$ and the measurement vector is given as $z_{k}= \{ z(0), z(1), \ldots, z(k) \}$.

<center>

$J(k) = \sum_{n=0}^{k}(z(n)-H(n)\hat{x}^{WLS})^{T}R^{-1}(n)(z(n)-H(n)\hat{x}^{WLS})$
</center>

where $R(n)$ is a weighted matrix.<br>
 

Then, differentiate $J(k)$ with $\hat{x}^{WLS}$ to get the minimum value of $J(k)$.

<center>

$\frac{dJ(k)}{d\hat{x}^{WLS}} = -2(H^{k})^{T}(R^{k})^{-1}(z^{k}-H^{k}\hat{x}^{WLS}) = 0$<br>

$\therefore \hat{x}^{WLS}(k)=((H^{k})^{T}(R^{k})^{-1}H^{k})^{-1}(H^{k})^{T}(R^{k})^{-1}z^{k}$
</center>

Here, the measurement error $\tilde{X}$ and the covariance of the estimation error $P_{\tilde{X}\tilde{X}}$ are given as:

<center>

$\tilde{X}(k) = x - \hat{X}^{WLS}(k) = -((H^{k})^{T}(R^{k})^{-1}H^{k})^{-1}(H^{k})^{T}(R^{k})^{-1}V^{k}$<br>

$P_{\tilde{X}\tilde{X}}(k) = \mathbb{E}[\tilde{X}(k)\tilde{X}^{T}(k)] = ((H^{k})^{T}(R^{k})^{-1}H^{k})^{-1}(H^{k})^{T}(R^{k})^{-1}\mathbb{E}[V^{k}(V^{k})^{T}](R^{k})^{-1}H^{k}((H^{k})^{T}(R^{k})^{-1}H^{k})^{-1}$
</center>
<br>

If $\mathbb{E}[V^{T}(l)]=R(k)\delta_{kl}$, $P_{\tilde{X}\tilde{X}}(k)$ simplifies to:

<center>

$P_{\tilde{X}\tilde{X}}(k) =((H^{k})^{T}(R^{k})^{-1}H^{k})^{-1}$
</center>

This type of estimator is called a batch WLS estimator. If a new measurement $z(k+1)$ is given, it should gather the measurements from $z(0)$ to $z(k+1)$ to form $z^{k+1}$, then update the corresponding $H^{k+1}$ and $R^{k+1}$, and finally, recalculate $\hat{x}^{WLS}(k+1)$.

<br><br><br><br>

# Recursive WLS Estimator

To address the disadvantage of recalculating $\hat{x}^{WLS}(k+1)$ in a batch WLS estimator, a recursive WLS estimator that updates the existing estimate has been introduced.To transform a batch WLS estimator into a recursive WLS estimator, the parameters used in the WLS estimator are represented as:

<center>

$z^{k+1} = \begin{bmatrix}
z^{k} \\
z(k+1)
\end{bmatrix}$<br>

$H^{k+1}=\begin{bmatrix}
H^{k} \\
H(k+1)
\end{bmatrix}$<br>

$v^{k+1}=\begin{bmatrix}
v^{k} \\
v(k+1)
\end{bmatrix}$<br>

$R^{k+1}=\begin{bmatrix}
R^{k} && 0 \\
0 && R(k+1)
\end{bmatrix}$<br>
</center>

Next, $P_{\tilde{X}\tilde{X}}^{-1}$ is calculated as:

<center>

$P_{\tilde{X}\tilde{X}}^{-1}(k+1)=(H^{k+1})^{T}(R^{k+1})^{-1}H^{k+1}$<br>

$=((H^{k})^{T}H^{T}(k+1))\begin{bmatrix}
R^{k} && 0 \\
0 && R(k+1)
\end{bmatrix}$<br>

$=(H^{k})^{T}(R^{k})^{-1}H^{k} + H^{T}(k+1)R^{-1}(k+1)H(k+1)$<br>

$=P_{\tilde{X}\tilde{X}}^{-1}(k)+H^{T}(k+1)R^{-1}(k+1)H(k+1)$<br>

$\therefore P_{\tilde{X}\tilde{X}}(k+1)=(P_{\tilde{X}\tilde{X}}(k)+H^{T}(k+1)R^{-1}(k+1)H(k+1))^{-1}$<br>

$=P_{\tilde{X}\tilde{X}}(k)-P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)(H(k+1)P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)+R(k+1))^{-1}H(k+1)P_{\tilde{X}\tilde{X}}(k)$<br>

$=P_{\tilde{X}\tilde{X}}(k)-K(k+1)H(k+1)+R(k+1)$<br>

$=P_{\tilde{X}\tilde{X}}(k)-K(k+1)S(k+1)K^{T}(k+1)$
</center>

where 

+ $S(k+1) = H(k+1)P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)+R(k+1)$

+ $K(k+1) = P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)S^{-1}(k+1)$

To express $P_{\tilde{X}\tilde{X}}$ in terms of $K$, multiply both sides by $H^{T}(k+1)R^{-1}(k+1)$.

<center>

$P_{\tilde{X}\tilde{X}}(k+1)H^{T}(k+1)R^{-1}(k+1)=P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)R^{-1}(k+1)-P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)(H(k+1)P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)+R(k+1))^{-1}H(k+1)P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)R^{-1}(k+1)$<br>

$=P_{\tilde{X}\tilde{X}}(k)H^{T}(k+1)S^{-1}(k+1)$<br>

$=K(k+1)$
</center>

The updated estimate $\hat{x}^{WLS}(k+1)$ is then calculated as:

<center>

$\hat{x}^{WLS}(k+1)=((H^{k+1})^{T}(R^{k+1})^{-1}H^{k+1})^{-1}(H^{k+1})^{T}(R^{k+1})^{-1}z^{k_+1}$<br>

$=P_{\tilde{X}\tilde{X}}(k+1)(H^{k+1})^{T}(R^{k+1})^{-1}z^{k+1}$

$=P_{\tilde{X}\tilde{X}}(k+1)((H^{k})^{T}H^{T}(k+1))\begin{bmatrix}
R^{k} && 0 \\
0 && R(k+1)
\end{bmatrix}^{-1}\begin{bmatrix}
z^{k} \\
z(k+1)
\end{bmatrix}$<br>

$=P_{\tilde{X}\tilde{X}}(k+1)(H^{k})^{T}(R^{k})^{-1}z^{k} + P_{\tilde{X}\tilde{X}}(k+1)H^{T}(k+1)R^{-1}(k+1)z(k+1)$<br>

$=(I-K(k+1)H(k+1))P_{\tilde{X}\tilde{X}}(k)(H^{k})^{T}(R^{k})^{-1}z^{k} + K(k+1)z(k+1)$<br>

$=(I-K(k+1)H(k+1))\hat{x}^{WLS}(k)+K(k+1)z(k+1)$<br>

$=\hat{x}^{WLS}(k) + K(k+1)(z(k+1)-H(k+1)\hat{x}^{WLS}(k))$
</center>
