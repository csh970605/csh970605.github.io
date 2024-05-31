---
title: Random Vector
author: SeHoon
date: 2024-05-13 10:02:30 +0900
categories: [Mathematics, Statistics]
tags: [Mathematics, Statistics, Kalman Filter]
math: true
mermaid: true
---

# Random Vector

A random vector is a vector consisting of random variables. When the element consist the vecotr $X$ is $X_{1}, X_{2}, ..., X{n}$, the probability distribution function is defined as formula [1].

<p align="center">
    <span>$F_{X_{1},...,X_{n}}(x_{1}, ..., x_{n}) = P (X_{1} \leq x_{1}, ..., X_{n} \leq x_{n})$</span>
    <span style="float: right;">[1]</span>
</p>

And the joint probability distribution function is written as formula [2].

<p align="center">
    <span>$F_{X}(x) = F_{X_{1},...,X_{n}}(x_{1}, ..., x_{n})$</span>
    <span style="float: right;">[2]</span>
</p>

where
<center>

$X = \begin{bmatrix}
X_{1}\\ 
X_{2}\\
\vdots \\
X_{n}
\end{bmatrix},x = \begin{bmatrix}
x_{1}\\ 
x_{2}\\
\vdots \\
x_{n}
\end{bmatrix}$
</center>

The probability density function of random vector $X$ $p_{X}(x) $ is defined as the joint probablity density function of random variable as formula [3].

<center>

$F_{X}(x) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}...\int_{-\infty}^{\infty}p_{X_{1}}, ..., p_{X_{n}}(x_{1}, ..., x_{n})dx_{1}...dx_{n}$

<p align="center">
    <span>$= \int_{-\infty}^{\infty}p_{X}(x)dx$</span>
    <span style="float: right;">[3]</span>
</p>

</center>

Where $p_{X}(x)$ is a multivariate function that is $p_{X}(x) = p_{X_{1}}, ..., p_{X_{n}}(x_{1}, ..., x_{n})$

And the conditional probability density function of random vector $X$ that is given random vector $Y$ is $Y=y$ is defined as formula [4].

<p align="center">
    <span>$P(X \leq x \mid Y = y)= \int_{-\infty}^{\infty}p_{X \mid Y}(x \mid y)dx$</span>
    <span style="float: right;">[4]</span>
</p>

where

<center>

$(X \leq x) = (X_{1} \leq x_{1}, X_{2} \leq x_{2}, ..., X_{n} \leq x_{n})$

$(Y \leq t) = (Y_{1} \leq y_{1}, Y_{2} \leq y_{2}, ..., Y_{n} \leq y_{n})$

$p_{X \mid Y}(x \mid y) = p_{X_{1}, ..., X_{n} \mid Y_{1}, ..., Y_{m}}(x_{1}, ..., x_{n} \mid y_{1}, ..., y_{m})$

$ = \frac{p_{XY}(x,y)}{p_{Y}(y)} = \frac{p_{X_{1}, ..., X_{n} \mid Y_{1}, ..., Y_{m}}(x_{1}, ..., x_{n} \mid y_{1}, ..., y_{m})}{p_{Y_{1}, ..., Y_{m}}(x_{1}, ..., x_{n} \mid y_{1}, ..., y_{m})}$

</center>

And $P_{X \mid Y}(x \mid y)$ is a multi variable function.

<br><br><br><br>


# Expectation and Covariance

<br><br>

## Expectation

The Expectation or mean of random vector $X=[X_{1}, X_{2}, ..., X_{n}]^{T}$ is defined as the expectation of each random vector element as formula [5].

<center>

$\mathbb{E}[X] = \begin{bmatrix}
\mathbb{E}[X_{1}]\\ 
\vdots \\
\mathbb{E}[X_{n}]
\end{bmatrix} = \int_{-\infty}^{\infty}\begin{bmatrix}
x_{1}\\ 
\vdots \\
x_{n}
\end{bmatrix}p_{X}(x)dx$

<p align="center">
    <span>$=\int_{-\infty}^{\infty}xp_{X}(x)dx$</span>
    <span style="float: right;">[5]</span>
</p>

</center>

where $x = [x_{1}, x_{2}, ..., x_{n}]^{T}$.<br>

The expectation of function $g(X)$ of random vector $X$ is defined as:

<center>

$\mathbb{E}[g(X)] = \int_{-\infty}^{\infty}g(x)p_{X}(x)dx$
</center>
<br><br>

## Covariance

The covariance matrix $Cov(X)$ of random vector $X=[X_{1}, X_{2}, ..., X_{n}]^{T}$ is defined as symmetric matrix as formula [6].

<center>

