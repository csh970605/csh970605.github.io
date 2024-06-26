---
title: UCMC Track
author: SeHoon
date: 2024-06-26 10:00:30 +0900
categories: [Papers, Tracking]
tags: [Papers, Tracking, MultiObjectTracking]
math: true
mermaid: true
---

# [Multi-Object Tracking with Uniform Camera Motion Compensation (UCMC)](https://arxiv.org/pdf/2312.08952)

UCMC is an advanced motion-based multi-object tracker consisting of four main methods compared to other trackers such as [SORT](https://csh970605.github.io/posts/SORT/).

The four main methods are:

+ Camera Motion Compensation (CMC)

+ Mapped Mahalanobis Distance (MMD)

+ Process Noise Compensation (PNC)

+ Correlated Measurement Distribution (CMD)

Through these methods, UCMC solves the problem that other trackers can't handle when the camera is moving and boosts performance.

# Methology

<br><br>

## Camera Motion Compensation (CMC)

CMC is used to determine whether an object in two continuous frames is the same object or not. Unlike traditional CMC, UCMC found that using the same CMC parameters in the same video sequence can guarantee performance. UCMC models the target object's motion using a simple [Kalman filter](https://csh970605.github.io/posts/Kalman_Filter/) on the ground plane, instead of on the imaging plane as other trackers do. By doing so, it can effectively compensate for the motion estimation errors caused by camera movement through the PNC of the Kalman filter.

<br><br>

## Mapped Mahalanobis Distance (MMD)
While most other trackers use [IOU](https://csh970605.github.io/posts/IOU_Loss/), UCMC computes the projected probability distribution on the ground plane and utilizes the Mahalanobis distance to calculate the matching costs between targets. Calculating ground plane-based association can effectively consider camera movement as noise within the motion model. It is also effective when the video is captured at low FPS. By employing the normalized Mahalanobis distance in ground plane modeling, it can be effectively addressed.<br>

The calculation of MMD between track state and measurement has three steps:

1. Calculate Residual

2. Calculate Residual Covariance Matrix

3. Calculate Normalized Mahalanobis Distance

During the calculation process of Normalized Mahalanobis Distance, UCMC uses the normalized Mahalanobis distance, incorporating the logarithm of the determinant of the measurement covariance matrix. This ensures that data association decisions are not solely based on the discrepancies between measurements and predictions but also holistically consider the accuracy and uncertainty of measurements.
<br><br>

### Calculate Residual

<center>

$\epsilon = z - H\hat{x}$
</center>

where

+ $z$ : Mapped measurement on the ground plane.

+ $H$ : Observation matrix.

+ $\hat{x}$ : Predicted track state.

<br><br>

### Calculate Residual Covariance Matrix

<center>

$S = HPH^{T} + R_{k}$
</center>

where

+ $H$ : Observation matrix.

+ $P$ : Predicted covariance matrix.

+ $R_{k}$ : Mapped measurement noise covariance matrix.

<br><br>

### Calculate Normalized Mahalanobis Distance

<center>

$D = \epsilon^{T}S^{-1}\epsilon + \ln (\det S)$
</center>
where

+ $\epsilon$ : Residual matrix.

+ $S$ : Residual covariance matrix.

<br><br>

## Process Noise Compensation (PNC)

Assuming that the camera's motion-induced acceleration is the source of noise, UCMC can represent it through the system motion model as:

<center>

$\left\{\begin{matrix}
\Delta x = \frac{\sigma \times (\Delta t)^2}{2}\\ \Delta v = \sigma \times \Delta t
\end{matrix}\right$

</center>

<br><br>

## Correlated Measurement Distribution (CMD)

<br><br><br><br>

# Pipeline of UCMC

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/63b7b2f1-2758-49bf-8876-8b99a1990518">
</center>

<br><br><br><br>

# Conclusion