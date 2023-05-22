---
title: Line & Circle & Blob Detection
author: SeHoon
date: 2023-05-21 20:26:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# Line detection
Line detection is performed by two methods<br>
+ Hough Lines: **cv2.HoughLines(image, rho, theta, threshold)** where:<br>
    + image : binarized/thresholded image
    + rho : Distance resolution of the accumulator in pixels.
    + theta : Angle resolution of the accumulator in radians.
    + threshold : the minimum vote for it to be considered a line.



+ Probabilistic Hough Lines :  **cv2.HoughLinesP(image, rho, theta, threshold, minLineLength, maxLineGap)** where:<br>
    + image : Ninarized/thresholded image
    + rho : Distance resolution of the accumulator in pixels.
    + theta : Angle resolution of the accumulator in radians.
    + threshold : The minimum vote for it to be considered a line.
    + minLineLength : The minimum pixels of line. default = 0.
    + maxLineGap : The gap of pixels between lines. default = 0.<br><br><br><br>

## Result
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/58068d82-ac5d-4340-9f74-e4b6211f1cf7" width=500>
</center>
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0cf455bd-e5d9-4db7-a107-97a01110d924" width=500>
</center>


<br><br><br><br>

# Circle detection
Line detection is performed by:<br>
**cv2.HoughCircles(image, method, dp, minDist, param1, param2, minRadius, maxRadius)** where:<br>

+ image : Binarized/thresholded image.
+ method : Detection method.
+ dp : Inverse ratio of accumulator resolution.
+ minDist : The minimum distance between the center of detected circles.
+ param1 : Gradient value used in the edge detection. default = 100.
+ param2 : Accumulator threshold for the "method" (lower allows more circles to be detected (false positives)). default = 100.
+ minRadius : Limits the smallest circle to this size (via radius). default = 0.
+ maxRadius : Limits the biggest circle to this size (via radius). default = 0.
<br><br><br><br>


## Method of HoughCircles
---
<br>

+ cv2.HOUGH_GRADIENT
+ cv2.HOUGH_GRADIENT_ALT
<br><br><br><br>


## Result
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/6db238fe-dc21-44d4-824d-7f498b5d2694" width=500>
</center>

<br><br><br><br>

# Blob Detection
Blob detection is performed by:<br>
**cv2.drawKeypoints(image, keypoints, outImage, color, flags)** where:<br>

+ image : The image detected by **cv2.SimpleBlobDetector.create()**
+ keypoints : Keypoints from the source image.
+ outImage : Output image. Its content depends on the flags value defining what is drawn in the output image.
+ color : Color of keypoints. default = Scalar::all(-1)
+ flags : Flags setting drawing features. Possible flags bit values are defined by DrawMatchesFlags. default = DRAW_MATCHES_FLAGS_DEFAULT
<br><br><br><br>

## Flags of Blob detections
---
<br>

+ DRAW_MATCHES_FLAGS_DEFAULT
+ DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS
+ DRAW_MATCHES_FLAGS_DRAW_OVER_OUTIMG
+ DRAW_MATCHES_FLAGS_NOT_DRAW_SINGLE_POINTS

<br><br><br><br>



## Result
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/137c29d8-c50e-4192-8b64-642003f3713e" width=500>
</center>
<br><br><br><br>

# Counting Blobs

We can count blobs by:<br>
**cv2.SimpleBlobDetector.Params()**<br>
We can set the filtering parameters of simpleBlobDetector. Let's see what the parameters are in it.<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/e636914d-928c-4f09-8fc6-89105bfe89af" width=500>
</center>
<br><br>

We can set those parameters by:

```py
params = cv2.SimpleBlobDetector.Params()

# Set Threshold filtering parameters
params.minThreshold = 10
params.maxThreshold = 200

# Set Area filtering parameters
params.filterByArea = True
params.minArea = 100

# Set Circularity filtering parameters
params.filterByCircularity = True 
params.minCircularity = 0.9

# Set Convexity filtering parameters
params.filterByConvexity = False
params.minConvexity = 0.2
    
# Set inertia filtering parameters
params.filterByInertia = True
params.minInertiaRatio = 0.01

# Create a detector with the parameters
detector = cv2.SimpleBlobDetector.create(params)
    
# Detect blobs
keypoints = detector.detect(image)
```

<br><br><br><br>

## Result
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/61049a83-9237-4397-a8ba-2d08da48b596" width=500>
</center>

<br><br><br><br>


# Implementation
+ [Line, Circle and Blob Detection](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/13.%20Line%2C%20Circle%20and%20Blob%20Detection.ipynb)<br>
+ [Counting Circles, Ellipses and Finding Waldo](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/14.%20Counting%20Circles%2C%20Ellipses%20and%20Finding%20Waldo%20with%20Template%20Matching.ipynb)

