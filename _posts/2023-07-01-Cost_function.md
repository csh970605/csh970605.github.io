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

Cost function is a function that needs to find the maximum or minimum value in an optimization algorithm in machine learning. [Gradient descent](https://csh970605.github.io/posts/Gradient_Descent/) is a base algorithm To make the cost function maximum or minimum.

<br><br><br><br>

# Types of cost function

+ MSE(Mean Squared Error) : $\frac{1}{N} \Sigma_{i=1}^{N}(y_{i}\ -\ \hat{y_{i}})^{2}$<br>


+ MAE(Mean Absolute Error) : $\frac{1}{N} \Sigma_{i=1}^{N}|y_{i}\ -\ \hat{y_{i}}|$<br>


+ Binary Cross-entropy(log loss) : $-\frac{1}{N} \Sigma_{i=1}^{N}(y_{i}log(\hat{y_{i}})\ +\ (1-y_{i})log(1-\hat{y_{i}}))$<br>


+ Multinomial-log loss : $-\frac{1}{N}\Sigma_{i=1}^{N}\Sigma_{i=1}^{K}(y_{i,k}*log(\hat{y_{i,k}}))$<br>


where $y_{i}$=Ground Truth, $\hat{y_{i}}$=Expected Value