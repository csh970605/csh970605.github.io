---
title: Template Matching
author: SeHoon
date: 2023-05-22 16:26:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Template Matching in OpenCV?
Template matching  takes a “sliding window” of our waldo query image and slides it across our puzzle image from left to right and top to bottom, one pixel at a time. Then, for each of these locations, it compute the correlation coefficient to determine how “good” or “bad” the match is.<br>

Template matching can be done by:<br>
**cv2.matchTemplate()**