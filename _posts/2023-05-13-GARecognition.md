---
title: Gestures and Actions recognition
author: SeHoon
date: 2023-05-13 22:47:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# How to Recognize Gestures and Actions?
We use [MPII](http://human-pose.mpi-inf.mpg.de/) model to recognize gestures and actions of human. The **MPII** was developed using a specific [CNN](https://csh970605.github.io/posts/CNN/) architecture called **VGG**. The shape of VGG is:
<center>
<img src="https://github.com/csh970605/Machine-LearningA-Z/assets/28240052/7d5f937a-e07e-40dd-b0f9-c43943614fb1" width=800>
</center>
<br><br>

As image above:
+ The white boxes : Convolutional layers.<br>
+ The red boxes : [Pooling layers](https://csh970605.github.io/posts/Pooling/).
+ Other boxes : Detection layers. The output layer will be the number of objects. That is, If we use imagenet(https://www.image-net.org/), the numbers of the output layer will be 1000.<br>
But, since we use MPII which detect the points of human, the numbers of the output layer will be 15. Like:
<center>
<img src="https://github.com/csh970605/Machine-LearningA-Z/assets/28240052/02a83b27-a9ca-4365-9559-bf50b1dcc448" width=900>
</center>
<br><br>


# Implementation
<br>

+ [recognize gestures and actions by Caffe](https://github.com/csh970605/Computer-Vision-Masterclass/tree/main/Section%2010) 
<br>I used Caffe framework to implement it.
