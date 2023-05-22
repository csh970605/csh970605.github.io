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
**cv2.matchTemplate(image, templ, method) -> result** where :<br>
+ image : Image where the search is running.
+ templ : Searched template. It must be not greater than the source image and have the same data type.
+ method : Parameter specifying the comparison method. This parameter helps us to find as global minimums(when **TM_SQDIFF** was used) or maximums(**TM_CCORR** or **TM_CCOEFF** was used).
+ result : we can get "min_val", "max_val", "min_loc", "max_loc" by using **cv2.minMaxLoc(result)**.

<br><br><br><br>

## Result
---
<br>
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/ab59c7f6-fb3f-4818-80ad-53101cb3d773" width=500>
</center>
<br><br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/62d441f4-215d-487b-bd73-e4e0662bbfce" width=500>
</center>
<br><br><br><br>

# Implementation
+ [Counting Circles, Ellipses and Finding Waldo](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/14.%20Counting%20Circles%2C%20Ellipses%20and%20Finding%20Waldo%20with%20Template%20Matching.ipynb)