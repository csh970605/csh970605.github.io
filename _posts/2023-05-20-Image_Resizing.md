---
title: Image Resizing, Scaling
author: SeHoon
date: 2023-05-20 15:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is image Resizing?

In image resizing, we just change the width and height. To do image Resizing, we can use<br>
**cv2.resize(image, dsize(output imagesize), x_scale, y_scale, interpolation)**<br>
If dsize is None, the output image will be calculated as a function of scaling using x&y scale.

<br><br>

## List of Interpolation

+ **INTER_NEAREST** : a nearest-neighbor interpolation. the fastest, the worst quality.
+ **INTER_LINEAR** : a bilinear interpolation (used by default). the best efficiency.
+ **INTER_AREA** : resampling using pixel area relation. It may be a preferred method for image decimation, as it gives moire’-free results. But when the image is zoomed, it is similar to theINTER_NEAREST method. 
+ **INTER_CUBIC** : a bicubic interpolation over 4×4 pixel neighborhood.more slower than INTER_LINEAR, more quality than it.
+ **INTER_LANCZOS4** : a Lanczos interpolation over 8×8 pixel neighborhood. the slowest, the best quality.
<br><br>

# What is image scaling?

In scaling we change the size, but keep the width to height ratio constant. To do image scaling, we can use<br>
**cv2.resize(image, dsize=None, x_scale, y_scale, interpolation)**<br>
<br><br><br>

# Implementation

+ [Resizing, scaling, cropping](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/6.%20Scaling%2C%20Re-sizing%2C%20Interpolations%20and%20Cropping.ipynb)

