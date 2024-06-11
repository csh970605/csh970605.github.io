---
title: Object Tracking
author: SeHoon
date: 2023-03-24 22:38:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# How object tracking differs from object detection
Tracking algorithms are much faster than detection algorithms because to track an object, the algorithm already knows what it looks like in order to track it in the next frames of the video. Also, the algorithms can detect a kind of pattern that indicates the direction and speed of the objects. So the algorithm already knows where the object will be in the next frame of the video.
<br><br>
In short, the information is used to predict the location of the object in the next frame.
<br><br>
**For this reason, tracking algorithms are faster because they use existing data, whereas detection algorithms have to be executed frame by frame without using data.**
<br>
**On the other hand, tracking algorithms can have difficulty tracking objects that change position drastically.**
<br><br>
Unlike detection algorithms that make a detection every frame, a tracking algorithm will detect the object only in the first frame, and then it will use that information until the end of the video.
<br><br>
Tracking algorithms can adapt to small variations in the images or videos. As you can see in the image below, their hands are in front of their faces.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/227708295-f4ffc934-ca97-456b-ae17-7271420086f8.png">
</center><br>
So, face recognition algorithms will not recognize the faces. However, tracking algorithms can recognize the faces because it has information about the object.
<br><br>

# KCF(Kernelized Correlation Filters)
Runs very fast, but the quality is not so good, especially in fast videos.<br>
You can see more details in the [KCF](https://csh970605.github.io/posts/KCF) post.<br><br><br><br>
# CSRT(Discriminative Correlation Filter with Channel and Spatial Reliability)
Runs at a lower speed, but the quality is higher.<br>
You can see more details in the [CSRT](https://csh970605.github.io/posts/CSRT) post.<br><br><br><br>

# OpticalFlow
Optical flow is the pattern of apparent motion of image objects between two consecutive frames caused by the movement of an object or camera. You can see more details in the [Optical Flow](https://csh970605.github.io/posts/OT_OpticalFlow/) post.<br><br><br><br>

# Mean Shift & Cam Shift
Mean shift is a hill climbing algorithm that involves shifting this kernel iteratively to a higher density region until convergence. You can see more details in the [Mean Shift & Cam Shift](https://csh970605.github.io/posts/OBT_MCShift/) post.<br><br><br><br>

# SORT

SORT is a powerful tracking algorithm that uses other SOTA detecting frameworks. Although it uses traditional tracking methods, it was a SOTA tracker. You can see more details in the [SORT](https://csh970605.github.io/posts/SORT/) post.

<br><br><br><br>
