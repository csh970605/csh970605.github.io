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

    +  prevPts : Vector of 2D points for which the flow needs to be found.

    +  nextPts : Output vector of 2D points containing the calculated new positions of input features in the second image.

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
---
<br>

1. Computes the dense optical flow using **cv2.calcOpticalFlowFarneback(prev, next, flow, pyr_scale, levels, winsize, iterations, poly_n, poly_sigma, flags) -> flow** where<br>

    + prev : Input image.
    
    + next : Input image.

    + flow : Computed flow image. Output.

    + pyr_scale : Specifying the image scale (<1) to build pyramids for each image.<br>
    For example, pyr_scale=0.5 means a classical pyramid, where each next layer is twice smaller than the previous one.

    + levels : Number of pyramid layers including the initial image.<br>
    For example, levels=1 means that no extra layers are created and only the original images are used.

    + winsize : Averaging window size. Larger values increase the algorithm robustness to image noise and give more chances for fast motion detection, but yield more blurred motion field.

    + iterations : Number of iterations the algorithm does at each pyramid level.

    + poly_n : Size of the pixel neighborhood used to find polynomial expansion in each pixels. Larger values mean that the image will be approximated with smoother surfaces, yielding more robust algorithm and more blurred motion field.<br>
    Usually, it would be 5 or 7.

    + poly_sigma : Standard deviation of the Gaussian that is used to smooth derivatives used as a basis for the polynomial expansion. <br>
    For example, poly_n=5, you can set poly_sigma=1.1. poly_n=7, a good value would be poly_sigma=1.5.

    + flags : Operation flags that can be a combination where :<br>

        + OPTFLOW_USE_INITIAL_FLOW : Uses the input flow as an initial flow approximation.

        + OPTFLOW_FARNEBACK_GAUSSIAN : uses the Gaussian **winsize * winsize** filter instead of a box filter of the same size for optical flow estimation.

<br><br>

2. Calculate the magnitude (speed) and angle of motion using **cv2.cartToPolar(x, y) -> magnitude, angle** where<br>

    + x : flow[..., 0] that obtained in step 1.

    + y : flow[..., 1] that obtained in step 1.

<br><br>

3. Calculate the color to reflect speed and angle.<br>

```py
hsv[..., 0] = angle * (180 / (np.pi / 2))
hsv[..., 1] = 255
hsv[..., 2] = cv2.normalize(magnitude, None, 0, 255, cv2.NORM_MINMAX)

final_image = cv2.cvtColor(hsv, cv2.COLOR_HSV2BGR)
```


<br><br><br><br>


# Implementation

+ [Object Tracking with Optical Flow](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/25.%20Object%20Tracking%20with%20Optical%20Flow.ipynb)