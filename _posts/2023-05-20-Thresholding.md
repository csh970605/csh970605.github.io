---
title: Thresholding in image
author: SeHoon
date: 2023-05-20 19:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Thresholding in image?
As you can see in thresholding, in openCV, thresholding changes the values of pixels based on a specific value. It can be used as:<br>
+ **cv2.threshold(src, thresh, maxval, type)** where<br>
    + src = input array (multiple-channel, 8-bit or 32-bit floating point).
    + thresh = threshold value.
    + maxval = maximum value to use with the THRESH_BINARY and THRESH_BINARY_INV thresholding types.
    + type = thresholding type.

+ **cv2.adaptiveThreshold(src, maxValue, adaptiveMethod, thresholdType, blockSize, C)** where<br>
    + src = Source 8-bit single-channel image.
    + maxValue = Non-zero value assigned to the pixels for which the condition is satisfied. See the details below.
    + adaptiveMethod = Adaptive thresholding algorithm to use.
    + thresholdType = Thresholding type that must be either THRESH_BINARY or THRESH_BINARY_INV .
    + blockSize = Size of a pixel neighborhood that is used to calculate a threshold value for the pixel: 3, 5, 7, and so on.
    + C = Constant subtracted from the mean or weighted mean. Normally, it is positive but may be zero or negative as well.

<br><br>

## Types of thresholding
---
<br>

+ THRESH_BINARY : $dst(x, y) = \begin{cases}maxval\ if\ src(x,y)\ >\ thresh \\ 0\ \ otherwise \end{cases} $
+ THRESH_BINARY_INV : $dst(x, y) = \begin{cases}0\ if\ src(x,y)\ >\ thresh \\ maxval\ \ otherwise \end{cases} $
+ THRESH_TRUNC : $dst(x, y) = \begin{cases}threshold\ if\ src(x,y)\ >\ thresh \\ xrc(x,y)\ \ otherwise \end{cases} $
+ THRESH_TOZERO : $dst(x, y) = \begin{cases}src(x,y)\ if\ src(x,y)\ >\ thresh \\ 0\ \ otherwise \end{cases} $
+ THRESH_TOZERO_INV : $dst(x, y) = \begin{cases}0\ if\ src(x,y)\ >\ thresh \\ src(x,y)\ \ otherwise \end{cases} $

<br><br>

## Adaptive Method
---
<br>

+ ADAPTIVE_THRESH_MEAN_C : the threshold value T(x,y) is a mean of the blockSize×blockSize neighborhood of (x,y) minus C.
+ ADAPTIVE_THRESH_GAUSSIAN_C :the threshold value T(x,y) is a weighted sum of the blockSize×blockSize neighborhood of (x,y) minus C . 

<br><br><br><br>

# Implementation

+ [Thresholding, Binarization & Adaptive Thresholding](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/9.%20Thresholding%2C%20Binarization%20_%20Adaptive%20Thresholding.ipynb)