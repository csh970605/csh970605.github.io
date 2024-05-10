---
title: Expected Value and Variance
author: SeHoon
date: 2024-05-10 08:02:30 +0900
categories: [Mathmatics, Statistics]
tags: [Mathmatics, Statistics, Kalman Filter]
math: true
mermaid: true
---

# Expected Value

The expectation or mean of [random variable](https://csh970605.github.io/posts/Probability_RandomVector/#random-variable) $X$ $E[X]$ is defined as formula [1].

<p align="center">
    <span>$E[X] = \int_{-\infty}^{\infty}xp_{X}(x)dx$</span>
    <span style="float: right;">[1]</span>
</p>

And the $k^{th}$ moment of random varialbe X $E[X]$ is defined as formula [2].

<p align="center">
    <span>$E[X^{k}] = \int_{-\infty}^{\infty}x^{k}p_{X}(x)dx$</span>
    <span style="float: right;">[2]</span>
</p>

Where the first moment is expectation and second moment is mean square or average power of random variable.<br>

And the function of random variable $X$ $g(X)$ is defined as formula [3].

<p align="center">
    <span>$E[g()] = \int_{-\infty}^{\infty}g(x)p_{X}(x)dx$</span>
    <span style="float: right;">[3]</span>
</p>

if random variable $X$ has a joint distribution with $Y$, the expectation of function of random variable $X$ $E[g(X)]$ is defined as formula [4].

<center>

$E[g()] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}g(x)p_{XY}(x,y)dxdy$

<p align="center">
    <span>$= \int_{-\infty}^{\infty}x^{k}p_{X}(x)dx$</span>
    <span style="float: right;">[4]</span>
</p>
</center>

The expectaion of function of random variable $X$ and $Y$ $g(X, Y)$ is defined as formula [5].

<p align="center">
    <span>$E[g(X, Y)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}g(x, y)p_{XY}(x,y)dxdy$</span>
    <span style="float: right;">[4]</span>
</p>

<br><br><br><br>

# Variance