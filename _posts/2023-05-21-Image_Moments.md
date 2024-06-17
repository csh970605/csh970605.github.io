---
title: Image Moments
author: SeHoon
date: 2023-05-21 14:53:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Image Moments?
Image moment is a certain particular weighted average (moment) of the image pixels' intensities, or a function of such moments, usually chosen to have some attractive property or interpretation.<br>
In openCV, it is used as<br>
**cv2.moments(cv2.contourArea([contours[i]](https://csh970605.github.io/posts/Contours/)))**<br>
Through this method, we can get 
<center>

$M\ =\ \begin{cases}zero\ order\ moments\ :\ m_{00}\\
first\ moments\ :\ m_{10},\ m{01}\\
secnod\ moments\ :\ m_{11},\ m_{20},\ m_{02}\\
third\ moments\ :\ mu_{11},\ mu_{20},\ mu_{02}\\
second\ central\ moments\ :\ mu_{11},\ mu_{20},\ mu_{02}\\
third\ central\ moments\ :\ mu_{21},\ mu_{12},\ mu_{30},\ mu_{03}\\
second\ normalized\ central\ moments\ :\ nu_{11},\ nu_{20},\ nu_{02}\\
third\ normalized\ central\ moments\ :\ nu_{21},\ nu_{12},\ nu_{30},\ nu_{03},\  \end{cases}$
</center>

<br>
By the output, we can calculate <br>

+ Mass center($ \bar{x},\ \bar{y} $) : $ \bar{x}\ =\ \frac{m_{10}}{m_{00}},\ \bar{y}\ =\ \frac{m_{01}}{m_{00}}$
+ Spatial moments : $ m_{ij}\ =\ \sum_{x,y}(array(x,y)*x^{i}y^{j}) $
+ Central moments : $ mu{ij}\ =\ \sum_{x,y}(array(x,y)*(x-\bar{x})^{i}(y-\bar{y}^{j})) $
+ Normalized central moments : $ nu_{ij}\ =\ \frac{mu_{ij}}{m_{00}^{\frac{i+j}{2}+1}} $

<br><br><br><br>

# Implementation
[Moments, Sorting, Approximating & Matching Contours](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/12.%20Moments%2C%20Sorting%2C%20Approximating%20and%20Matching%20Contours.ipynb)
