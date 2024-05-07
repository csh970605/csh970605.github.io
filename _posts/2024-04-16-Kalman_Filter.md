---
title: Kalman Filter
author: SeHoon
date: 2024-04-16 10:01:30 +0900
categories: [Papers, Mathmatics]
tags: [Papers, Mathmatics, MultiObjectTracking]
math: true
mermaid: true
---

# Kalman Filter

Kalman Filter is an **[estimator](https://csh970605.github.io/posts/Kalman_Filter/#estimator)** using the state-space equation of the system and it is an optimal data processing algorithm with a recursive structure.<br>
Initially, Kalman Filters could only be used in linear systems, and a method that could be applied to nonlinear systems was devised later.<br>

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

+ Filtering : Infer present state variables based on measurement data from the past to the future. It is used to estimate the state of the system by post-processing measurement data accumulated in a test or experiment.<br><br>

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

<br><br>

## System Dynamics Model

One of the available information, the System dynamics model, is a mathematical model that descirbes how excercise properties of dynamic systems change over time.<br>
System exercise model are built to describe specific state variables and parameters of interest and interrelationships between system inputs and outputs using Newton's laws of motion, empirical insights, experiments, etc.<br>

System dynamics model needs to be modeled to accurately describe real-world motion, but it involves lots of uncertainties in practice.<br>
These uncertainties are caused by various approximation processes while deriving mathematical dynamics models, unexpected increasing of system complexity while operating and disruption from outside the system or changes in the operating environment. And also, It happens because only important system dynamics modes are intentionally modeled and the rest are not modeled. In some cases, it may be due to a lack of understanding of the system, too expensive and time-consuming to obtain a model, or due to special conditions.<br>

Given the uncertainty inherent in these mathematical dynamics models, the best modeling method is to use probabilities to express the uncertainty.<br>
So, the mathmatical dynamics model can be made as state-space equation like:

<p align="center">
    <span>$\dot{x}(t)=f(x(t), u(t), w(t),t)$</span>
    <span style="float: right;">[1]</span>
</p>


where 
+ $x(t) \in R^{p}$ : A state variable. 
+ $w(t) \in R^{m}$ : A process noise.
+ $u(t) \in R^{q}$ : A input of system.


<br><br>

