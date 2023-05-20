---
title: Blurring and Denoising
author: SeHoon
date: 2023-05-20 16:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Blurring?

As you can see the naime Blurring, it blurrs image by:<br>

+ Convolution : It uses [convolution layer](https://csh970605.github.io/posts/CNN/) in order to get blurred images. It can be used as:<br>
**cv2.filter2D(src, ddepth, kernel)** where: <br>
    + src = input image
    + ddepth = desired depth of the destination image.
    + kernel = 	convolution kernel (or rather a correlation kernel), a single-channel floating point matrix; if you want to apply different kernels to different channels, split the image into separate color planes using split and process them individually.

+ Regular : Averaging done by convolving the image with a normalized box filter. This takes the pixels under the box and replaces the central element. Box size needs to odd and positive  It can be used as:
**cv2.blur(src, ksize)** where:<br>
    + src = input image; it can have any number of channels, which are processed independently.
    + ksize = blurring kernel size.

+ Gaussian : instead of box filter, use gaussian kernel. It can be used as:<br>
**cv2.GaussianBlur(src, ksize, sigmaX,  sigmaY)** where:
    + src = input image; it can have any number of channels, which are processed independently.
    + ksize = blurring kernel size.
    + sigmaX = Gaussian kernel standard deviation in X direction.
    + sigmaY = Gaussian kernel standard deviation in Y direction; if sigmaY is zero, it is set to be equal to sigmaX, if both sigmas are zeros, they are computed from ksize.width and ksize.height.

+ Median : Takes median of all the pixels under kernel area and central element is replaced with this median value. It can be used as:<br>
**cv2.medianBlur(src, st, ksize)** where:
    + src = input image; it can have any number of channels, which are processed independently.
    + dst = output image of the same size and the same number of channels as src.    
    + ksize = blurring kernel size.

+ Bilateral Filter : bilateralFilter can reduce unwanted noise very well while keeping edges fairly sharp. It can be used as:<br>
**cv2.bilateralFilter(src, d, sigmaColor, sigmaSpace)** where:<br>
    + src = Source 8-bit or floating-point, 1-channel or 3-channel image.
    + d = Diameter of each pixel neighborhood that is used during filtering. If it is non-positive, it is computed from sigmaSpace.
    + sigmaColor = Filter sigma in the color space. A larger value of the parameter means that farther colors within the pixel neighborhood (see sigmaSpace) will be mixed together, resulting in larger areas of semi-equal color.
    + sigmaSpace = Filter sigma in the coordinate space. A larger value of the parameter means that farther pixels will influence each other as long as their colors are close enough (see sigmaColor ). When d>0, it specifies the neighborhood size regardless of sigmaSpace. Otherwise, d is proportional to sigmaSpace.

<br><br><br><br>

# Implementation

+ [Convolutions, Blurring and Sharpening Images](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/8.%20Convolutions%2C%20Blurring%20and%20Sharpening%20Images.ipynb)