---
title: Object Tracking with Optical Flow
author: SeHoon
date: 2023-05-25 22:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Optical Flow?
Optical flow is the pattern of apparent motion of image objects between two consecutive frames caused by the movemement of object or camera. It is 2D vector field where each vector is a displacement vector showing the movement of points from first frame to second.<br><br>

There are two ways to track object with optical flow.
+ The Lucas-Kanade Optical Flow : Computes the optical flow for a sparse feature set.

+ Gunner Farneback Optical Flow : Computes the optical flow for all the points in the frame.

<br><br><br><br>

## Steps of The Lucas-Kanade Optical Flow
---
<br>

1. Find initial corner location<br>
It can be done by **cv2.goodFeaturesToTrack(image, maxCorners, qualityLevel, minDistance, mask, blockSize)** where<br>

    + image : 8-bit or floating-point 32-bit, single-channel image.
    
    + maxCorners : Maximum number of corners to return. If there are more corners than are found, the strongest of them is returned.

    + qualityLevel : Parameter characterizing the minimal accepted quality of image corners. The parameter value is multiplied by the best corner quality measure. <br>
    For example, if the best corner has the quality measure = 1500, and the qualityLevel=0.01 , then all the corners with the quality measure less than 15 are rejected.

    + minDistance : Minimum possible Euclidean distance between the returned corners.

    + immaskage : Specifies the region in which the corners are detected.

    + blockSize : Size of an average block for computing a derivative covariation matrix over each pixel neighborhood.
    <br><br>

2. Calculate optical flow<br>
It can be done by **cv2.calcOpticalFlowPyrLK(prevImg, nextImg, prevPts, nextPts, winSize, maxLevel, criteria) -> nextPts, status, err** where<br>

    +  prevImg : 8-bit input image.

    +  nextImg : 8-bit input image.

    +  prevPts : Vector of 2D points for which the flow needs to be found

    +  nextPts : Output vector of 2D points containing the calculated new positions of input features in the second image

    +  winSize : Size of the search window at each pyramid level.

    +  maxLevel : maximal pyramid level number. If set to 0, pyramids are not used (single level), if set to 1, two levels are used, and so on

    +  criteria : Stop criteria for the iterative search algorithm. It has three parameters as an input which is:<br>

        + type : 

            + cv2.TERM_CRITERIA_EPS = Stop iteration until reach at the epsilon.

            + cv2.TERM_CRITERIA_MAX_ITER = Stop iteration until reach at the max_iter.

            + cv2.TERM_CRITERIA_EPS + cv2.TERM_CRITERIA_MAX_ITER = Stop iteration until one of the two conditions is fulfilled.

        + max_iter : Max iteration number.

        + epsilon : Accuracy.
<br><br>

    +  status : Output status vector. Each element of the vector is set to 1 if the flow for the corresponding features has been found, otherwise, it is set to 0.

    +  err : Output vector of errors.

<br><br>

3. Get detected points from prevImg and nextImg.<br>
It can be done by

```py
detected_prev = prevPts[status==1]
detected_next = nextPts[status==1]
```

<br><br><br><br>

## Steps of Gunner Farneback Optical Flow

1. 