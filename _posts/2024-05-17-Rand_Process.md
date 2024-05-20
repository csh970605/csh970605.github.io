---
title: Random Process
author: SeHoon
date: 2024-05-17 10:02:30 +0900
categories: [Mathematics, Statistics]
tags: [Mathematics, Statistics, Kalman Filter]
math: true
mermaid: true
---

# Random Process

A random process is defined as the function mapping the result of probability experiment to the time function. It is written as:

<center>

$X(t)\equiv X(t, e)$
</center>

And random variable $X\equiv X(e)$ is defined as the function mapping the result of probability $e$ to the real number.<br>
Random process is used to model the time-varying probability experiments. For example, models for stock prices, power of wind, noises of sensor, etc.<br><br>

<br><br>

## Vector Random Process

Vector random process is the vector whose element is scalar random process. It is expressed as:

<center>

$X(t) \equiv X(t,e) = [X_{1}(t, e)X_{2}(t,e), ..., X_{n}(t,e)]^{T}$
</center>

And it is simply called random process.

<br><br>

## Sample Function

Random processe is usually capitalized and lowercase in the time function that random processe can actually take. That is if the time function of random process mapping the probability experiment result $E$ is $x(t)$, random process is written as $X(T, e) = x(t, e) or X(t) = x(t)$.<br>

$x(t)$ means the state of random process at time $t$, and it is called **sample function**. More speceifically, if e is fixed as $e = e_{1}$, random process becomes sample function $X(t, e_{1}) = x(t, e_{1})$. One more example, if e is fixed as $e = e_{2}$, random process becomes sample function $X(t, e_{2}) = x(t, e_{2})$.<br>

As you can see at the example, sample function is deterministic function and all the samples are called **ensemble**.
<br><br>

And if time is discrete, the random process is called **discrete-time** or **random sequence**. It is expressed as :

<center>

$X(k) \equiv X(k,e) = [X_{1}(k,e)X_{2}(k,e), ..., X_{n}(k,e)]^{T}$
</center>

Where $k$ is index of time.
<br><br><br><br>

# Mean Function and Autocorrelation Function and Autocovariance Function

In this section, we will see **mean function**, **autocorrelation function**, **autocovariance function**.

Except those, the other definition of random sequence is the same as random process

<br><br>

## Mean Function

The [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) of random process is a function of time because it can vary from time to time. And written as $p_{X}(x(t))$. At the time $t = t_{1}$, a expectation or ensemble mean function is defined as expectations of the elements of a random vector respectively.

That is,

<center>

$\mu_{X}(t_{1}) = E[X(t_{1})]$
</center>

<br><br>

## Autocorrelation Function

At time $t_{1}$ and $t_{2}$, two random vectors have [joint probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#joint-probability-function) $p_{X}(x(t_{1}), x(t_{2}))$.
To show autocorrelation at different points in time of random process, we define autocorrelation function $R_{XX}(t_{1}, t_{2})$ as follows:

<center>

$R_{XX}(t_{1}, t_{2}) = E[X(t_{1}), X^{T}(t_{2})]$

$= \begin{bmatrix}
E[X_{1}(t_{1}), X_{1}(t_{2})] & \cdots & E[X_{1}(t_{1}), X_{n}(t_{2})]\\
\vdots & \ddots & \vdots\\
E[X_{n}(t_{1}), X_{1}(t_{2})] & \cdots & E[X_{n}(t_{1}), X_{n}(t_{2})]
\end{bmatrix}$
</center>
<br><br>

## Autocovariance Function

Autocovariance Function $P_{XX}(t_{1}, t_{2})$ is defined as:

<center>

$P_{XX}(t_{1}, t_{2}) = E[(X(t_{1})-E[X(t_{1})])(X(t_{2})-E[X(t_{2})])^{T}]$
</center>

<br><br>
<br><br>

# Stationarity Process

Stationarity process means the partial or entire probabilitic feature of random process is time-invariant.<br>

In stationarity process, there are two process:

+ [Strict-sense stationary(SSS)](https://csh970605.github.io/posts/Rand_Process/#strict-sense-stationarysss)

+ [Wide-sense stationary(WSS)](https://csh970605.github.io/posts/Probability_RandomVector/#wide-sense-stationarywss)

<br><br>

## Strict Sense Stationary(SSS)

If at a probability density function of random process $X(t)$, when taking any $m$ time points $t_{1} < t_{2} < ... < t_{m}$, joint probability density functions of $X(t_{m}), X(t_{m}), ..., X(t_{m})$ satisfy the following expression for any $h > 0$, $X(t)$ is called **SSS process**

<center>

$p_{X}(x(t_{1}), x(t_{2}), ..., x(t_{m})) = p_{X}(x(t_{1} + h), x(t_{2} + h), ..., x(t_{m} + h))$
</center>

If $X(t)$ is SSS process, a mean of ensemble becomes constant and autocorrelation function $R_{XX}(t_{1}, t_{2})$ at any two time points $X(t_{1})$ and $X(t_{2})$ becomse a function of the time difference between two time points $(t_{2} - t_{1})$.<br>
That is,

+ $E[X(t)] = constant$

+ $R_{XX}(t_{1}, t_{2}) = R_{XX}(t_{2} - t_{1}) = R_{XX}(\tau)$
<br><br>

## Wide Sense Stationary(WSS)

If a mean of ensemble of random process $X(t)$ is constant and $R_{XX}(t_{1}, t_{2} = RXX_{\tau})$, $X(t)$ is called **WSS process**.<br>

If $X(t)$ is SSS process, $X(t)$ is WSS process also but inverse is not established.<br>

WSS is a general condition that can also be applied to multi-dimensional signals, that is, time series data of vector values, but there is also a scalar WSS used when the WSS condition is applied to a single variable (scalar) time signal.

<br><br>

### Scalar WSS

At scalar WSS, the feature of auto-correation funtion $R_{XX}(\tau)$ of $X(t)$ and $Y(t)$ is:

+ $E[X^{2}(t)] = R_{XX}(0) \geq 0$

+ $R_{XX}(\tau) = R_{XX}(-\tau)$

+ $\left | R_{XX}(\tau) \right | \leq R_{XX}(0)$
<br><br>
