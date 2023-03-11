---
title: Face Recognition
author: SeHoon
date: 2023-03-11 20:32:00 +0900
categories: [Vision Machine Learning, Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---
# What is Face Recognition?
<br>
 with the facial images already extracted, cropped, resized and usually converted to grayscale, the face recognition algorithm is responsible for finding characteristics which best describe the image.<br><br>
 
 ## Differences From Face Detection
 <br>
 Face recognition classifies faces with face images extracted from face detection.
<br><br>

# Algorithm
<br>
We will use LBPH(Local Binary Patterns Histograms)<br>
<br>

## What is LBPH?
<br>
LBP (Local Binary Patterns) is a feature extraction technique used to recognize or analyze textures in the field of image processing. LBPH is a technique that combines LBP and a histogram (H). LBP extracts features of an image by converting the pixel values around each pixel in the image into binary numbers. Binary numbers are generated based on the relative brightness difference between the center pixel and its neighbors. If the neighboring pixel is larger than the center pixel, it is represented as 1, and if it is less than the center pixel, it is represented as 0.

Using these binary numbers, we can extract texture features for each pixel. Extracting Local Binary Patterns (LBPs) can result in specific patterns appearing in specific parts of an image. It uses these patterns to recognize objects or faces in images.