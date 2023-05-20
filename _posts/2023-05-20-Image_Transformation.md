---
title: Image Transformation
author: SeHoon
date: 2023-05-20 15:10:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Image Transformation?

Image transformation performs two role:
+ Image translation : image translation simply shifts the position of an image. 
+ Image rotation : image rotation makes the image rotate by $\theta$.
<br><br><br>

## Image translation
---
<br>

To do the image translation, we can use <br>
**cv2.warpAffine(image, T, (width, height))** where 

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/18925822-0ff2-47f0-8b65-4691fb4b091d" width=500>
</center>
<br><br>
<br>

## Image rotation
---
<br>

To do the image rotation, we can use <br>
**cv2.getRotationMatrix2D(rotation_center_x, rotation_centery, angle of rotation, scale)** where
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/4a215d45-34ca-4ff8-9dde-134815f38e75" width=500>
</center>
<br><br>
<br><br>

# Implementation

[Image transformation](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/5.%20Transformations%20-%20Translations%20and%20Rotations.ipynb)


<center>
<img src="" width=500>
</center>
<br><br>