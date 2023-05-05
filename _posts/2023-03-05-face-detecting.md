---
title: Face Detecting
author: SeHoon
date: 2023-03-05 15:47:00 +0900
categories: [Vision Machine Learning, VML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Face Detection?<br>
it has the objective of finding the faces (location and size) in an image and probably extract them to be used by the face recognition algorithm.<br>

<br><br>

# Algorithms<br>
There are two algorithms<br>

- Casacade Classifier<br>
    + Train positive and negative images to quickly and accurately detect face regions.<br>
    + There are more details in [Casacade Classifier](https://csh970605.github.io/posts/Casacade-Classifier/) post<br>
- HOG(Histograms of Oriented Gradients)
    + A method of extracting a histogram-type feature by considering the angle and size of the pixel variation<br>
    + There are more details in [HOG(Histograms of Oriented Gradients)](https://csh970605.github.io/posts/HOG/) post<br><br>


# Additional Reading<br>
+ [OpenCV documentation](https://docs.opencv.org/4.x/)
+ [Dlib documentation](http://dlib.net/python/index.html)
+ [Face Detection: A Literature Review](http://www.ijirset.com/upload/2017/july/92_Face.pdf)
+ [Cascade classifier](https://www.cs.cmu.edu/~efros/courses/LBMV07/Papers/viola-cvpr-01.pdf)
+ [HOG classifier](https://hal.inria.fr/inria-00548512/document)
+ [Building your own object detector with OpenCV](https://medium.com/@vipulgote4/guide-to-make-custom-haar-cascade-xml-file-for-object-detection-with-opencv-6932e22c3f0e)
+ [Building your own object detector with Dlib](https://learnopencv.com/training-a-custom-object-detector-with-dlib-making-gesture-controlled-applications/)