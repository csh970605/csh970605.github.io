---
title: Blur Detection
author: SeHoon
date: 2023-06-05 20:59:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# How to do Blur Detection?

We can get the value of blur by using **cv2.Laplacian(src, ddepth, ksize, scale, delta).var()** where:<br>

+ src : Grayscaled image.

+ ddepth : Desired depth of the destination image.

+ ksize : Aperture size used to compute the second-derivative filters. <br>
If ksize > 1, Laplacian is computed $\Delta src\ =\ \frac{\delta a^{2} src}{\delta x^{2}}\ +\ \frac{\delta^{2} src}{\delta y^{2}}$.<br>
If ksize = 1, Laplacian is computed by filtering the image with 3X3 matrix which is:<br>
$$\begin{bmatrix}
0 & 1 & 0\\
1 & -4 & 1\\
0 & 1 & 0
\end{bmatrix}$$


+ scale : Optional scale factor for the computed Laplacian values.

+ delta : Optional delta value that is added to the results prior to storing them in dst.


To detect blur, we take the variance of the response output. The Laplacian is the 2nd derivative of an image and thus it highlights the areas of an image containing rapid intensity changes. Hence it's use in Edge Detection. A high variance should in theory, indicate the presence of both edge-like and non-edge like (hence the wide range of values resulting in a high variance), which is typical of a normal in-focus image. A low variance, thus might mean very little edges in the image meaning it might be blurred as the more blur present the less edges there are.

<br><br><br><br>


# Implementation

+ [Blur Detection](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/39.%20Detect%20Blur%20in%20Images.ipynb)