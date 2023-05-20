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

+ Convolution : It uses [convolution layer](https://csh970605.github.io/posts/CNN/) in order to get blurred images. It can be used by:<br>
**cv2.filter2D(src, dst, ddepth, kernel, anchor, delta, borderType)** where: <br>
    + src = input image
    + dst = output image of the same size and the same number of channels as src.
    + ddepth = desired depth of the destination image.
    + kernel = 	convolution kernel (or rather a correlation kernel), a single-channel floating point matrix; if you want to apply different kernels to different channels, split the image into separate color planes using split and process them individually.
    + anchor = anchor of the kernel that indicates the relative position of a filtered point within the kernel; the anchor should lie within the kernel; default value (-1,-1) means that the anchor is at the kernel center.
    + delta = optional value added to the filtered pixels before storing them in dst.
    + borderType = pixel extrapolation method.

+ Regular : Averaging done by convolving the image with a normalized box filter. This takes the pixels under the box and replaces the central element. Box size needs to odd and positive  It can be used by:
**cv2.blur(src, dst, ksize, anchor, borderType)** where:<br>
    + src = input image; it can have any number of channels, which are processed independently, but the depth should be CV_8U, CV_16U, CV_16S, CV_32F or CV_64F.
    + dst = output image of the same size and the same number of channels as src.    
    + ksize = blurring kernel size.
    + anchor = anchor of the kernel that indicates the relative position of a filtered point within the kernel; the anchor should lie within the kernel; default value (-1,-1) means that the anchor is at the kernel center.
    + borderType = pixel extrapolation method.

+ Gaussian : instead of box filter, use gaussian kernel. It can be used by:<br>
**cv2.GaussianBlur(src, dst, ksize, sigmaX,  sigmaY, borderType)** where:
    + src = input image; it can have any number of channels, which are processed independently, but the depth should be CV_8U, CV_16U, CV_16S, CV_32F or CV_64F.
    + dst = output image of the same size and the same number of channels as src.    
    + ksize = blurring kernel size.
    + sigmaX = Gaussian kernel standard deviation in X direction.
    + sigmaY = Gaussian kernel standard deviation in Y direction; if sigmaY is zero, it is set to be equal to sigmaX, if both sigmas are zeros, they are computed from ksize.width and ksize.height.
    + borderType = pixel extrapolation method.

+ Median : Takes median of all the pixels under kernel area and central element is replaced with this median value. It can be used by:<br>
**cv2.medianBlur(src, st, ksize)** where:
    + src = input image; it can have any number of channels, which are processed independently, but the depth should be CV_8U, CV_16U, CV_16S, CV_32F or CV_64F.
    + dst = output image of the same size and the same number of channels as src.    
    + ksize = blurring kernel size.

+ Bilateral Filter : bilateralFilter can reduce unwanted noise very well while keeping edges fairly sharp. It can be used by:<br>
**cv2.bilateralFilter(src, dst, d, sigmaColor, sigmaSpace, borderType)** where:<br>
    + src = Source 8-bit or floating-point, 1-channel or 3-channel image.
    + dst = Destination image of the same size and type as src .
    + d = Diameter of each pixel neighborhood that is used during filtering. If it is non-positive, it is computed from sigmaSpace.
    + sigmaColor = Filter sigma in the color space. A larger value of the parameter means that farther colors within the pixel neighborhood (see sigmaSpace) will be mixed together, resulting in larger areas of semi-equal color.
    + sigmaSpace = Filter sigma in the coordinate space. A larger value of the parameter means that farther pixels will influence each other as long as their colors are close enough (see sigmaColor ). When d>0, it specifies the neighborhood size regardless of sigmaSpace. Otherwise, d is proportional to sigmaSpace.
    + borderType = pixel extrapolation method.

<br><br><br><br>

# Implementation

+ [Convolutions, Blurring and Sharpening Images](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/8.%20Convolutions%2C%20Blurring%20and%20Sharpening%20Images.ipynb)