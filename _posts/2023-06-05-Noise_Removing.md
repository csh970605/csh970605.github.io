---
title: Remove Noise
author: SeHoon
date: 2023-06-05 15:09:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# How to Remove Noise?
There are 4 ways to remove noise that can be applied in each situation.

+ **cv2.fastNlMeansDenoising(src, dst, h, templateWindowSize, SearchWindowSize)** is used for image in grayscale where:
    
    + src : Input image.

    + dst : Output.

    + h : Array of parameters regulating filter strength, either one parameter applied to all channels or one per channel in dst. The bigger value removes noise well, but the smaller value preserves some details.

    + templateWindowSize : Size in pixels of the template patch that is used to compute weights. The value should be odd. And the value of 7 is recommended.

    + SearchWindowSize : Size in pixels of the window that is used to compute weighted average for given pixel. The value sholud be odd. And the value of 21 is recommended.

+ **cv2.fastNlMeansDenoisingColored(src, dst, h_luminance, photo_render, search_window, block_size)** is used for image in multiscale where: 

    + src : Input image.

    + dst : Output.

    + h_luminance : Parameter regulating filter strength. The bigger value removes noise well, but the smaller value preserves some details.

    + photo_render : The same as h but for color components. For most images value equals 10 will be enough to remove colored noise and do not distort colors.

    + search_window : Size in pixels of the window that is used to compute weighted average for given pixel. The value should be odd. And the value of 21 is recommended.

    + block_size : Size in pixels of the template patch that is used to compute weights. The value should be odd. And the value of 7 is recommended.

+ **cv2.fastNlMeansDenoisingMulti(srcImgs, dst, imgToDenoiseIndex, temporalWindowSize, h, templateWindowSize, searchWindowSize, normType)** is used for images sequence in small period of time. And the images must be grayscale images where: <br>

    + srcImgs : Input images sequence.

    + dst : Output.

    + imgToDenoiseIndex : Target image to denoise index in srcImgs sequence

    + temporalWindowSize : Number of surrounding images to use for target image denoising. The value should be odd.

    + h : Array of parameters regulating filter strength, either one parameter applied to all channels or one per channel in dst. The bigger value removes noise well, but the smaller value preserves some details.

    + templateWindowSize : Size in pixels of the template patch that is used to compute weights. The value should be odd. And the value of 7 is recommended.

    + searchWindowSize : Size in pixels of the window that is used to compute weighted average for given pixel. The value sholud be odd. And the value of 21 is recommended.

    + normType : Type of norm used for weight calculation. It can be NORM_L2 or NORM_L1

    
     Images from imgToDenoiseIndex - temporalWindowSize / 2 to imgToDenoiseIndex - temporalWindowSize / 2 from srcImgs will be used to denoise srcImgs[imgToDenoiseIndex] image.
     <br><br>

+ **cv2.fastNlMeansDenoisingColoredMulti(srcImgs, dst, imgToDenoiseIndex, temporalWindowSize, h, hColor, templateWindowSize, searchWindowSize)** is used for images sequence in small period of time. And the images must be multiscale images where: 

    + srcImgs : Input images sequence.

    + dst : Output

    + imgToDenoiseIndex : Target image to denoise index in srcImgs sequence

    + temporalWindowSize : Number of surrounding images to use for target image denoising. The value should be odd.

    + h : Array of parameters regulating filter strength, either one parameter applied to all channels or one per channel in dst. The bigger value removes noise well, but the smaller value preserves some details.

    + hColor : The same as h but for color components.

    + templateWindowSize : Size in pixels of the template patch that is used to compute weights. The value should be odd. And the value of 7 is recommended.

    + searchWindowSize : Size in pixels of the window that is used to compute weighted average for given pixel. The value sholud be odd. And the value of 21 is recommended.

    Images from imgToDenoiseIndex - temporalWindowSize / 2 to imgToDenoiseIndex - temporalWindowSize / 2 from srcImgs will be used to denoise srcImgs[imgToDenoiseIndex] image.
    <br><br><br><br>

# Implementation

+ [Add and Remove Noise](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/38-1.%20Add%20and%20Remove%20Noise.ipynb)