---
title: Restore Damged Photos
author: SeHoon
date: 2023-06-03 20:09:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# How to Restore Damaged Photos?
We can restore damaged photos by preparing two images one with a damaged image and the other with an image that the damaged areas(want to restore) are marked manually. Note that the color of marked area is better to be white.<br>
Then, apply **cv2.inpaint(src, inpaintMask, dst, inpaintRadius, flags)** where:<br>

+ src : Damaged image.

+ inpaintMask : The image that mark manually.

+ dst : Output image.

+ inpaintRadius : Radius of a circular neighborhood of each point inpainted that is considered by the algorithm.

+ flags : Inpainting method that is **cv2.INPAINT_NS** or **cv2.INPAINT_TELEA**

<br><br><br><br>

## Steps of Restoring image.
---
<br>

1. Prepare 2 images.

2. [Thresholding](https://csh970605.github.io/posts/Thresholding/) the marked image.

3. Make our marks thicker by **cv2.dilate(src, dst, kernel, anchor, iterations)** where: <br>

    + src : Input image.

    + dst : Output image.

    + kernel : Structuring element used for dilation.

    + anchor : Position of the anchor within the element. Default = (-1, -1)(means the anchor is at the element center.)

    + iterations : number of times dilation is applied.
    <br><br>

4. Get the restored image by **cv2.inpaint()**.

<br><br><br><br>

# Implementation

+ [Inpainting to Restore Damaged Photos](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/37.%20Inpainting%20to%20Restore%20Damaged%20Photos.ipynb)