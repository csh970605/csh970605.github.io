---
title: Random Vector
author: SeHoon
date: 2024-05-13 10:02:30 +0900
categories: [Mathmatics, Statistics]
tags: [Mathmatics, Statistics, Kalman Filter]
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
    <span>$P(X \leq x \bar Y = y)= \int_{-\infty}^{\infty}p_{X \mid Y}(x \mid y)dx$</span>
    <span style="float: right;">[4]</span>
</p>