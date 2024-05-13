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

Where the first moment is expectation and the second moment is mean square or average power of random variable.<br>

And the function of random variable $X$ $g(X)$ is defined as formula [3].

<p align="center">
    <span>$E[g(X)] = \int_{-\infty}^{\infty}g(x)p_{X}(x)dx$</span>
    <span style="float: right;">[3]</span>
</p>

if random variable $X$ has a joint distribution with $Y$, the expectation of function of random variable $X$ $E[g(X)]$ is defined as formula [4].

<center>

$E[g(X)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}g(x)p_{XY}(x,y)dxdy$

<p align="center">
    <span>$= \int_{-\infty}^{\infty}x^{k}p_{X}(x)dx$</span>
    <span style="float: right;">[4]</span>
</p>
</center>

The expectaion of function of random variable $X$ and $Y$ $g(X, Y)$ is defined as formula [5].

<p align="center">
    <span>$E[g(X, Y)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}g(x, y)p_{XY}(x,y)dxdy$</span>
    <span style="float: right;">[5]</span>
</p>

<br><br><br><br>

# Variance

The variance of random variable is defined as formula [6].

<center>

$Var(X) = E[X^{2}] - (E[X])^{2}$

<p align="center">
    <span>$= E[(X-E[X])^{2}]$</span>
    <span style="float: right;">[6]</span>
</p>

$= \int_{-\infty}^{\infty}(x-E[X])^{2}p_{X}(x)dx$

The **standard deviation** of $X$ is defined as $\sigma_{X} = \sqrt{Var(X)}$. And the $k^{th}$ central moment $E[(X-\mu_{X})^{k}]$ is defined as formula [7].

<p align="center">
    <span>$E[(X - E[X])^{k}] = \int_{-\infty}^{\infty}(x-E[X])^{k}p_{X}(x)dx$</span>
    <span style="float: right;">[7]</span>
</p>

Where $E[X] = \mu_{X}$, the first central moment is 0, the second central momentom is being the variance of random variable.<br>

The covariance of two random variable $X$ and $Y$ is defined as formula [8].

<center>

$Cov(X, Y) = E[(X-E[X])(Y-E[Y])]$

<p align="center">
    <span>$= \int_{-\infty}^{\infty}\int_{-\infty}^{\infty}(x-E[X])(y-E[Y])p_{XY}(x, y)dxdy$</span>
    <span style="float: right;">[8]</span>
</p>
</center>

As you can see at the formula[8], if $X=Y$, $Cov(X,Y) = Var(X)$.<br>

If the covariance of random variable $X$ and $Y$ is 0, it is called that $X$ and $Y$ are **uncorrelated** to each other. And the **correlation** of $X$ and $Y$ is defined as formula [9].

<center>

$Cor(X, Y) = E[XY]$

<p align="center">
    <span>$= \int_{-\infty}^{\infty}\int_{-\infty}^{\infty}xyp_{XY}(x, y)dxdy$</span>
    <span style="float: right;">[9]</span>
</p>
</center>

However, $X$ and $Y$ are independent, the correlation is expressed as:

<center>

$Cor(X,Y) = E[XY] = E[X][Y]$
</center>

And if $E[XY] = 0$, it is called **orthogonal**. 

<br><br><br><br>


# Conditional Expectation and Variance

<br><br>

## Conditional Expectaion

The conditional expectation of $X$ that is given random variable $Y$ as $y$ is defined as formula [10].

<p align="center">
    <span>$E[X \mid Y = y] = \int_{-\infty}^{\infty}xp_{X \mid Y}(x \mid y) dx$</span>
    <span style="float: right;">[10]</span>
</p>

And conditional expectation of $X$ that is conditioning the random variable $Y$ is defined as formula [11].

<p align="center">
    <span>$E[X \mid Y] = \int_{-\infty}^{\infty}xp_{X \mid Y}(x \mid Y) dx$</span>
    <span style="float: right;">[11]</span>
</p>

<span style="color: red;">**Note that $E[X \mid Y=y]$ is a real number as a function of real number $y$, but $E[X \mid Y]$ is a random variable as a function of random variable $Y$.**</span>

<br><br>

The conditional expectaion of $X$ that is given random variable $Y$ as $y$ and the conditional expectation of $X$ That is conditioning the random variable $Y$ are defined as fromula [12], [13] respectively.

<p align="center">
    <span>$E[g(X) \mid Y=y] = \int_{-\infty}^{\infty}g(x)p_{X \mid Y}(x \mid y) dx$</span>
    <span style="float: right;">[12]</span>
</p>

<p align="center">
    <span>$E[g(X) \mid Y] = \int_{-\infty}^{\infty}g(x)p_{X \mid Y}(x \mid Y) dx$</span>
    <span style="float: right;">[13]</span>
</p>

Since $Var(X \mid Y)$ is also random variable, the expectation can be caluclated as formula [14].

<center>

$E[Var(X \mid Y)] = E[E[X^{2} \mid Y] - (E[X \mid Y])^{2}]$

<p align="center">
    <span>$= E[X^{2}] - E[(E[X \mid Y])^{2}]$</span>
    <span style="float: right;">[14]</span>
</p>
</center>


<br><br>

## Conditional variance

The conditional variance of $X$ that is given random variable $Y$ as $y$ and the conditional variance of $X$ That is conditioning the random variable $Y$ are defined as fromula [15], [16] respectively.

<center>

$Var(X \mid Y = y) = E[(X-E[X \mid Y=y)]^{2} \mid Y=y]$

<p align="center">
    <span>$= E[X^{2} \mid Y] - (E[X \mid Y = y])^{2}$</span>
    <span style="float: right;">[15]</span>
</p>

$Var(X \mid Y) = E[(X - E[X \mid Y])^{2} \mid y] $
<p align="center">
    <span>$= E[X^{2} \mid Y] - (E[X \mid Y])^{2}$</span>
    <span style="float: right;">[16]</span>
</p>

</center>

As [conditional expectaion](https://csh970605.github.io/posts/EValue_Variance/#conditional-expectaion) does, <span style="color: red;">**note that $Var[X \mid Y=y]$ is a real number as a function of real number $y$, but $Var[X \mid Y]$ is a random variable as a function of random variable $Y$.**</span>

And also, since $E(X \mid Y)$ is also random variable, the expectation can be caluclated as formula [17].

<center>

$Var(E[X \mid Y]) = E[(E[X \mid Y] - E[E[X \mid Y]])^{2}]$

<p align="center">
    <span>$= E[(E[X \mid Y])^{2} - (E[X])^{2}]$</span>
    <span style="float: right;">[17]</span>
</p>

</center>

According to the definition of [variance](https://csh970605.github.io/posts/EValue_Variance/#variance), $Var(X)$ can be expressed as follows:

<center>

$Var(X) = E[Var(X \mid Y)] + Var(E[X \mid Y])$
</center>