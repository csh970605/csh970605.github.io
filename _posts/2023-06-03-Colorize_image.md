---
title: Colorize image
author: SeHoon
date: 2023-06-03 14:09:00 +090
categories: [Vision Machine Learning, VML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Colorize image

We can color the black-white(grayscale) image by Caffe Model. <br>
The colorize model consists of many [convolutional layers](https://csh970605.github.io/posts/CNN/). Let's see the structure of colorize model.

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/8e40261b-9297-403c-8508-c2b269724a17" width=800>
</center>
<br><br>
<br><br>

## Steps of colorizing image using OpenCV
---
<br>

1. Get the Caffe model by [readNetFromCaffe](https://csh970605.github.io/posts/readNetFromCaffe/).

2. Load cluster centers.

3. Populate cluster centers as 181 convolution kernel.

4. Convert image to LAB.

5. Get the L channel of image only.

6. Resize the image to network input size(224,224).

7. Subtract 50 for mean-centering.

8. Concatenate with original image L.

<br><br>
<br><br>

# Implementation

+ [Colorize Black and White Photos using a Caffe Model in OpenCV](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/36.%20Colorize%20Black%20and%20White%20Photos%20using%20a%20Caffe%20Model%20in%20OpenCV.ipynb)