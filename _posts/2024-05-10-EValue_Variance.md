---
title: Expected Value and Variance
author: SeHoon
date: 2024-05-10 08:02:30 +0900
categories: [Mathematics, Statistics]
tags: [Mathematics, Statistics, Kalman Filter]
math: true
mermaid: true
---

# Expected Value

The expectation or mean of the [random variable](https://csh970605.github.io/posts/Probability_RandomVector/#random-variable) $X$, denoted $\mathbb{E}[X]$, is defined by equation [1].

<p align="center">
    <span>$\mathbb{E}[X] = \int_{-\infty}^{\infty}xp_{X}(x)dx$</span>
    <span style="float: right;">[1]</span>
</p>

The $k^{th}$ moment of the random variable $X$, denoted $\mathbb{E}[X^k]$, is defined by equation [2].

<p align="center">
    <span>$\mathbb{E}[X^{k}] = \int_{-\infty}^{\infty}x^{k}p_{X}(x)dx$</span>
    <span style="float: right;">[2]</span>
</p>

The first moment is the expectation, and the second moment is the mean square or average power of the random variable.<br>

The expectation of a function of the random variable $X$, denoted $\mathbb{E}[g(X)]$, is defined by equation [3].

<p align="center">
    <span>$\mathbb{E}[g(X)] = \int_{-\infty}^{\infty}g(x)p_{X}(x)dx$</span>
    <span style="float: right;">[3]</span>
</p>

If the random variable $X$ has a joint distribution with $Y$, the expectation of a function of the random variable $X$, denoted $\mathbb{E}[g(X)]$, is defined by equation [4].

<center>

$\mathbb{E}[g(X)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}g(x)p_{XY}(x,y)dxdy$

<p align="center">
    <span>$= \int_{-\infty}^{\infty}x^{k}p_{X}(x)dx$</span>
    <span style="float: right;">[4]</span>
</p>
</center>

The expectation of a function of the random variables $X$ and $Y$, denoted $\mathbb{E}[g(X, Y)]$, is defined by equation [5].

<p align="center">
    <span>$\mathbb{E}[g(X, Y)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}g(x, y)p_{XY}(x,y)dxdy$</span>
    <span style="float: right;">[5]</span>
</p>

<br><br><br><br>

# Variance

The variance of a random variable is defined by equation [6].

<center>

$Var(X) = \mathbb{E}[X^{2}] - (\mathbb{E}[X])^{2}$

<p align="center">
    <span>$= \mathbb{E}[(X-\mathbb{E}[X])^{2}]$</span>
    <span style="float: right;">[6]</span>
</p>

$= \int_{-\infty}^{\infty}(x-\mathbb{E}[X])^{2}p_{X}(x)dx$

</center>

The **standard deviation**  of $X$ is defined as $\sigma_{X} = \sqrt{Var(X)}$. The $k^{th}$ central moment, denoted $\mathbb{E}[(X - \mu_{X})^{k}]$, is defined by equation [7].

<p align="center">
    <span>$\mathbb{E}[(X - \mathbb{E}[X])^{k}] = \int_{-\infty}^{\infty}(x-\mathbb{E}[X])^{k}p_{X}(x)dx$</span>
    <span style="float: right;">[7]</span>
</p>

where, $\mathbb{E}[X] = \mu_{X}$. The first central moment is 0, and the second central moment is the variance of the random variable.<br>

The covariance of two random variables $X$ and $Y$ is defined by equation [8].

<center>

$Cov(X, Y) = \mathbb{E}[(X-\mathbb{E}[X])(Y-\mathbb{E}[Y])]$

<p align="center">
    <span>$= \int_{-\infty}^{\infty}\int_{-\infty}^{\infty}(x-\mathbb{E}[X])(y-\mathbb{E}[Y])p_{XY}(x, y)dxdy$</span>
    <span style="float: right;">[8]</span>
</p>
</center>

As you can see in equation [8], if $X = Y$, $Cov(X, Y) = Var(X)$.<br>

If the covariance of random variables $X$ and $Y$ is 0, $X$ and $Y$ are said to be **uncorrelated**. The **correlation** of $X$ and $Y$ is defined by equation [9].

<center>

$Cor(X, Y) = \mathbb{E}[XY]$

<p align="center">
    <span>$= \int_{-\infty}^{\infty}\int_{-\infty}^{\infty}xyp_{XY}(x, y)dxdy$</span>
    <span style="float: right;">[9]</span>
</p>
</center>

However, if $X$ and $Y$ are independent, the correlation is expressed as:

<center>

$Cor(X, Y) = \mathbb{E}[XY] = \mathbb{E}[X] \mathbb{E}[Y]$
</center>

If $\mathbb{E}[XY] = 0$, $X$ and $Y$ are said to be **orthogonal**. 

<br><br><br><br>


# Conditional Expectation and Variance

<br><br>

## Conditional Expectaion

The conditional expectation of $X$ given random variable $Y$ as $y$ is defined by equation [10].

<p align="center">
    <span>$\mathbb{E}[X \mid Y = y] = \int_{-\infty}^{\infty}xp_{X \mid Y}(x \mid y) dx$</span>
    <span style="float: right;">[10]</span>
</p>

The conditional expectation of $X$ given the random variable $Y$ is defined by equation [11].

<p align="center">
    <span>$\mathbb{E}[X \mid Y] = \int_{-\infty}^{\infty}xp_{X \mid Y}(x \mid Y) dx$</span>
    <span style="float: right;">[11]</span>
</p>

<span style="color: red;">*Note that $\mathbb{E}[X \mid Y = y]$ is a real number as a function of the real number $y$, but $\mathbb{E}[X \mid Y]$ is a random variable as a function of the random variable $Y$.**</span>

<br><br>

The conditional expectation of $X$ given that the random variable $Y$ as $y$ and the conditional expectation of $X$ given the random variable $Y$ are defined by equations [12] and [13], respectively.

<p align="center">
    <span>$\mathbb{E}[g(X) \mid Y=y] = \int_{-\infty}^{\infty}g(x)p_{X \mid Y}(x \mid y) dx$</span>
    <span style="float: right;">[12]</span>
</p>

<p align="center">
    <span>$\mathbb{E}[g(X) \mid Y] = \int_{-\infty}^{\infty}g(x)p_{X \mid Y}(x \mid Y) dx$</span>
    <span style="float: right;">[13]</span>
</p>

Since $Var(X \mid Y)$ is also a random variable, the expectation can be calculated by equation [14].

<center>

$\mathbb{E}[Var(X \mid Y)] = \mathbb{E}[\mathbb{E}[X^{2} \mid Y] - (\mathbb{E}[X \mid Y])^{2}]$

<p align="center">
    <span>$= \mathbb{E}[X^{2}] - \mathbb{E}[(\mathbb{E}[X \mid Y])^{2}]$</span>
    <span style="float: right;">[14]</span>
</p>
</center>


<br><br>

## Conditional variance

The conditional variance of $X$ given random variable $Y$ as $y$ and the conditional variance of $X$ given the random variable $Y$ are defined by equations [15] and [16], respectively.

<center>

$Var(X \mid Y = y) = \mathbb{E}[(X-\mathbb{E}[X \mid Y=y)]^{2} \mid Y=y]$

<p align="center">
    <span>$= \mathbb{E}[X^{2} \mid Y=y] - (\mathbb{E}[X \mid Y = y])^{2}$</span>
    <span style="float: right;">[15]</span>
</p>

$Var(X \mid Y) = \mathbb{E}[(X - \mathbb{E}[X \mid Y])^{2} \mid y] $
<p align="center">
    <span>$= \mathbb{E}[X^{2} \mid Y] - (\mathbb{E}[X \mid Y])^{2}$</span>
    <span style="float: right;">[16]</span>
</p>

</center>

As with [conditional expectaion](https://csh970605.github.io/posts/EValue_Variance/#conditional-expectaion), <span style="color: red;">**note that $Var[X \mid Y = y]$ is a real number as a function of the real number $y$, but $Var[X \mid Y]$ is a random variable as a function of the random variable $Y$.**</span>

Additionally, since $\mathbb{E}(X \mid Y)$ is also a random variable, the expectation can be calculated by equation [17].

<center>

$Var(\mathbb{E}[X \mid Y]) = \mathbb{E}[(\mathbb{E}[X \mid Y] - \mathbb{E}[\mathbb{E}[X \mid Y]])^{2}]$

<p align="center">
    <span>$= \mathbb{E}[(\mathbb{E}[X \mid Y])^{2}] - (\mathbb{E}[X])^{2}$</span>
    <span style="float: right;">[17]</span>
</p>

</center>

According to the definition of [variance](https://csh970605.github.io/posts/EValue_Variance/#variance), $Var(X)$ can be expressed as follows:

<center>

$Var(X) = \mathbb{E}[Var(X \mid Y)] + Var(\mathbb{E}[X \mid Y])$
</center>

