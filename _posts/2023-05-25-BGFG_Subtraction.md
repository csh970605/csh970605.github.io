---
title: Background & Foreground Subtraction
author: SeHoon
date: 2023-05-25 13:11:00 +0900
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

Original Image
<img src="https://drive.google.com/uc?export=view&id=1Z-ckZnZ3Cwpel8Kp7qL0Lp7xPvugyzHK">
<br><br>

MOG
<img src="https://drive.google.com/uc?export=view&id=1I7zpPIHMI8XKn4DD2oBM_pnwcbQ5bhAp">
<br><br>

GSOC
<img src="https://drive.google.com/uc?export=view&id=14L5lNqIaoaf6jMHrPFAkfR0yBlNGJy4O">
<br><br>

CNT
<img src="https://drive.google.com/uc?export=view&id=1eV_DI4fmYR7MUQ_vJMHBs4JheFXU6XXP">
<br><br>

GMG
<img src="https://drive.google.com/uc?export=view&id=1W_SapOTS9HpYQ-7QjugxU7PI0nZ5-_PA">
<br><br>

LSBP
<img src="https://drive.google.com/uc?export=view&id=1vRjc7rC_fpDQsj-GhAYr488K7fldv7Rs">
<br><br>

KNN
<img src="https://drive.google.com/uc?export=view&id=1_vDIN7iq1-WO3uQaNBbryPcj5OqA9FcB">
<br><br>

MOG2
<img src="https://drive.google.com/uc?export=view&id=1_vDIN7iq1-WO3uQaNBbryPcj5OqA9FcB">
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

Original Image
<img src="https://drive.google.com/uc?export=view&id=1Z-ckZnZ3Cwpel8Kp7qL0Lp7xPvugyzHK">
<br><br>

<img src="https://drive.google.com/uc?export=view&id=1whfVO6wG_KwNyQhtUeT8edyC2uM5QKL5">


<br><br><br><br>

# Implementation

+ [Background and Foreground Subtraction](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/23.%20Background%20and%20Foreground%20Subtraction.ipynb)