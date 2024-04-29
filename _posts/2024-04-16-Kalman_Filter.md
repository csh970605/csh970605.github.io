---
title: Kalman Filter
author: SeHoon
date: 2024-04-16 10:01:30 +0900
categories: [Papers, DeepLearning]
tags: [Papers, DeepLearning, MultiObjectTracking]
math: true
mermaid: true
---

# Kalman Filter

Kalman Filter is an estimator using the state-space equation of the system and it is an optimal data processing algorithm with a recursive structure.<br>
Initially, Kalman Filters could only be used in linear systems, and a method that could be applied to nonlinear systems was devised later.<br>
Since Kalman Filter is an estimator, we should know what the estimator is. <br>
Estimator is an algorithm that estimates an unknown quantity from available informations. And the unkown quantities are usually expressed as **[state variables]()** and **[system parameters]()**.

<br><br>

## State variables

State variables are variables that can be changed extremly over time by external forces or actions.
<br><br>


## System parameters

System parameters are variables that do not change or change slowly over time. However, if necessary, the system parameters are sometimes considered as state variables. For example, if the parameter is the unknown quantity to be estimated, the parameter is regarded as a state variable.