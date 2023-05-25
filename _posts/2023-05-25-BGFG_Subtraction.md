---
title: Background & Foreground Subtraction
author: SeHoon
date: 2023-05-25 12:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Background Subtraction?
Background subtraction (BS) is a common and widely used technique for generating a foreground mask by using static cameras.<br><br>
BS calculates the foreground mask performing a subtraction between the current frame and a background model, containing the static part of the scene or, more in general, everything that can be considered as background given the characteristics of the observed scene.
<br><br>

We can perform Background subtraction by methods in **cv2.bgsegm**. For example, we can create MOG background subtractor by **cv2.bgsegm.createBackgroundSubtractorMOG()** and apply it by **cv2.bgsegm.createBackgroundSubtractorMOG().apply(image)**<br><br>

Or, we can just create background subtractor by **cv2.createBackgroundSubtractorKNN()** or **cv2.createBackgroundSubtractorMOG2()** and also apply it just adding .apply(image) behind these functions.

<br><br><br><br>

## Methods on bgsegm
---
<br>

+ cv2.bgsegm.createBackgroundSubtractorCNT() : Creates a CNT Background Subtractor.
+ cv2.bgsegm.createBackgroundSubtractorGMG() : Creates a GMG Background Subtractor.
+ cv2.bgsegm.createBackgroundSubtractorGSOC() : Creates an instance of BackgroundSubtractorGSOC algorithm.
+ cv2.bgsegm.createBackgroundSubtractorLSBP() : Creates an instance of BackgroundSubtractorLSBP algorithm.
+ cv2.bgsegm.createBackgroundSubtractorMOG() : Creates mixture-of-gaussian background subtractor.
+ cv2.bgsegm.createSyntheticSequenceGenerator() : Creates an instance of SyntheticSequenceGenerator.

<br><br><br><br>

## Result
---
<br>

<center>

<img src="" width=500>

<br><br>

<img src="" width=500>
</center>
<br><br><br><br>

# What is Foreground Subtraction?
Foreground subtraction is a technique for generating a background mask. We can perform it via steps.
<br><br><br><br>

## Steps of Foreground Subtraction
---
<br>

1. Update weights : We can update weights by **cv2.accumulateWeighted(src, dst, alpha)** where<br>
    + src : Input image.
    + dst : Output image.
    + alpha : weight of the input image.
2. Calculate absolute values and convert the result to 8-bit. : we can calculate and convert the result by **cv2.convertScaleAbs(src)** where
    + src : Input image that created in step 1.
<br><br><br><br>

## Result
---
<br>

