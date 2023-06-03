---
title: readNetFromCaffe
author: SeHoon
date: 2023-06-03 14:09:00 +090
categories: [Vision Machine Learning, VML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is readNetFromCaffe?

**cv2.dnn.readNetFromCaffe(prototxt, caffeModel)** reads a network model stored in [Caffe](https://csh970605.github.io/posts/GARecognition/) framework's format. where:

+ prototxt : path to the .prototxt file with text description of the network architecture.

+ caffeModel path to the .caffemodel file with learned network.

