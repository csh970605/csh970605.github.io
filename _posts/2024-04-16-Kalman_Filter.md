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

Kalman Filter is an **[estimator](https://csh970605.github.io/posts/Kalman_Filter/#estimator)** using the state-space equation of the system and it is an optimal data processing algorithm with a recursive structure.<br>
Initially, Kalman Filters could only be used in linear systems, and a method that could be applied to nonlinear systems was devised later.<br>
Basic kalman filter looks like:

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/27e45739-cd80-452e-b80f-f413a54ef2d0">
</center>

<br><br>


## Estimator

Estimator is an algorithm that estimates an unknown quantity from available informations:
+ **The unkown quantities** are usually expressed as **[state variables](https://csh970605.github.io/posts/Kalman_Filter/#state-variables)** and **[system parameters](https://csh970605.github.io/posts/Kalman_Filter/#system-parameters)**.
+ **The available informations** consists of an exercise model, a measurement model, a noise model, and measurement data.
<br>

And Estimator is classified into **prediction**, **filtering**, **smoothing** according to the measurment data and the estimation point of state variables:
+ Prediction : Infer future state variables based on measurement data from the past to the present. It is used to estimate the trajectory of celestial bodies or estimate future stock prices.<br><br>

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/bfb2800a-09b5-4df4-8dc7-184d5c079c1b">
    </center><br>

+ Filtering : Infer present state variables based on measurement data from the past to the present. It is used to estimate the real-time state of robots, missiles, or airplanes.<br><br>

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3ad1fc7f-d057-42e7-ae8d-42f919769118">
    </center><br>

+ Smoothing : Infer present state variables based on measurement data from the past to the future. It is used to estimate the state of the system by post-processing measurement data accumulated in a test or experiment.<br><br>

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0b31f93f-d961-4f6f-ac4c-488675bde63d">
    </center><br>
<br><br>

Kalman filter provides the mathmetical mothod that can be applied to the three estimate methods.
<br><br>

### State variables

State variables are variables that can be changed extremly over time by external forces or actions.
<br><br>


### System parameters

System parameters are variables that do not change or change slowly over time. However, if necessary, the system parameters are sometimes considered as state variables. For example, if the parameter is the unknown quantity to be estimated, the parameter is regarded as a state variable.

<br><br><br><br>

## Dynamics Model

One of the available information, the dynamics model, is a mathematical model that descirbes how excercise properties of dynamic systems change over time.<br>
dynamics model are built to describe specific state variables and parameters of interest and interrelationships between system inputs and outputs using Newton's laws of motion, empirical insights, experiments, etc.<br>

Dynamics model needs to be modeled to accurately describe real-world motion, but it involves lots of uncertainties in practice.<br>
These uncertainties are caused by various approximation processes while deriving mathematical dynamics models, unexpected increasing of system complexity while operating and disruption from outside the system or changes in the operating environment. And also, It happens because only important dynamics modes are intentionally modeled and the rest are not modeled. In some cases, it may be due to a lack of understanding of the system, too expensive and time-consuming to obtain a model, or due to special conditions.<br>

Given the uncertainty inherent in these mathematical dynamics models, the best modeling method is to use probabilities to express the uncertainty.<br>
So, the mathmatical dynamics model can be made as **[state-space equation](https://csh970605.github.io/posts/Kalman_Filter/#state-space-equation)**.<br>

However, Kalman filters should not be developed as continuous-time models as shown in the formula [1] but as [discrete-time models](https://csh970605.github.io/posts/Kalman_Filter/#discrete-time-model).<br>

Finally, the dynamics model will be expressed as :
<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/a43ae4a4-e53d-4fbd-ad31-da60c5332f9e">
</center>
<br>

The performance of Kalman filters depends on the accuracy of the system model. Therefore, in order to properly select and build a system model, you need to understand the system, state variables, parameters, etc.
<br><br>


### State-Space Equation

The state-space equation is expressed as follows:
<p align="center">
    <span>$\dot{x}(t)=f(x(t), u(t), w(t),t)$</span>
    <span style="float: right;">[1]</span>
</p>


where 
+ $x(t) \in \matbb{R}^{p}$ : A state variable. It is introduced to express the uncertainty inherent in the mathematical dynamic model.
+ $w(t) \in \matbb{R}^{m}$ : A process noise. It is called noise model that model the probabilitic feature of w(t).
+ $u(t) \in \matbb{R}^{q}$ : A input of system. It is also referred to as the "control input" and is assumed to be accurately known.
+ $f(\cdot,t)$ : Time-varying non-linear function that include system parameters.
+ $x(t)$ : At a given time, it is assumed to contain all the relevant information to describe the motion of the system.

<br><br>

### Discrete-Time Model


Discrete-time model is a special occlusion continuous-time model which measurements are sampled in discrete-time and system inputs are kept constant within sampling time. And it is expressed as a difference equation as follows :

<p align="center">
    <span>$x(k+1) = f(x(k), u(k), w(k), k)$</span>
    <span style="float: right;">[2]</span>
</p>

where
+ $k$ : Time index.
+ $x(k)$ : $x(kT)$, $T$ means sampling time.
<br>

It will be discussed later.

<br><br><br><br>

## Measurement Model

The Measurement Model is a mathematical expression of the functional relationship between measurement values, which are data acquired as output values from various sensors to observe the motion of the system, and state variables and parameters.<br>
Since the dynamics of system can be explained by using a change in time of state variables, sensor must measure the state variables. However, since measurement of sensor can be contaminated by noise or bias, sensor can not measure the exact values as it intend.<br>

To solve that problem, kalman filter devise a mathmetical tool to infer the unmeasured data by using contaminated measurement data.<br>
Measurement model assumes as measurements are collected at discrete time and expresses as follows:

<p align="center">
    <span>$z(k) = h(x(k),k) + v(k)$</span>
    <span style="float: right;">[3]</span>
</p>

where

+ $z(k)\in \matbb{R}^{p}$ : Measurements.
+ $v(k) \in \matbb{R}^{p}$ : Measurement noises. It is a variable for expressing the error inherent in the measurement as probability.
+ $h(x(k),k)$ : It is a non-linear function for expressing the functional relationship between state variables and outputs.

Finally, the measurement model will be expressed as :
<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/c9cd08a1-12eb-43e8-8134-b0fa84975671">
</center>

