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

A random process is defined as a function that maps the result of a probability experiment to a time function. It is written as:

<center>

$X(t)\equiv X(t, e)$
</center>

A random variable $X \equiv X(e)$ is defined as a function that maps the result of a probability experiment $e$ to a real number. A random process is used to model time-varying probability experiments. Examples include models for stock prices, wind power, sensor noise, etc.<br><br>

<br><br>

## Vector Random Process

A vector random process is a vector whose elements are scalar random processes. It is expressed as:

<center>

$X(t) \equiv X(t, e) = [X_{1}(t, e), X_{2}(t, e), \ldots, X_{n}(t, e)]^{T}$
</center>

It is also simply called a **random process**.

<br><br>

## Sample Function

A random process is usually denoted with capital letters, and the corresponding time function is denoted with lowercase letters. That is, if the time function of a random process mapping the probability experiment result $e$ is $x(t)$, the random process is written as $X(t, e) = x(t, e)$ or $X(t) = x(t)$.<br>

$x(t)$ represents the state of the random process at time $t$, and it is called a **sample function**. More specifically, if $e$ is fixed as $e = e_{1}$, the random process becomes the sample function $X(t, e_{1}) = x(t, e_{1})$. For another example, if $e$ is fixed as $e = e_{2}$, the random process becomes the sample function $X(t, e_{2}) = x(t, e_{2})$.<br>

As you can see in the example, a sample function is a deterministic function, and all the samples are called an **ensemble**.
<br><br>

If time is discrete, the random process is called a **discrete-time random process** or a **random sequence**. It is expressed as :

<center>

$X(k) \equiv X(k, e) = [X_{1}(k, e), X_{2}(k, e), \ldots, X_{n}(k, e)]^{T}$
</center>

where $k$ is the index of time.
<br><br><br><br>

# Mean Function and Auto-correlation Function and Auto-covariance Function

In this section, we will discuss the **mean function**, **auto-correlation function**, **auto-covariance function**.

Apart from these, the other definitions of a random sequence are the same as those of a random process.

<br><br>

## Mean Function

The [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) of a random process is a function of time because it can vary from time to time, and it is written as $p_{X}(x(t))$. At time $t = t_{1}$, the expectation or ensemble mean function is defined as the expectation of the elements of a random vector.

This means that

<center>

$\mu_{X}(t_{1}) = \mathbb{E}[X(t_{1})]$
</center>

<br><br>

## Auto-correlation Function

