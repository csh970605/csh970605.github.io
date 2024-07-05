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

UCMC is an advanced motion-based multi-object tracker consisting of five main methods compared to other trackers such as [SORT](https://csh970605.github.io/posts/SORT/).

The five main methods are:

+ Motion Modeling on Ground Plane

+ Camera Motion Compensation (CMC)

+ Mapped Mahalanobis Distance (MMD)

+ Process Noise Compensation (PNC)

+ Correlated Measurement Distribution (CMD)

Through these methods, UCMC solves the problem that other trackers can't handle when the camera is moving and boosts performance.

# Methology

<br><br>

## Motion Modeling on Ground Plane

To make observation and calculation more convenient, the choice was made to use the midpoint coordinates of the bottom edge of the bounding box in the image plane, projected onto the ground plane coordinates $x$ and $y$, as the observation vector. The state vector $\mathbf{x}$ is defined as :

<center>

$\mathbf{x} = [x, \dot{x}, y, \dot{y}]^{\top}$
</center>
where 

+ $\dot{x}$ : Rate of change of $x$.

+ $\dot{y}$ : Rate of change of $y$.

According to the [linear camera model](https://www.eecis.udel.edu/~jye/lab_research/ECCV/ECCV04.pdf), the mapping relationship between the ground plane coordinates $x$ and $y$ and the image plane coordinates $u$ and $v$ can be expressed as

<center>

$\begin{bmatrix}
u \\
v \\
1
\end{bmatrix} = A\frac{1}{\gamma}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}$
</center>

where

+ $\gamma$ : A scale factor

+ $A$ : A projection matrix that is the product of camera intrinsic and extrinsic parameters.
<br><br>

### Details

Here, I show the detailed information of the linear camera model that UCMC uses.<br>

UCMC derives an expression that relates three-dimensional world coordinates to two-dimensional pixel coordinates based on the geometric relationship of the linear camera model.

<center>

$\gamma_{0}\begin{bmatrix}
u\\
v\\
1
\end{bmatrix} = K_{i}K_{o} \begin{bmatrix}
x \\
y \\
z \\
1
\end{bmatrix}$
</center>

where 

+ $x, y, z$ : Three-dimensional coordinates.

+ $u, v$ : Pixel coordinates in the image.

+ $\gamma_{0}$ : A scale factor.

+ $K_{i}$ : The intrinsic matrix $\begin{bmatrix}
f_{x} & 0 & u_{0} & 0 \\
0 & f_{y} & v_{0} & 0 \\
0 & 0 & 1 & 0
\end{bmatrix}$.

+ $K_{o}$ : The extrinsic matrix $\begin{bmatrix}
R & T \\
0 & 1
\end{bmatrix}$.

Thus, the equation above can be expressed as:
<center>

$\gamma_{0}\begin{bmatrix}
u\\
v\\
1
\end{bmatrix} = K_{i}K_{o}\begin{bmatrix}
x \\
y \\
z \\
1
\end{bmatrix} = \begin{bmatrix}
\theta_{11} & \theta_{12} & \theta_{13} & \theta_{14} \\
\theta_{21} & \theta_{22} & \theta_{23} & \theta_{24} \\
\theta_{31} & \theta_{32} & \theta_{33} & \theta_{34} \\
\end{bmatrix} \begin{bmatrix}
x \\
y \\
z \\
1
\end{bmatrix}$
</center>

Let $z = z_{0}$ be a constant. Then, the equation above becomes:

<center>

$\begin{bmatrix}
u\\
v\\
1
\end{bmatrix} = \begin{bmatrix}
\theta_{11} & \theta_{12} & \theta_{13}z_{0} + \theta_{14} \\
\theta_{21} & \theta_{22} & \theta_{23}z_{0} + \theta_{24} \\
\theta_{31} & \theta_{32} & \theta_{33}z_{0} + \theta_{34} \\
\end{bmatrix} \frac{1}{\gamma} \begin{bmatrix}
x \\
y \\
1
\end{bmatrix} = A\frac{1}{\gamma}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}$
</center>

where

+ $A$ = $\begin{bmatrix}
\theta_{11} & \theta_{12} & \theta_{13}z_{0} + \theta_{14} \\
\theta_{21} & \theta_{22} & \theta_{23}z_{0} + \theta_{24} \\
\theta_{31} & \theta_{32} & \theta_{33}z_{0} + \theta_{34} \\
\end{bmatrix}$.

