---
title: Finding Corners
author: SeHoon
date: 2023-05-22 16:36:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# How to Detect Corners?
A corner is a point whose local neighborhood stands in two dominant and different edge directions. In other words, a corner can be interpreted as the junction of two edges, where an edge is a sudden change in image brightness.
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/4faeea3c-3d0d-4281-abf2-37465b81d1b9" width=800>
</center>
<br><br>

And there is two algorithms in openCV which is :<br>
+ **cv2.cornerHarris(src, blockSize, ksize, k) -> dst** where:
    + src : Should be grayscale and float32 type.
    + blockSize : The size of neighborhood considered for corner detection
    + ksize : Aperture parameter of Sobel derivative used.
    + k : Harris detector free parameter in the equation $ dst(x,y)\ =\ detM^{(x,y)}\ -\ k(trM^{(x,y)})^{2}$ where $M^{(x,y)}$ over a blockSize * blockSize neighborhood.
    + dst : Array of corner locations (x,y)
    <br>
    <br>

+ **cv2.goodFeaturesToTrack(image, maxCorners, qualityLevel, minDistance, mask, blockSize) -> dst** where:
    + image : 8-bit or floating-point 32-bit, single-channel image.
    + maxCorners : Maximum number of corners to return. If there are more corners than are found, the strongest of them is returned.
    + qualityLevel : Parameter characterizing the minimal accepted quality of image corners. The parameter value is multiplied by the best corner quality measure (smallest eigenvalue). The corners with the quality measure less than the product are rejected.<br>
    For example, if the best corner has the quality measure = 1500, and the qualityLevel=0.01 , then all the corners with the quality - - measure less than 15 are rejected.
    + minDistance : Minimum possible Euclidean distance between the returned corners.
    + mask : Optional region of interest. Default = empty.
    + blockSize : Size of an average block for computing a derivative covariation matrix over each pixel neighborhood. Default = 3
    + dst : Array of corner locations (x,y)
<br><br><br><br>

## Result
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/12ee02b2-1491-4c37-a938-a23276bb372c" width=500>
</center>
<br><br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/2417450d-8ff3-4766-bd56-3f9c660c4cae" width=500>
</center>
<br><br><br><br>

# Implementation
+ [Finding Corners](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/15.%20Finding%20Corners.ipynb)