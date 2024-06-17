---
title: L2 Regularization
author: SeHoon
date: 2023-06-08 15:20:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is L2 Regularization?

It is a way to perform [Regularization](https://csh970605.github.io/posts/Regularization/).<br>
L2 Regularization is weight decay technique which decrease more faster if the weight is bigger. Thus, as the overall weights get smaller, the learning effect improves. L2 Regularization adds the squared value of the weights to the cost function:


$Cost = \frac{1}{n} \sum_{i=1}^{n}(L(y_{i}, \hat{y_{i}}) + \frac{\lambda}{2}|w|^{2})$

<br>

where $L(y_{i}, \hat{y_{i}})$ : Existing [cost function](https://csh970605.github.io/posts/Cost_function/).