---
title: Object Tracking
author: SeHoon
date: 2023-03-24 22:38:00 +0900
categories: [Vision Machine Learning, Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# How object tracking differs from object detection
Tracking algorithms are much faster than detection algorithms because to track an object, the algorithm already knows what it looks like in order to track it in the next frames of the video.
<br><br>
Also the algorithms can detect a kind of pattern that indicates the direction and speed of the objects. So the algorithm already knows that in the next frame of the video, where the object will be.
<br><br>
In short, the information is used to predict the location of the object in the next frame.
<br><br>
**For this reason, tracking algorithms are faster because they use existing data, where as the detection algorithm would have to be executed frame by frame without using data.**
<br><br>
**On the other hand, tracking algorithms can have a difficulty in tracking objects that change position drastically.**
<br><br>
Unlike detection algorithms that make a detection every frame, a tracking algorithm will detect the object only in the first frame. and then it will use that information until the end of video.
<br><br>
Tracking algorithm can adapt to small variations in the images or videos.<br>
As you can see image below, their hands are in front of the faces.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/227708295-f4ffc934-ca97-456b-ae17-7271420086f8.png">
</center><br>
So, face recognition alogirthm will not recognize the faces.<br>
But, tracking algorithm can recognize the faces because tracking algorithm has information about the object.
<br><br>

# KCF(Kernel Correlation Filters)
runs very fast, but the quality is not so good.<br>

# CSRT(Discriminative Correlation Filter with Channel and Spatial Reliability)
runs lower speed, but the quality is higher.<br>