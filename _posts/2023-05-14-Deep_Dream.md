---
title: DeepDream
author: SeHoon
date: 2023-05-13 20:47:00 +0900
categories: [Vision Machine Learning, VML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Deep Dream?
Deep Dream is a computer vision algorithm created by Alexander Mordvintsev from Google. The algorithm works by creating a dream-like effect. Deep Dream works by feeding an image into a trained ANN, where the neurons fire and generate activations. The Deep Dream algorithm works by trying to change the input image in a way that makes some of these neurons fire more (boost the neurons' firing or activations). The process is continuously repeated until the input image contains all the features that a specific layer was originally looking for.

<br><br><br><br>

# Steps of Deep Dream

1. Forward an image through a trained [ANN](https://csh970605.github.io/posts/ANN/), [CNN](https://csh970605.github.io/posts/CNN/), ResNet, etc.
2. Select a layer of choice (first layers capture edges, deep layers capture full shapes such as faces).
3. Calculate the activations (output) coming out from the layer of interest.
4. Calculate the gradient of the activations with respect to the input image.
5. Modify the image to increase these activations, and thus enhance the patterns seen by the network, resulting in a trippy, hallucinated image.
6. Iterate and repeat over multiple scales.

<br><br><br>

# Implementation

+ [Deep Dream](https://github.com/csh970605/TensorFlow-2.0-Advanced/tree/main/Section%204)

<center>
<img src="https://github.com/csh970605/TensorFlow-2.0-Advanced/assets/28240052/c5e519de-49b3-4310-a2f1-6084c82b79a7" width=500>
</center>
<br><br>