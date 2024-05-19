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

Random processe is usually capitalized and lowercase in the time function that random processe can actually take. That is if the time function of random process mapping the probability experiment result $E$ is $x(t), random process is written as $X(T, e) = x(t, e) or X(t) = x(t)$.<br>

$x(t)$ means the state of random process at time $t$, and it is called **sample function**. More speceifically, if e is fixed as $e = e_{1}$, random process becomes sample function $X(t, e_{1}) = x(t, e_{1})$. One more example, if e is fixed as $e = e_{2}$, random process becomes sample function $X(t, e_{2}) = x(t, e_{2})$.<br>

As you can see at the example, sample function is deterministic function and all the samples are called **ensemble**.
