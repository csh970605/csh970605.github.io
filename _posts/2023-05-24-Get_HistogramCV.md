---
title: Get histogram in CV
author: SeHoon
date: 2023-05-24 22:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# How to get histogram in CV?

We can get histogram simply by using:<br>
**cv2.calcHist(images, channels, mask, hitSize, ranges)** where,<br>
+ images : The source image of type uint8 or float32. it should be given in square brackets, ie, "[img]".
+ channels : Also given in square brackets. It is the index of channel for which we calculate histogram. For example, if input is grayscale image, its value is [0]. For color image, you can pass [0], [1] or [2] to calculate histogram of blue, green or red channel respectively.
+ mask : To find histogram of full image, it is given as "None". But if you want to find histogram of particular region of image, you have to create a mask image for that and give it as mask.
+ hitSize : Array of histogram sizes in each dimension.
+ ranges : Array of the dims arrays of the histogram bin boundaries in each dimension. Normally, it is [0,256].
<br><br><br><br>

## Result
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/dfcf17c4-ce8d-4066-b7a0-acf05ff6f170" width=500>
<br><br>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/72653336-a9a3-44be-bc60-d9e37f4deb7f" width=500>
</center>


<br><br><br><br>

# Obtain the dominant colors in image by [K-Means Clustering](https://csh970605.github.io/posts/KMeans_Clustering/)

<br><br><br><br>

## Result
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/dfcf17c4-ce8d-4066-b7a0-acf05ff6f170" width=500>
<br><br>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/e0efabcb-e60b-407f-ba71-94fca5ab10f1" width=500>
</center>
<br><br><br><br>

# Implementation

+ [K-Means Clustering & Histograms](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/19.%20Histograms%20and%20K-Means%20Clustering%20for%20Dominant%20Colors.ipynb)