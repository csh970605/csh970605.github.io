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

# Mean Function and Auto-correlation Function and Auto-covariance Function

In this section, we will see **mean function**, **auto-correlation function**, **auto-covariance function**.

Except those, the other definition of random sequence is the same as random process

<br><br>

## Mean Function

The [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) of random process is a function of time because it can vary from time to time. And written as $p_{X}(x(t))$. At the time $t = t_{1}$, a expectation or ensemble mean function is defined as expectations of the elements of a random vector respectively.

That is,

<center>

$\mu_{X}(t_{1}) = E[X(t_{1})]$
</center>

<br><br>

## Auto-correlation Function

At time $t_{1}$ and $t_{2}$, two random vectors have [joint probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#joint-probability-function) $p_{X}(x(t_{1}), x(t_{2}))$.
To show auto-correlation at different points in time of random process, we define auto-correlation function $R_{XX}(t_{1}, t_{2})$ as follows:

<center>

$R_{XX}(t_{1}, t_{2}) = E[X(t_{1}), X^{T}(t_{2})]$

$= \begin{bmatrix}
E[X_{1}(t_{1}), X_{1}(t_{2})] & \cdots & E[X_{1}(t_{1}), X_{n}(t_{2})]\\
\vdots & \ddots & \vdots\\
E[X_{n}(t_{1}), X_{1}(t_{2})] & \cdots & E[X_{n}(t_{1}), X_{n}(t_{2})]
\end{bmatrix}$
</center>
<br>

Auto-correlation function represents the auto-correlation of random processes in the time domain and represents the power or distribution of energy that process contains in the frequency domain.
<br><br>

## Auto-covariance Function

Auto-covariance Function $P_{XX}(t_{1}, t_{2})$ is defined as:

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

If $X(t)$ is SSS process, a mean of ensemble becomes constant and auto-correlation function $R_{XX}(t_{1}, t_{2})$ at any two time points $X(t_{1})$ and $X(t_{2})$ becomse a function of the time difference between two time points $(t_{2} - t_{1})$.<br>
That is,

+ $E[X(t)] = constant$

+ $R_{XX}(t_{1}, t_{2}) = R_{XX}(t_{2} - t_{1}) = R_{XX}(\tau)$
<br><br>

## Wide Sense Stationary(WSS)

If a mean of ensemble of random process $X(t)$ is constant and $R_{XX}(t_{1}, t_{2} = RXX_{\tau})$, $X(t)$ is called **WSS process**.<br>

If $X(t)$ is SSS process, $X(t)$ is WSS process also but inverse is not established.<br><br>

In the WSS, a sharp decrease in $R_{XX}$ for $\tau$ as shown in the image [1] results in a sharp decrease in the correlation between the two time points. Conversely, a gradual decrease in $R_{XX}$ for $\tau$ as shown in the image [2] results in a gradual decrease in the correlation between the two time points. <br>

Thus, $R_{XX}(\tau)$ functions as a measure of the rate of change of $X(t)$ relative to time $t$. In other words, it acts as a kind of frequency response to $X$.

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/c9705da9-6b4f-4b13-ba82-9cc59621c8d6">
image [1]<br><br>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/c8c40ceb-11e9-4283-a8be-0295a08b98d5">
image [2]
</center>
WSS is a general condition that can also be applied to multi-dimensional signals, that is, time series data of vector values, but there is also a scalar WSS used when the WSS condition is applied to a single variable (scalar) time signal.

<br><br>

### Scalar WSS

At scalar WSS, the feature of auto-correation funtion $R_{XX}(\tau)$ of $X(t)$ and $Y(t)$ is:

+ $E[X^{2}(t)] = R_{XX}(0) \geq 0$

+ $R_{XX}(\tau) = R_{XX}(-\tau)$

+ $\left | R_{XX}(\tau) \right | \leq R_{XX}(0)$
<br><br>
<br><br>

# Power Spectral Density(PSD)

Power spectral density $S_{XX}(\omega)$ of WSS random process is defined as fourier transform of auto-correation function. The function of $S_{XX}(\omega)$ is :

<center>

$S_{XX}(\omega) = \int_{-\infty}^{\infty}R_{XX}(\tau)e^{-j\omega \tau}d\tau$

</center>

where $\omega$ is frequency in $rad/sec$.
<br>

We can get auto-correation function by using fourier inverse transform from power spectral density as:

<center>

$R_{XX}(\tau) = \frac{1}{2\pi}\int_{-\infty}^{\infty}S_{XX}(\omega)e^{j\omega\tau}d\omega$
</center>
<br>

The power of $X(t)$ is calculated from auto-correaltion function or power spectral density as:

<center>

$E[X(t)X^{T}(t)] = R_{XX}(0) = \frac{1}{2\pi}\int_{-\infty}^{\infty}S_{XX}(\omega)d\omega$
</center>
<br>

The power spectral density of WSS random sequence $S_{XX}(\hat{\omega})$ is defined by discrete-time fourier transform of auto-correlation function as:

<center>

$S_{XX}(\hat{\omega}) = \Sigma_{n=-\infty}^{\infty}R_{XX}(n)e^{-j\hat{\omega}n}$
</center>
<br>

where $\hat{\omega}$ is discrete-time frequency and the range is $\hat{\omega} \in [-\pi, \pi]$.<br>

Also, we can get a auto-correlation function by discrete-time fourier inverse transform from power spectral density as:

<center>

$R_{XX}(n) = \frac{1}{2\pi}\int_{-\pi}^{\pi}S_{XX}(\hat{\omega})e^{j\hat{\omega}n}d\hat{\omega}$
</center><br>

A power of random sequence $X(k)$ can be calculated from auto-correlation function or power spectral density as:

<center>

$E[X(k)X^{T}(k)] = R_{XX}(0) = \frac{1}{2\pi}\int_{-\pi}^{\pi}S_{XX}(\hat{\omega})d\hat{\omega}$

$\int e^{(a-jw)\tau}d\tau$
</center>

<br><br><br><br>

# White Noise

A random process that is in non-relationship timely is called **white noise** $V(t)$. And it is an impulse-like signal in a deterministic system, defined as a WSS process in which the auto-correlation function is given as a [Dirac delta function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-mass-function) as follows:

<center>

$E[V(t)V^{T}(t+\tau)] = R_{VV}(\tau) = S_{0}\delta(\tau)$
</center>

where $S_{0}$ is const matrix.<br>

And the power spectral density is:

<center>

$S_{VV}(\omega) = \int_{-\infty}^{\infty}R_{VV}(\tau)e^{-j\omega \tau}d\tau = S_{0}\int_{-\infty}^{\infty}\delta(\tau)e^{-j\omega \tau}d\tau = S_{0}$
</center>

Therefore, a white noise has same power spectral density value at all of the frquency domain.<br>
<br>

## White Noise Sequence

WSS random sequence $V(k)$ that the auto-correlation function is given as a kronecker delta function as follows is called **white noise sequence**.

<center>

$E[V(k)V^{T}(k+m)] = R_{VV}(m) = S_{0}\delta_{m}$
</center>

where $\delta_{m}$ is a kronecker delta function and is defined as:

<center>

$\delta_{m} = \left\{\begin{matrix}
1, \ m=0\\ 
0, \ m \neq 0
\end{matrix}\right.$
</center>

And the power spectral density of white noise sequnce is:

<center>

$S_{VV}(\hat{\omega}) = \Sigma_{n=-\infty}^{\infty}R_{VV}(n)e^{-j\hat{\omega}n} = S_{0}$
</center>

And it has same power spectrum density values in all frequency domain.

<br><br>

## Gaussian White Noise

In every time point $t$ or $k$, a probability density function of white noise $V(t) or V(k) is given as a gaussian function, it is called **gaussian white noise**.

<br><br><br><br>

# Ergodic Process in The Mean

A time average and time correlation of any deterministic function $x(t)$ is defined as formula [1] and formula [2] respectively.

<p align="center">
    <span>&lt; $x(t)$ &gt; $=lim_{T \rightarrow \infty} \frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)dt$</span>
    <span style="float: right;">[1]</span>
</p>
<p align="center">
    <span>&lt; $x(t)x^{T}(t+\tau)$ &gt; $=lim_{T \rightarrow \infty} \frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)x^{T}(t+\tau)dt$</span>
    <span style="float: right;">[2]</span>
</p>