$Cov(X) = \mathbb{E}[(X-\mathbb{E}[X])(X-\mathbb{E}[X])^{T}]$

$= \int_{-\infty}^{\infty}(x-\mathbb{E}[X])(X-\mathbb{E}[X])^{T}p_{X}(x)dx$

<p align="center">
    <span>$\begin{bmatrix}
 \sigma_{11}&  \sigma_{12}& \cdots & \sigma_{1n}\\ 
 \sigma_{21}&  \sigma_{22}& \cdots & \sigma_{2n}\\ 
 \vdots & \vdots & \ddots & \vdots \\ 
 \sigma_{n1}&  \sigma_{n2}& \cdots & \sigma_{nn}
\end{bmatrix}$</span>
    <span style="float: right;">[6]</span>
</p>
</center>

Where $\sigma_{ij} = \sigma_{ji} = \mathbb{E}[(X_{i} - \mathbb{E}[X_{i}])(X_{j}-\mathbb{E}[X_{j}])]$.

And the correlation matrix of random vector $X$ and $Y$ is defined as:

<center>

$\mathbb{E}[XY^{T}] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} xy^{T}p_{XY}(x,y)dxdy$
</center>

And the inter-covariance matrix of random vector $X$ and $Y$ is defined as:

<center>

$\mathbb{E}[(X-\mathbb{E}[X])(Y-\mathbb{E}[Y])^{T}] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}(x-\mathbb{E}[X])(y-\mathbb{E}[Y])^{T}p_{XY}(x,y)dxdy$
</center>

If the inter-covariance matrix of $X$ and $Y$ is 0, $X$ and $Y$ are in the **uncorrelated** to each other.<br>
If $\mathbb{E}[X^{T}Y]=0$, $X$ and $Y$ are **orthogonal** to each other.<br>

If $p_{XY}(x,y)=p_{X}(x)p_{Y}(y)$, $X$ and $Y$ are independent.

The conditional expectation of $X$ that is given random variable $Y$ as $y$ is defined as formula [7].

<p align="center">
    <span>$\mathbb{E}[X \mid Y = y] = \int_{-\infty}^{\infty}xp_{X \mid Y}(x \mid y) dx$</span>
    <span style="float: right;">[7]</span>
</p>

And conditional expectation of $X$ that is conditioning the random variable $Y$ is defined as formula [8].

<p align="center">
    <span>$\mathbb{E}[X \mid Y] = \int_{-\infty}^{\infty}xp_{X \mid Y}(x \mid Y) dx$</span>
    <span style="float: right;">[8]</span>
</p>

<span style="color: red;">**Note that $\mathbb{E}[X \mid Y=y]$ is a real number as a function of real number $y$, but $\mathbb{E}[X \mid Y]$ is a random variable as a function of random variable $Y$.**</span>

The conditional covariance matrix of $X$ that is given random variable $Y$ as $y$ and the conditional covariance matrix of $X$ That is conditioning the random variable $Y$ are defined as fromula [9], [10] respectively.

<p align="center">
    <span>$Cov[X \mid Y=y] = \mathbb{E}[(X - \mathbb{E}[X \mid Y=y])(X - \mathbb{E}[X \mid Y=y])^{T} \mid Y=y]$</span>
    <span style="float: right;">[9]</span>
</p>

<p align="center">
    <span>$Cov[X \mid Y] = \mathbb{E}[(X - \mathbb{E}[X \mid Y])(X - \mathbb{E} [X \mid Y])^{T} \mid Y]$</span>
    <span style="float: right;">[10]</span>
</p>

<br><br><br><br>

# Characteristic function

The characteristic function of random vector $X$ is defined as formula [11].

<p align="center">
    <span>$\Phi_{X}(\omega) = \mathbb{E}[e^{j\omega^{T}X}]$</span>
    <span style="float: right;">[11]</span>
</p>

where $\omega =[\omega_{1}, \omega_{2}, ..., \omega_{n}]^{T}$ is a $n$-dimensional real number vector, $n$ is the dimension of $X$.<br>
According to the definition of expectation, formula [11] can be written as formula [12].

<p align="center">
    <span>$\Phi_{X}(\omega) = \int_{-\infty}^{\infty}e^{j\omega^{T}X}p_{X}(x)dx$</span>
    <span style="float: right;">[12]</span>
</p>

As you can see at the formula [12], the characteristic function of random vector $X$ is the multi-dimensional inverse Fourier transform of probability density function. Thus, the probability of $X$ can be get by transforming the characteristic function as:

<center>

$p_{X}(x) = \frac{1}{(2\pi)^{n}} \int_{-\infty}^{\infty}\Phi_{X}(\omega)e^{-j\omega^{T}X}d\omega$
</center>