---
title: Gaussian Distribution
author: SeHoon
date: 2023-09-15 10:42:30 +0900
categories: [Mathematics, Statistics]
tags: [Mathematics, Statistics]
math: true
mermaid: true
---

# What is Gaussian Distribution?

Gaussian distribution also known as normal distribution is a type of continuous probability distribution.<br>
The general form of its [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) is :

<center>
<font size=4>

$f(x) = \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}$<br>
</font>
</center>

Where <br>

+ $\mu$ : The mean or expectation of distribution.<br>
+ $\sigma$ : standard deviation.


Since gaussian distribution is calculated by two probability information, that is, expectation and distribution, it is easy to treat mathematically. And also, since lots of signals from nature is similiary to gaussian distribution, it is usually used to model the various social, nature phenomenons.

The shape of gaussian distribution is:

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/04a3e688-62ca-45e3-b253-73717f7bb95d">
</center>

The probability density function of gaussian random vector $X$ is defined as formula[1].

<center>

$p_{X}(x) = N(x \mid \mu_{X}, P_{XX})$

<p align="center">
    <span>$= \frac{1}{\sqrt{(2 \pi)^{n}detP_{XX}}e^{-\frac{1}{2}(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X})}}$</span>
    <span style="float: right;">[2]</span>
</p>

</center>

Where

+ $\mu_{X}$ : Expectation.
+ $P_{XX}$ : Covariance.