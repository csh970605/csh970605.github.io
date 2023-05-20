---
title: Arithmetic and Bitwise Operation
author: SeHoon
date: 2023-05-20 16:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Arithmetic Operation?

These are simple operations that allow us to directly add or subract to the color intensity.<br>
Calculates the per-element operation of two arrays. The overall effect is increasing or decreasing brightness. We can use Arithmetic Operation as:
**cv2.add(image, matrix)**.<br>
You should notice that do not add matrix like "image * matrix". You can get less or more values of added image than you expected.
<br><br><br>

# What is Bitwise Operation?
Bitwise Operation performs bit operation between two images. There is four kind of bitwise operator:<br>

+ cv2.bitwise_and(image1, image2, dst, mask)
+ cv2.bitwise_or(image1, image2, dst, mask)
+ cv2.bitwise_xor(image1, image2, dst, mask)
+ cv2.bitwise_not(image1, image2, dst, mask)


parameters:<br>
+ dst : output array that has the same size and type as input arrays.
+ mask : optional operation mask, 8-bit single channel array, that specifies elements of the output array to be changed.


<br><br><br><br>

# Implementation

[Arithmetic and Bitwise Operations](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/7.%20Arithmetic%20and%20Bitwise%20Operations.ipynb)
