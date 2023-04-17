---
title: Cross Entropy
author: SeHoon
date: 2023-04-17 20:00:00 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is Cross Entropy?
Cross entropy function is a loss function for evaluating network performance(usually [CNN](https://csh970605.github.io/posts/CNN/)).<br>
Here is the two formulas of cross entropy:<br>

<center>
<font size=5>

$ L_{i}\ =\ -log(\frac{e^{f_{yi}}}{\Sigma_{j}e^{f_{j}}}) $<br>

$ H(p,q)\ =\ -\Sigma_{x}p(x)log\ q(x)$

</font>
</center>
<br><br>
Then, let's see how the formula applied.<br>
For example, here is predicted value made by CNN and expected value:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232476899-10db79f6-4395-4dd7-b2eb-06efcc94e813.png" width=500>
</center>
<br><br>

And let's calculate $H(p,q)$:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232477091-6153b2cb-fc15-47aa-bd59-16a59b1380ce.png" width=500>
</center>
<br><br>

The result is $ H(p, q)\ =\ 0.04 $
<br><br>
With cross entropy, there is a log in it to help the network evaluate and act on even these small errors.