---
title: Kalman Filter
author: SeHoon
date: 2024-04-16 10:01:30 +0900
categories: [Mathematics, Statistics]
tags: [Papers, Mathematics, MultiObjectTracking]
math: true
mermaid: true
---

# Kalman Filter

The Kalman Filter is **[estimator](https://csh970605.github.io/posts/Kalman_Filter/#estimator)** that uses the state-space equation of the system and is an optimal data processing algorithm with a recursive structure. Initially, Kalman Filters could only be used in linear systems, but a method that could be applied to nonlinear systems was devised later.<br>
A basic Kalman Filter looks like this:

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/27e45739-cd80-452e-b80f-f413a54ef2d0">
</center>

<br><br>


## Estimator

An estimator is an algorithm that estimates an unknown quantity from available information:

+ **The unknown quantities** are usually expressed as **[state variables](https://csh970605.github.io/posts/Kalman_Filter/#state-variables)** and **[system parameters](https://csh970605.github.io/posts/Kalman_Filter/#system-parameters)**.
+ **The available information** consists of an exercise model, a measurement model, a noise model, and measurement data.
<br>

An estimator is classified into **prediction**, **filtering**, **smoothing** according to the measurement data and the estimation point of state variables:
+ Prediction : Infers future state variables based on measurement data from the past to the present. It is used to estimate the trajectory of celestial bodies or future stock prices.<br><br>

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/bfb2800a-09b5-4df4-8dc7-184d5c079c1b">
    </center><br>

+ Filtering : Infers present state variables based on measurement data from the past to the present. It is used to estimate the real-time state of robots, missiles, or airplanes.<br><br>

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3ad1fc7f-d057-42e7-ae8d-42f919769118">
    </center><br>

+ Smoothing : Infers present state variables based on measurement data from the past to the future. It is used to estimate the state of the system by post-processing measurement data accumulated in a test or experiment.<br><br>

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0b31f93f-d961-4f6f-ac4c-488675bde63d">
    </center><br>
<br><br>

The Kalman filter provides the mathematical method that can be applied to these three estimation methods.
<br><br>

### State variables

State variables are variables that can change significantly over time due to external forces or actions.
<br><br>


### System parameters

System parameters are variables that do not change or change slowly over time. However, if necessary, system parameters are sometimes considered as state variables. For example, if a parameter is the unknown quantity to be estimated, it is regarded as a state variable.

<br><br><br><br>

## Dynamics Model

One type of available information, the dynamics model, is a mathematical model that describes how the properties of dynamic systems change over time.<br>
Dynamics models are built to describe specific state variables and parameters of interest, as well as the interrelationships between system inputs and outputs, using Newton's laws of motion, empirical insights, experiments, etc.<br>

A dynamics model needs to be created to accurately describe real-world motion, but it involves many uncertainties in practice.<br>
These uncertainties are caused by various approximation processes while deriving mathematical dynamics models, unexpected increases in system complexity during operation, disruptions from outside the system, or changes in the operating environment. Additionally, this happens because only important dynamic modes are intentionally modeled while the rest are not. In some cases, it may be due to a lack of understanding of the system, the high cost and time required to obtain a model, or special conditions.<br>

Given the uncertainty inherent in these mathematical dynamics models, the best modeling method is to use probabilities to express this uncertainty.<br>
Therefore, the mathematical dynamics model can be represented as a **[state-space equation](https://csh970605.github.io/posts/Kalman_Filter/#state-space-equation)**.<br>

However, Kalman filters should not be developed as continuous-time models as shown in formula [1], but as [discrete-time models](https://csh970605.github.io/posts/Kalman_Filter/#discrete-time-model).<br>

Finally, the dynamics model is expressed as:
<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/a43ae4a4-e53d-4fbd-ad31-da60c5332f9e">
</center>
<br>

The performance of a Kalman filter depends on the accuracy of the system model.Therefore, to properly select and build a system model, you need to understand the system, state variables, parameters, etc.
<br><br>


### State-Space Equation

The state-space equation is expressed as follows:
<p align="center">
    <span>$\dot{x}(t)=f(x(t), u(t), w(t),t)$</span>
    <span style="float: right;">[1]</span>
</p>


where 
+ $x(t) \in \mathbb{R}^{p}$: A state variable. It is introduced to express the uncertainty inherent in the mathematical dynamic model.
+ $w(t) \in \mathbb{R}^{m}$: Process noise. It is called a noise model that represents the probabilistic nature of $w(t)$.
+ $u(t) \in \mathbb{R}^{q}$: An input of the system. It is also referred to as the "control input" and is assumed to be accurately known.
+ $f(\cdot, t)$: A time-varying non-linear function that includes system parameters.
+ $x(t)$ : At a given time, it is assumed to contain all the relevant information to describe the motion of the system.

<br><br>

### Discrete-Time Model


The discrete-time model is a special case of the continuous-time model where measurements are sampled at discrete times and system inputs are kept constant within the sampling period. It is expressed as a difference equation as follows:

<p align="center">
    <span>$x(k+1) = f(x(k), u(k), w(k), k)$</span>
    <span style="float: right;">[2]</span>
</p>

where
+ $k$ : Time index.
+ $x(k)$ : $x(kT)$, where $T$ is the sampling time.
<br>

This will be discussed later.

<br><br>

## Measurement Model

The measurement model is a mathematical expression of the functional relationship between measurement values, which are data acquired as output values from various sensors to observe the motion of the system, and state variables and parameters.<br>
Since the dynamics of the system can be explained by changes in the state variables over time, sensors must measure the state variables. However, since sensor measurements can be contaminated by noise or bias, sensors cannot measure the exact values as intended.<br>

To solve this problem, the Kalman filter devises a mathematical tool to infer unmeasured data using contaminated measurement data. The measurement model assumes that measurements are collected at discrete times and is expressed as follows:

<p align="center">
    <span>$z(k) = h(x(k),k) + v(k)$</span>
    <span style="float: right;">[3]</span>
</p>

where

+ $z(k) \in \mathbb{R}^{p}$ : Measurements.
+ $v(k) \in \mathbb{R}^{p}$ : Measurement noise. It is a variable for expressing the error inherent in the measurement as a probability.
+ $h(x(k),k)$ : A non-linear function for expressing the functional relationship between state variables and outputs.

Finally, the measurement model is expressed as:
<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/c9cd08a1-12eb-43e8-8134-b0fa84975671">
</center>

