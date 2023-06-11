---
title: scaled-YOLOv4
author: SeHoon
date: 2023-06-10 19:30:00 +0900
categories: [Vision Machine Learning, VML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is scaled-YOLOv4?

Scaled-YOLOv4 is designed to use in every devices whether they are low-end devices or high-end devices. And also, it can perform real-time object detection on 16, 30, 60 FPS movies or embedded systems.<br><br>

As you can see the name of scaled-YOLOv4, it just adds [YOLOv4](https://csh970605.github.io/posts/YOLOv4/) and the upper & lower bounds of linear scaling up&down model which are YOLOv4-large & YOLOv4-tiny.
<br><br>

Then, let's see the structure of scaled-YOLOv4.
<br><br><br><br>

# Structure of scaled-YOLOv4

+ Backbone : CSPDarknet53 with no computation of down-sampling convolution for cross-stage process. And scaled-YOLOv4 is separated YOLOv4-tiny and YOLOv4-large

    + YOLOv4-tiny : CSPOSANet with PCB architecture to form the backbone of YOLOv4.

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/c1aa1824-f510-4290-8103-128ce4f1e932" width=500>
    </center><br><br>

    + YOLOv4-large : A fully CSP-ized model YOLOv4-P5 and scaling it up to YOLOv4-P6 and YOLOv4-P7.<br>
    YOLOv4-p6 reaches real-time performance at 30 FPS video when the width scaling factor is equal to 1.<br>
    YOLOv4-P7 reaches real-time performance at 16 FPS video when the width scaling factor is equal to 1.25.

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/ea5af52a-c43b-45e4-b6e7-dd334c7a20c1" width=800>
    </center><br><br>

    + BOF for backbone : [CUTMIX](https://arxiv.org/abs/1905.04899), mosaic [data augmentation](https://csh970605.github.io/posts/Data_Augmentation/)

    + BOS for backbone :[CSP](https://csh970605.github.io/posts/CSP/), MiWRC



+ Neck : Use CSP-ize the PAN architecture in YOLOv4((a) in image below) and 2 reversed CSP dark layers((b) in image below). Unlike the original SPP module, in scaled-YOLOv4, SPP module is inserted in the middle position of the first computation list group of the CSPPAN.

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/b6c7c8de-9cd7-440d-b63a-0c5848096f7d" width=500>
</center><br><br>



+ Head : [YOLOv3](https://csh970605.github.io/posts/YOLOv3/)

    + BOF for detector : [CIoU-loss](https://csh970605.github.io/posts/CIOU_Loss/), CmBN, [DropBlock](https://csh970605.github.io/posts/DropBlock/) regularization, Mosaic data augmentation, Self-Adversarial Training, Eliminate grid sensitivity, Using multiple anchors for a single ground truth, Cosine annealing scheduler, Optimal hyperparameters, Random training shapes.

    + BOS for Detector : [Mish activation](https://csh970605.github.io/posts/Activation_Function/), SPP-block, SAM-block, PAN path-aggregation block, DIoU-NMS

<br><br><br><br>


# Implementation

+ [How to Train Scaled-YOLOv4 on our Pistols Dataset](https://github.com/csh970605/Modern_Computer_Vision/blob/main/Deep%20Learning%20CV/42.%20Object%20Detection%20-%20Gun%2C%20Pistol%20Detector%20-%20Scaled-YOLOv4.ipynb)