Let $b = A^{-1}\begin{bmatrix}
u \\
v \\
1
\end{bmatrix} = \begin{bmatrix}
b1 \\
b2 \\
b3
\end{bmatrix}$

$\therefore$ the physical coordinates can be calculated from pixel coordinates as:

<center>

$\begin{bmatrix}
x \\
y
\end{bmatrix} = \begin{bmatrix}
\frac{b_{1}}{b_{3}} \\
\frac{b_{2}}{b_{3}}
\end{bmatrix}$
</center>

When UCMC obtains the computation formula from pixel coordinates to ground coordinates, the errors in pixel coordinates will also be mapped to ground coordinates. Therefore, it becomes necessary to further explore the distribution of detection errors in the ground plane caused by the errors in the image plane.
<br><br>

## Camera Motion Compensation (CMC)

CMC is used to determine whether an object in two consecutive frames is the same object. Unlike traditional CMC, UCMC found that using the same CMC parameters in the same video sequence guarantees performance. UCMC models the target object's motion using a simple [Kalman filter](https://csh970605.github.io/posts/Kalman_Filter/) on the ground plane, instead of on the image plane as other trackers do. By doing so, it can effectively compensate for the motion estimation errors caused by camera movement through the PNC of the Kalman filter.

<br><br>

## Mapped Mahalanobis Distance (MMD)
While most other trackers use [IOU](https://csh970605.github.io/posts/IOU_Loss/), UCMC computes the projected probability distribution on the ground plane and utilizes the Mahalanobis distance to calculate the matching costs between targets. Calculating ground plane-based associations can effectively consider camera movement as noise within the motion model. It is also effective when the video is captured at low FPS. By employing the normalized Mahalanobis distance in ground plane modeling, the issue can be effectively addressed.<br>

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
\end{matrix}\right.$

$= G$

$= \begin{bmatrix}
\frac{\Delta t^{2}}{2} & 0 \\
\Delta t & 0 \\
0 & \frac{\Delta t^{2}}{2} \\
0 & \Delta t
\end{bmatrix}$

</center>
where

+ $\Delta x$ : The changes in position.

+ $\Delta v$ : The changes in velocity under the influence of noise.

+ $\sigma$ : The acceleration change due to camera motion.

+ $\Delta t$ : The time interval between two image frames.

$G$ captures the relationship between the changes in position and velocity caused by noise in each direction. For a two-dimensional Constant Velocity Model with a Kalman filter, the covariance matrix of the process noise can be :

<center>

$Q_{k} = G \cdot \text{diag}(\sigma_{x}, \sigma_{y}) \cdot G^{T}$
</center>

where

+ $\sigma_{x}$ : The process compensation factors along the $x$ axis. Handling the motion noise cause by camera movements of tilt.

+ $\sigma_{y}$ : The process compensation factors along the $y$ axis. Handling the motion noise cause by camera movements of rotation.

<br><br>

## Correlated Measurement Distribution (CMD)

In general, the measurement errors of detectors on the image plane follow an independent normal distribution, and their covariance matrix $R_{k}^{uv}$ is represented as follows:

<center>

$R_{k}^{uv} = \begin{bmatrix}
(\sigma_{m}w_{k})^{2} & 0 \\
0 & (\sigma_{m}h_{k})^{2}
\end{bmatrix}$
</center>

where

+ $\sigma_{m}$ : The detection noise factor as a hyperparameter.

+ $w_{k}$ : The detected width from the detector.

+ $h_{k}$ : The detected height from the detector.

However, since UCMC uses the measurement errors of detectors on the ground plane, we should calculate the mapped measurement noise matrix $R_{k}$ in the ground plane. $R_{k}$ is expressed as:

<center>

$R_{k} = CR_{k}^{uv}C^{T}$ 
</center>

where

+ $C = \begin{bmatrix}
\gamma a_{11} - a_{31} \gamma x & \gamma a_{12} - a_{32} \gamma x \\
\gamma a_{21} - a_{31} \gamma y & \gamma a_{22} - a_{32} \gamma y
\end{bmatrix}$

+ $a_{11} \ldots a_{32}$ : Elements of a projection matrix, which is the product of the camera intrinsic and extrinsic parameters, the inverse of matrix $A^{-1} = \begin{bmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33} \\
\end{bmatrix}$.

It is important to highlight that the mapped distribution exhibits a strong correlation since $R_{k}$ is non-diagonal.

<br><br>

### Details 

Take $A$ from the [Motion Modeling on Ground Plane](https://csh970605.github.io/posts/UCMC_Track/#details) and let the inverse matrix of $A$ be:

<center>

$A^{-1} = \begin{bmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
a_{31} & a_{32} & a_{33} \\
\end{bmatrix}$
</center>

Then, we obtain
<center>

$\left\{\begin{matrix}
x = \gamma(a_{11}u + a_{12}v + a_{13})\\
y = \gamma(a_{21}u + a_{22}v + a_{23})
\end{matrix}\right.$
</center>

where

+ $\gamma$ is defined as the reciprocal of $b_{3}$.

Next, taking the total derivative of the above equation:

<center>

$\left\{\begin{matrix}
dx = \gamma(a_{11}du + a_{12}dv) + b_{1}d\gamma \\
dy = \gamma(a_{21}du+a_{22}dv) + b_{2}d\gamma \\
d\gamma = -(\frac{1}{b_{3}})^{2}(a_{31}du + a_{32}dv)
\end{matrix}\right.$
</center>

Combine two equations( $\left\{\begin{matrix}
dx = \gamma(a_{11}du + a_{12}dv) + b_{1}d\gamma \\
dy = \gamma(a_{21}du+a_{22}dv) + b_{2}d\gamma \\
d\gamma = -(\frac{1}{b_{3}})^{2}(a_{31}du + a_{32}dv)
\end{matrix}\right.$, $\begin{bmatrix}
x \\
y
\end{bmatrix} = \begin{bmatrix}
\frac{b_{1}}{b_{3}} \\
\frac{b_{2}}{b_{3}}
\end{bmatrix}$
) it becomes:

<center>

$\begin{bmatrix}
dx \\
dy
\end{bmatrix} = \begin{bmatrix}
\gamma a_{11} - a_{31}\gamma x & \gamma a_{12} - a_{32}\gamma x \\
\gamma a_{21} - a_{31}\gamma x & \gamma a_{22} - a_{32}\gamma x \\
\end{bmatrix}\begin{bmatrix}
du \\
dv
\end{bmatrix}$
</center>

Assume that the measurement errors of detectors on the image plane follow an independent normal distribution, and their covariance matrix $R_{k}^{uv}$ is:

<center>

$R_{k}^{uv} = \begin{bmatrix}
(\sigma_{m}w_{k})^{2} & 0\\
0 & (\sigma_{m}h_{k})^{2}
\end{bmatrix}$ 
</center>

Then, the covariance matrix of measurement errors in the ground plane is:

<center>

$R_{k} = CR_{k}^{uv}C^{T}$
</center>

$\therefore$ we get the mapped measurement noise matrix $R_{k}$ in the ground plane.

# Pipeline of UCMC

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/63b7b2f1-2758-49bf-8876-8b99a1990518">
</center>

<br><br><br><br>

# Conclusion

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/823070a9-1378-4561-9506-68e7890643be">
</center>

where

+ HOTA (Higher Order Tracking Accuracy) : A metric designed to evaluate the accuracy and consistency of tracking. It measures higher-order tracking accuracy, considering various aspects of tracking performance. HOTA reflects not just detection accuracy but also the consistency of the tracks.<br>It emphasizes not only the accurate detection of multiple objects but also the reduction of incorrect tracks' persistence. This makes it a comprehensive measure of tracking performance.

+ IDF1 (ID F1 Score) : An F1 score based on the precision and recall of ID matches. It measures how accurately the tracked objects are matched with their IDs.<br>It evaluates whether objects are correctly identified and consistently tracked, making it useful for assessing the continuity and consistency of tracks.

+ MOTA (Multiple Object Tracking Accuracy) : A metric that evaluates the overall performance of multi-object tracking. It takes into account missed targets, false positives, and ID switches. Its equation is:
    <center>

    $\text{MOTA} = 1 - \frac{\text{False Negative} + \text{False Positive} + \text{ID Switches}}{\text{Total Ground Truth Objects}}$
    </center>
    It focuses on overall tracking performance, giving more weight to detection accuracy rather than the consistency of individual tracks.

+ AssA (Association Accuracy) : Measures the accuracy of associating objects correctly across frames. It evaluates whether objects are correctly linked from one frame to the next.<br>It emphasizes the correct linking of tracks, assessing whether objects are matched accurately between frames.

UCMC is a novel tracker in the sense that it uses methods such as MMD, CMD, etc. However, since it doesn't use features of tracking objects, it can't guarantee accuracy when the tracking objects are out of the camera angle. If UCMC uses features of the tracking objects, it can be a more precise tracker.