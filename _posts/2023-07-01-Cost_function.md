---
title: Cost Function
author: SeHoon
date: 2023-07-01 15:20:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is cost function?

A cost function is a function that needs to find the maximum or minimum value in an optimization algorithm in machine learning. [Gradient descent](https://csh970605.github.io/posts/Gradient_Descent/) is a basic algorithm used to minimize or maximize the cost function.

<br><br><br><br>

# Types of Cost Functions


+ MSE(Mean Squared Error) : $\frac{1}{N} \sum_{i=1}^{N}(y_{i} - \hat{y_{i}})^{2}$
<br>

+ MAE(Mean Absolute Error) : $\frac{1}{N} \sum_{i=1}^{N}|y_{i} - \hat{y_{i}}|$
<br>

+ Binary Cross-entropy(log loss) : $-\frac{1}{N} \sum_{i=1}^{N}(y_{i}\log(\hat{y_{i}}) + (1-y_{i})\log(1-\hat{y_{i}}))$
<br>

+ Multinomial-log loss : $-\frac{1}{N}\sum_{i=1}^{N}\sum_{i=1}^{K}(y_{i,k} \times log(\hat{y_{i,k}}))$
<br>

where $y_{i}$=Ground Truth, $\hat{y_{i}}$=Expected Value