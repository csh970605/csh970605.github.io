---
title: Object Tracking with Optical Flow
author: SeHoon
date: 2023-05-25 22:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Optical Flow?
Optical flow is the pattern of apparent motion of image objects between two consecutive frames caused by the movemement of object or camera. It is 2D vector field where each vector is a displacement vector showing the movement of points from first frame to second.<br><br>

There are two ways to track object with optical flow.
+ The Lucas-Kanade Optical Flow
+ Dense Optical Flow