---
title: Edge detecting
author: SeHoon
date: 2023-05-21 09:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Edge Detecting?
As you can see in the word "Edge detecting", it can detect edge by<br>
**cv2.Canny(image, threshold1, threshold2)**<br>
where:
+ image = 8-bit input image.
+ threshold1 = any value below threshold1 is considered not to be an edge. 
+ threshold2 = any gradient value larger than threshold2 is considered to be an edge.
Then how about the values between threshold1 and threshold2? they are considered as edges or non-edges based on how their intensities are connected.

<br><br><br>

# Modifing Edges
We can modify the thickness of edges by four ways:
+ Erosion = Removes pixels at the boundaries of objects in an image. It can used as<br>
**cv2.erode(src, kernel, anchor, iterations)** where<br>

    + src = input image; the number of channels can be arbitrary.
    + kernel = structuring element used for erosion; if element=Mat(), a 3 x 3 rectangular structuring element is used.
    + anchor = position of the anchor within the element; default value (-1, -1) means that the anchor is at the element center.
    + iterations = number of times erosion is applied.
    <br><br>

 + Dilation = Adds pixels to the boundaries of objects in an image. It can used as<br>
**cv2.dilate(src, kernel, anchor, iterations)** where<br>

    + src = input image; the number of channels can be arbitrary.
    + kernel = structuring element used for erosion; if element=Mat(), a 3 x 3 rectangular structuring element is used.
    + anchor = position of the anchor within the element; default value (-1, -1) means that the anchor is at the element center.
    + iterations = number of times erosion is applied.
    <br><br>

+ Morphology = It is a morphological operation used for removing noise, filling holes, and splicing broken lines. Morphological operations can be applied to binary images consisting only of black and white. It can used as<br>
**cv2.morphologyEx(src, op, kernel, anchor, iterations)** where<br>

    + src = input image; the number of channels can be arbitrary.
    + op = Type of a morphological operation.
    + kernel = structuring element used for erosion; if element=Mat(), a 3 x 3 rectangular structuring element is used.
    + anchor = position of the anchor within the element; default value (-1, -1) means that the anchor is at the element center.
    + iterations = number of times erosion is applied.

<br><br><br>


## Types of morphological operations.
---
<br>

+ MORPH_ERODE = Same as eroding
+ MORPH_DILATE = Same as dliting
+ MORPH_OPEN = Erosion followed by dilation
+ MORPH_CLOSE = Dilation followed by erosion
+ MORPH_GRADIENT = Boundary pixels obtained by subtracting the dilated image from the eroded image.
+ MORPH_TOPHAT = Original image - morph_open image.
+ MORPH_BLACKHAT = Morph_close - original image.
+ MORPH_HITMISS = It applies one or more structuring elements to an input image to obtain the output image. Because of that, MORPH_HITMISS is often used to detect corner of image.

<br><br><br><br>

# Implementation
[Dilation, Erosion and Edge Detection](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/10.%20Dilation%2C%20Erosion%20and%20Edge%20Detection.ipynb)
