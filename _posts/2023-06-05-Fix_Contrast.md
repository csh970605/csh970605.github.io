---
title: Fix Contrast with Histogram Equalization
author: SeHoon
date: 2023-06-05 20:09:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Histogram Equalization?

Histogram Equalization adjusts the dynamic range of an image, making it spread more evenly accross the intensity distribution in order to improve contrast.

<center>
Cumulative distiribution function(CDF) and histogram of the original image.<br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/98525f3f-950f-4984-aefe-e3d41dbf4d0d" width=500>
<br><br>

Cumulative distiribution function(CDF) and histogram of the histogram equalized image.
<br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/f6c0183f-7466-4791-9607-ec7bc88f3d6a" width=500>
</center>

<br><br><br><br>

# How to perform Histogram Equalization?

We can do histogram equalization simply using **cv2.equalizeHist(src, dst)**.<br>
Note that when using a color image, histogram equalization must be performed on all channels of the image and merged again.
<br><br><br><br>


# Implementation

+ [Fix Contrast with Histogram Equalization](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/38-2.%20Fix%20Contrast%20with%20Histogram%20Equalization.ipynb)