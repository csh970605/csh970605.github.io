---
title: Motion Tracking with Mean Shift & CAMSHIFT
author: SeHoon
date: 2023-05-25 20:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Mean Shift?
Mean shift is a hill climbing algorithm which involves shifting this kernel iteratively to a higher density region until convergence. Every shift is defined by a mean shift vector. The mean shift vector always points toward the direction of the maximum increase in the density.<br><br>

Consider we have a set of points. We are given a small window and we have to move that window to the area of maximum pixel density. It will take several steps given below: