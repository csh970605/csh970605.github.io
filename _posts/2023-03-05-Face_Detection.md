---
title: Face Detection
author: SeHoon
date: 2023-03-05 15:47:00 +0900
categories: [Vision Machine Learning, VML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Face Detection?<br>
It has the objective of finding the faces (location and size) in an image and possibly extract them to be used by the face recognition algorithm.<br>

<br><br>

# Algorithms<br>
There are two algorithms<br>

- Cascade Classifier<br>
    + Trains positive and negative images to quickly and accurately detect face regions.<br>
    + More details can be found in the [Cascade Classifier](https://csh970605.github.io/posts/Cascade-Classifier/) post.<br>
- HOG(Histograms of Oriented Gradients)
    + A method of extracting a histogram-type feature by considering the angle and size of the pixel variation<br>
    + More details can be found in the [HOG (Histograms of Oriented Gradients)](https://csh970605.github.io/posts/HOG/) post.<br><br>

