---
title: Background Removal
author: SeHoon
date: 2023-05-25 22:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# Types of Background Removal

+ Grab Cut

<br><br><br><br>

# What is Grab Cut?
GrabCut is an image segmentation method based on graph cuts.<br>
It can be used by **cv2.grabCut(img, mask, rect, bgdModel, fgdModel, iterCount, mode) -> mask, bgdModel, fgdModel** where<br>

+ img : 8-bit 3-channel image.

+ mask : Input/output 8-bit single-channel mask. The mask is initialized by the function when mode is set to cv2.GC_INIT_WITH_RECT. Otherwise, the mask is setted by GrabCutClasses.

+ rect : Coordinates of a rectangle which includes the foreground object in the format. The pixels outside of the ROI are marked as "obvious background". **The parameter is only used when mode==cv2.GC_INIT_WITH_RECT.**

+ bgdModel : Temporary array for the background model. Just create two np.float64 type zero arrays of size (1, 65).

+ fgdModel : Temporary array for the foreground model. Just create two np.float64 type zero arrays of size (1, 65).

+ iterCount : Number of iterations the algorithm should run.

+ mode : Operation mode that could be one of the GrabCutModes.


<br><br><br><br>

## GrabCutClasses
---
<br>

+ cv2.GC_BDG : An obvious background pixels.

+ cv2.GC_FGD : An obvious foreground (object) pixel.

+ cv2.GC_PR_BGD : A possible background pixel.

+ cv2.GC_PR_FGD : A possible foreground pixel.

<br><br><br><br>

## GrabCutModes
---
<br>

+ cv2.GC_INIT_WITH_RECT : The function initializes the state and the mask using the provided rectangle. After that it runs iterCount iterations of the algorithm.

+ cv2.GC_INIT_WITH_MASK : The function initializes the state using the provided mask. Note that cv2.GC_INIT_WITH_RECT and cv2.GC_INIT_WITH_MASK can be combined.

+ cv2.GC_EVAL : The value means that the algorithm should just resume.

+ cv2.GC_EVAL_FREEZE_MODEL : The value means that the algorithm should just run the grabCut algorithm (a single iteration) with the fixed model
