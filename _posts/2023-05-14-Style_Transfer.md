---
title: Style Transfer
author: SeHoon
date: 2023-05-13 21:47:00 +0900
categories: [Vision Machine Learning, VML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Style Transfer?
As you can see in the word "style transfer", it converts the style of an image like:
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/88be8987-c2e2-4082-8d36-eca6b0397495" width=800>
</center>
<br><br>

Style transfer consists of several [convolutional layers](https://csh970605.github.io/posts/CNN/) and [pooling layers](https://csh970605.github.io/posts/Pooling/).
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/1f639688-5bb3-46a0-bb00-875be79cde2c" width=500>
</center>
<br><br>

+ The orange arrow : The output of the original image.
+ The blue arrow : The output representing the style of the image. That is, it indicates the style of the image.
<br><br>
<br>

# Implementation

+ [Change painting style](https://github.com/csh970605/Computer-Vision-Masterclass/tree/main/Section%2011): I used VGG19 to implement it.

+ [Neural Style Transfer with OpenCV](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/34.%20Neural%20Style%20Transfer%20with%20OpenCV.ipynb): I used ECCV16 and t7 PyTorch models to implement it.


