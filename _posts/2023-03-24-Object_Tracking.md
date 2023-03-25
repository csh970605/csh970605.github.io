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

# KCF(Kernelized Correlation Filters)
Runs very fast, but the quality is not so good especially in fast videos.<br>
**Most common problem occurs when the bounding box loses the object.** <br>
<br>

## Goal
---
The goal of the KCF is to make several adjustments in bounding boxes in order to circle the object and be able to detect it.<br>
<br>

## How KCF works?
---
+ Frame 1(Initialization)<br>
We have the first frame, which is the initialization or the definition of the object to be detected.<br>
Algorithm applies a particle filter(red box) and two more bounding boxes are created to cover a large parts of the image(blue box, green box)<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/227716410-6727de58-550e-4616-b235-2e9db27898ef.png"><br>
</center><br>

+ Frame 2 & Frame 3(Translation Estimation)<br>
The larger rectangle is used the green box(filter) and some mathematical calculations are made to adjust the fram in the central parts of face as written in image below.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/227716442-f513f880-8d20-4092-b94c-75c8bebe4649.png"><br>
</center><br>

+ Frame 4 & Frame 5(Translation Estimation)<br>
The blue box(filter) is updated to the central position of the face.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/227716473-a5ba13e6-38dc-4a85-aecb-89563ad79053.png"><br>
</center><br>

+ Frame 6(Scale Estimation)<br>
The red box(filter) is updated to the central position of the face.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/227716479-f1ef642d-e891-4fda-abbf-6739c475c39e.png"><br>
</center><br>

+ Frame 7(Translation Estimation)<br>
Before this step, the first update of all filters is done.<br>
From now on, we repeat what we did from frame2 to frame6 with the box slightly smaller.<br>
This means, it was adjusted to the object.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/227716486-98efa8f5-cc24-486d-a772-76345cc8d638.png"><br>
</center><br>
<br>

The larger frames that were automatically generated are important to detect changes in the scale which represents the size of the objects.<br>
Example of size change: if in one frame the object is smaller and in the next frame the object increases size like a person approaching the camera.<br><br>

# CSRT(Discriminative Correlation Filter with Channel and Spatial Reliability)
Runs lower speed, but the quality is higher.<br>