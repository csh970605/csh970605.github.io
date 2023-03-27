---
title: Face Detecting
author: SeHoon
date: 2023-03-05 15:47:00 +0900
categories: [Vision Machine Learning, Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Face Detection?
<br>
it has the objective of finding the faces (location and size) in an image and probably extract them to be used by the face recognition algorithm.<br>

<br><br>

# Algorithms
<br>
There are two algorithms<br><br>

- Casacade Classifier<br>
    + Train positive and negative images to quickly and accurately detect face regions.<br>
    + There are more details in [Casacade Classifier](https://csh970605.github.io/posts/Casacade-Classifier/) post<br>
- HOG(Histograms of Oriented Gradients)
    + A method of extracting a histogram-type feature by considering the angle and size of the pixel variation<br>
    + There are more details in [HOG(Histograms of Oriented Gradients)](https://csh970605.github.io/posts/HOG/) post<br>

# Code<br>
You can see my implementation on my [Github](https://github.com/csh970605/Computer-Vision-Masterclass/tree/main/Section%201)
