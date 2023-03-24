---
title: Object Tracking
author: SeHoon
date: 2023-03-24 22:58:00 +0900
categories: [Vision Machine Learning, Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# Object Tracking
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