---
title: Object Tracking
author: SeHoon
date: 2023-03-24 22:38:00 +0900
categories: [Vision Machine Learning, VML_Introduction]
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
You can see more details in [KCF](https://csh970605.github.io/posts/KCF) post.<br><br>
# CSRT(Discriminative Correlation Filter with Channel and Spatial Reliability)
Runs lower speed, but the quality is higher.<br>
You can see more details in [KCF](https://csh970605.github.io/posts/CSRT) post.<br><br>

# Codes<br>
You can see my implementation on my [Github](https://github.com/csh970605/Computer-Vision-Masterclass/tree/main/Section%203)<br><br>

# Additional Reading<br>
+ [OpenCV documentation](https://docs.opencv.org/4.x/)
+ [Object Tracking: A Literature Review](https://arxiv.org/abs/1409.7618)
+ [KCF Algorithm](https://arxiv.org/abs/1404.7584)
+ [Improvement on KCF Algorithm](https://www.researchgate.net/publication/327844935_Improvement_of_the_KCF_Tracking_Algorithm_through_Object_Detection)
+ [CSRT Algorithm](https://arxiv.org/pdf/1611.08461.pdf)