At times $t_{1}$ and $t_{2}$, two random vectors have the [joint probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#joint-probability-function) $p_{X}(x(t_{1}), x(t_{2}))$.
To show the auto-correlation at different points in time of a random process, we define the auto-correlation function $R_{XX}(t_{1}, t_{2})$ as follows:

<center>

$R_{XX}(t_{1}, t_{2}) = \mathbb{E}[X(t_{1}), X^{T}(t_{2})]$

$= \begin{bmatrix}
\mathbb{E}[X_{1}(t_{1}), X_{1}(t_{2})] & \cdots & \mathbb{E}[X_{1}(t_{1}), X_{n}(t_{2})]\\
\vdots & \ddots & \vdots\\
\mathbb{E}[X_{n}(t_{1}), X_{1}(t_{2})] & \cdots & \mathbb{E}[X_{n}(t_{1}), X_{n}(t_{2})]
\end{bmatrix}$
</center>
<br>

The auto-correlation function represents the auto-correlation of random processes in the time domain and the power or distribution of energy that the process contains in the frequency domain.
<br><br>

## Auto-covariance Function

The auto-covariance function $P_{XX}(t_{1}, t_{2})$ is defined as follows:

<center>

$P_{XX}(t_{1}, t_{2}) = \mathbb{E}[(X(t_{1})-\mathbb{E}[X(t_{1})])(X(t_{2})-\mathbb{E}[X(t_{2})])^{T}]$
</center>

<br><br>
<br><br>

# Stationarity Process

A stationary process means that the partial or entire probabilistic feature of a random process is time-invariant.<br>

In stationary processes, there are two types:

+ [Strict-sense stationary (SSS)](https://csh970605.github.io/posts/Rand_Process/#strict-sense-stationarysss)

+ [Wide-sense stationary (WSS)](https://csh970605.github.io/posts/Probability_RandomVector/#wide-sense-stationarywss)

<br><br>

## Strict Sense Stationary (SSS)

If the probability density function of a random process $X(t)$, when taking any $m$ time points $t_{1} < t_{2} < \ldots < t_{m}$, satisfies the following expression for the joint probability density functions of $X(t_{1}), X(t_{2}), \ldots , X(t_{m})$ for any $h > 0$, then $X(t)$ is called an **SSS process**.

<center>

$p_{X}(x(t_{1}), x(t_{2}), \ldots , x(t_{m})) = p_{X}(x(t_{1} + h), x(t_{2} + h), \ldots , x(t_{m} + h))$
</center>

If $X(t)$ is an SSS process, the mean of the ensemble becomes constant, and the auto-correlation function $R_{XX}(t_{1}, t_{2})$ at any two time points $t_{1}$ and $t_{2}$ becomes a function of the time difference between the two time points $(t_{2} - t_{1})$.<br>
That is,

+ $\mathbb{E}[X(t)] = \text{constant}$

+ $R_{XX}(t_{1}, t_{2}) = R_{XX}(t_{2} - t_{1}) = R_{XX}(\tau)$
<br><br>

## Wide Sense Stationary (WSS)

If the mean of the ensemble of a random process $X(t)$ is constant and $R_{XX}(t_{1}, t_{2}) = R_{XX}(\tau)$, then $X(t)$ is called a **WSS process**.<br>

If $X(t)$ is an SSS process, then $X(t)$ is also a WSS process, but the inverse is not true.<br><br>

In WSS, a sharp decrease in $R_{XX}$ for $\tau$, as shown in image [1], results in a sharp decrease in the correlation between the two time points. Conversely, a gradual decrease in $R_{XX}$ for $\tau$, as shown in image [2], results in a gradual decrease in the correlation between the two time points. <br>

Thus, $R_{XX}(\tau)$ functions as a measure of the rate of change of $X(t)$ relative to time $t$. In other words, it acts as a kind of frequency response to $X$.

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/c9705da9-6b4f-4b13-ba82-9cc59621c8d6">
image [1]<br><br>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/c8c40ceb-11e9-4283-a8be-0295a08b98d5">
image [2]
</center>
WSS is a general condition that can also be applied to multi-dimensional signals, that is, time series data of vector values. However, there is also scalar WSS used when the WSS condition is applied to a single variable (scalar) time signal.

<br><br>

### Scalar WSS

In scalar WSS, the features of the auto-correlation function $R_{XX}(\tau)$ of $X(t)$ and $Y(t)$ are as follows:

+ $\mathbb{E}[X^{2}(t)] = R_{XX}(0) \geq 0$

+ $R_{XX}(\tau) = R_{XX}(-\tau)$

+ $\left | R_{XX}(\tau) \right | \leq R_{XX}(0)$
<br><br>
<br><br>

# Power Spectral Density (PSD)

The power spectral density $S_{XX}(\omega)$ of a WSS random process is defined as the Fourier transform of the auto-correlation function. The function $S_{XX}(\omega)$ is:

<center>

$S_{XX}(\omega) = \int_{-\infty}^{\infty}R_{XX}(\tau)e^{-j\omega \tau}d\tau$

</center>

where $\omega$ is the frequency in $rad/sec$.
<br>

We can get the auto-correlation function by using the Fourier inverse transform from the power spectral density as:

<center>

$R_{XX}(\tau) = \frac{1}{2\pi}\int_{-\infty}^{\infty}S_{XX}(\omega)e^{j\omega\tau}d\omega$
</center>
<br>

The power of $X(t)$ is calculated from the auto-correlation function or power spectral density as:

<center>

$\mathbb{E}[X(t)X^{T}(t)] = R_{XX}(0) = \frac{1}{2\pi}\int_{-\infty}^{\infty}S_{XX}(\omega)d\omega$
</center>
<br>

The power spectral density of a WSS random sequence $S_{XX}(\hat{\omega})$ is defined by the discrete-time Fourier transform of the auto-correlation function as:

<center>

$S_{XX}(\hat{\omega}) = \sum_{n=-\infty}^{\infty}R_{XX}(n)e^{-j\hat{\omega}n}$
</center>
<br>

where $\hat{\omega}$ is the discrete-time frequency and the range is $\hat{\omega} \in [-\pi, \pi]$.<br>

Also, we can get the auto-correlation function by the discrete-time Fourier inverse transform from the power spectral density as:
<center>

$R_{XX}(n) = \frac{1}{2\pi}\int_{-\pi}^{\pi}S_{XX}(\hat{\omega})e^{j\hat{\omega}n}d\hat{\omega}$
</center><br>

The power of a random sequence $X(k)$ can be calculated from the auto-correlation function or power spectral density as:

<center>

$\mathbb{E}[X(k)X^{T}(k)] = R_{XX}(0) = \frac{1}{2\pi}\int_{-\pi}^{\pi}S_{XX}(\hat{\omega})d\hat{\omega}$/*

$= \int e^{(a-jw)\tau}d\tau$
</center>

<br><br><br><br>

# White Noise

A random process that is temporally uncorrelated is called **white noise** $V(t)$. It is an impulse-like signal in a deterministic system, defined as a WSS process in which the auto-correlation function is given as a [Dirac delta function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-mass-function) as follows:

<center>

$\mathbb{E}[V(t)V^{T}(t+\tau)] = R_{VV}(\tau) = S_{0}\delta(\tau)$
</center>

where $S_{0}$ is a constant matrix.<br>

The power spectral density is:

<center>

$S_{VV}(\omega) = \int_{-\infty}^{\infty}R_{VV}(\tau)e^{-j\omega \tau}d\tau = S_{0}\int_{-\infty}^{\infty}\delta(\tau)e^{-j\omega \tau}d\tau = S_{0}$
</center>

Therefore, white noise has the same power spectral density value across all frequencies.<br>
<br>

## White Noise Sequence

A WSS random sequence $V(k)$, in which the auto-correlation function is given as a Kronecker delta function, is called a **white noise sequence**.

<center>

$\mathbb{E}[V(k)V^{T}(k+m)] = R_{VV}(m) = S_{0}\delta_{m}$
</center>

where $\delta_{m}$ is a Kronecker delta function defined as:

<center>

$\delta_{m} = \left\{\begin{matrix}
1, \ m=0\\ 
0, \ m \neq 0
\end{matrix}\right.$
</center>

The power spectral density of a white noise sequence is:

<center>

$S_{VV}(\hat{\omega}) = \sum_{n=-\infty}^{\infty}R_{VV}(n)e^{-j\hat{\omega}n} = S_{0}$
</center>

It has the same power spectral density value across all frequencies.

<br><br>

## Gaussian White Noise

At every time point $t$ or $k$, if the probability density function of white noise $V(t)$ or $V(k)$ is given as a Gaussian function, it is called **gaussian white noise**.

<br><br><br><br>

# Ergodic Process in The Mean

An ergodic process in the mean means that a sample function extracted from a stationary random process randomly includes all probabilistic information of the random process. Although it is very hard to prove whether it is an ergodic process or not, <span style="color: red;">note that white noise is an ergodic process.</span>


A time average and time correlation of any deterministic function $x(t)$ are defined as equations [1] and [2], respectively.

<p align="center">
    <span>&lt; $x(t)$ &gt; $=lim_{T \rightarrow \infty} \frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)dt$</span>
    <span style="float: right;">[1]</span>
</p>
<p align="center">
    <span>&lt; $x(t)x^{T}(t+\tau)$ &gt; $=lim_{T \rightarrow \infty} \frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)x^{T}(t+\tau)dt$</span>
    <span style="float: right;">[2]</span>
</p>

If $x(t)$ is a sample function of a stationary process, and if the ensemble mean $\mathbb{E}[X(t)]$ of $X(t)$ equals the time average $\langle x(t) \rangle$, $X(t)$ is called an **ergodic process in the mean**.<br>
Also, if the ensemble correlation $\mathbb{E}[X(t)X^{T}(t+\tau)]$ of $X(t)$ equals the time correlation $\langle x(t)x^{T}(t+\tau) \rangle$, $X(t)$ is called a **correlation ergodic process in the mean**.<br>

In a random sequence, time average and time correlation are defined as equations [3] and [4], respectively.

<p align="center">
    <span>&lt; $x(k)$ &gt; $=lim_{T \rightarrow \infty} \frac{1}{2N+1}\sum_{k=-n}^{N}x(k)$</span>
    <span style="float: right;">[1]</span>
</p>
<p align="center">
    <span>&lt; $x(k)x^{T}(k+m)$ &gt; $=lim_{T \rightarrow \infty} \frac{1}{2N+1}\sum_{k=-n}^{N}x(k)X^{T}(k+m)$</span>
    <span style="float: right;">[2]</span>
</p>

<br><br><br><br>

# Independent, Identically Distributed (IID)

If all random vectors that constitute a random process $X(t)$ are independent and have the same probability density function, $X(t)$ is called **IID**.<br>
If all random vectors that constitute a random sequence $X(t)$ are independent and have the same probability density function, $X(t)$ is called an **IID sequence**.

<br><br><br><br>

# Markov Process

A Markov process is a random process in which, given the current probability information, the future and the past are irrelevant or conditionally independent of each other.<br>
That is, when the probability distribution of a random process $X(t)$ is given at a specific time point $t_{1}$, if the probability distribution of $X(t)$ at time point $t > t_{1}$ is irrelevant to the probability distribution of $X(s)$ at time point $s < t_{1}$, $X(t)$ is defined as a **Markov process**.<br>
A Markov process is expressed probabilistically as follows:

<center>

$p_{X}(x(t) \mid x(s) \leq t_{1}) = p_{X}(x(t) \mid x(t_{1})), \ \ \forall t > t_{1}$
</center>
<br>

Similar to the Markov process, the definition of a Markov sequence is determined by the probability distribution of the preceding step. The equation for the Markov sequence $X(k)$ using the probability density function and an image of the Markov sequence is:

<center>

$p_{X}(s(k) \mid x(k-1), x(k-2), \ldots , x(0)) = p_{X}(x(k) \mid x(k-1)), \ \ \forall k$<br>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/27150017-1960-463c-88f7-44749beb755f">
</center>

<br><br><br><br>

# Differentiation of a Random Process

If a random process $X(t)$ satisfies the following equation, $X(t)$ is called **continuous in the mean square sense** at time $t=t_{0}$.

<center>

$\lim_{t \rightarrow t_{0}} \mathbb{E}[(X(t) - X(t_{0}))^{2}] = 0$
</center><br>

If a random process is continuous in the mean square sense at $t=t_{0}$, it can be written simply as a general deterministic function as:

<center>

$\lim_{t \rightarrow t_{0}} X(t) = X(t_{0})$
</center>

<br>

A random process can be differentiated because it changes over time. The differentiation $X'(t)$ of a random process $X(t)$ is defined as:
<center>

$X'(t) = \frac{dX(t)}{dt} = \lim_{h \rightarrow 0} \frac{X(t+h)-X(t)}{h}$
</center>

<font color='red'>

Note that the law of exchange holds for the differentiation or integral of the random process and the average operator $\mathbb{E}$.
</font>