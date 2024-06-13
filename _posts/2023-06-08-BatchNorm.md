---
title: Batch Normalization
author: SeHoon
date: 2023-06-08 15:23:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is Batch Normalization?
It is a way to perform [Regularization](https://csh970605.github.io/posts/Regularization/).<br>
Batch Normalization is normalized using the mean and variance of the mini-batch, and scale and shift are performed through $\gamma$ values and $\beta$ values. At this time, $\gamma$ and $\beta$ is learnable through [back propagation](https://csh970605.github.io/posts/Back_Propagation/).<br><br>

Then, let's see what happend in batch normalization.<br><br>

Input : Values of x over a mini-batch: B= {$x_{1}, \ldots, m$}<br>
        Parameters to be learned : $\gamma,\ \beta$
        <br>
Output : {$y_{i}\ =\ BN_{\gamma,\beta}(x_{i})$}
<br><br>

<font size=4>

$\mu_{B} \leftarrow \frac{1}{m}\sum_{i=1}^{m}x_{i}$ : mini-batch mean<br>

$\sigma^{2}_{B} \leftarrow \frac{1}{m}\sum_{i=1}^{m}(x_{i}-\mu_{B})^{2}$<br>

$\hat{x}_{i} \leftarrow \frac{x_{i}-\mu_{B}}{\sqrt{\sigma^{2}_{B}+\epsilon}}$<br>

$y_{i} \leftarrow \gamma\hat{x}_{i} + \beta \equiv BN_{\gamma,\beta}(x_{i})$<br>

</font>