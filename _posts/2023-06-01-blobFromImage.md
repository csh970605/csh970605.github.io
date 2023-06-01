---
title: blobFromImage
author: SeHoon
date: 2023-06-01 22:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is blobFromImage?
**cv2.dnn.blobFromImage(image, scalefactor, size, mean, swapRB, crop, ddepth) -> retval** creates 4-dimensional blob from image. Optionally resizes and crops image from center, subtract mean values, scales values by scalefactor, swap Blue and Red channels. where<br>

+ **image** : Input image.

+ **scalefactor** : Multiplier for images values.

+ **size** : Spatial size for output image.

+ **mean** : Scalar with mean values which are subtracted from channels. Values are intended to be in (mean-R, mean-G, mean-B) order if image has BGR ordering and swapRB is true.

+ **swapRB** : Flag which indicates that swap first and last channels in 3-channel image is necessary.

+ **crop** : Flag which indicates whether image will be cropped after resize or not.

+ **ddepth** : Depth of output blob. Choose CV_32F or CV_8U.

+ **retval** : 4-dimensional [Mat](https://docs.opencv.org/4.x/d3/d63/classcv_1_1Mat.html) with NCHW dimensions order.

