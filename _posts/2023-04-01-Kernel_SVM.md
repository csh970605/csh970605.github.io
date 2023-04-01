---
title: Kernel Support Vector Machine(Kernel SVM)
author: SeHoon
date: 2023-04-01 15:36:00 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is kernel SVM?

It is a concept that came out to compensate for the disadvantage that SVM cannot handle non linear datasets like image below.<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229292582-16000507-a769-45fb-9971-556652d1cae7.png"width=400>
</center>

<br><br>
Then, how kernel SVM classify non linear dataset? The answer is mapping to a higher dimension like image below.<br>
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229292858-a3b8faf2-edf1-4971-a8ed-e86514aeef72.png" width=500>
</center>

<br><br>

By mapping to a higher dimension, we can get a linearly separable dataset divided by hyperplane in the space.<br>
After going through the above process, if you project to the lower dimension again, you can get a result with a round hyperplane like the image below.

<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229293177-8c5bfff4-05d1-48f1-a51b-7d3048563c05.png" width=400>
</center>

<br><br>

If then, kernel SVM can classify more complex data set like image below?<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229293702-4fef8e9c-c9b6-474d-85c7-d991c3024a75.png" width=500>
</center>

The answer is YES. By adding more than two kernel formula like Gaussian RBF Kernel, it can classify data set.

There are simple Gaussian RBF kernel formula:<br>

<center>
<font size=4>

$K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{1} ) = $ $e^{-\vert \vec{x} - \vec{l} \vert^{2}\over 2\sigma^{2} }$

</font>
</center>

<br>
So, the result of kernel SVM will appear like this:
<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229294023-acb80d4f-4ba3-4691-b259-d8af7d7b07b8.png" width=500>
</center>

<br>

+ Green when:<br>
$K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{1} )$ $+ K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{2} ) > 0$
+ Red when:<br>
$K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{1} )$ $+ K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{2} ) = 0$

