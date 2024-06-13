---
title: Dimensionality Reduction
author: SeHoon
date: 2023-04-06 21:17:30 +0900
categories: [Machine Learning, ML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Dimensionality Reduction?

In [classification](https://csh970605.github.io/posts/Classification/), we worked with datasets composed of only two independent variables. We did so for two reasons:

+ Because we needed two dimensions to better visualize how Machine Learning models worked (by plotting the prediction regions and the prediction boundary for each model).

+ Because regardless of the original number of our independent variables, we can often end up with two independent variables by applying an appropriate Dimensionality Reduction technique.

There are two types of Dimensionality Reduction techniques:

+ Feature Selection
    + Backward Elimination<br>
    + Forward Selection<br>
    + Bidirectional Elimination<br>
    + Score Comparison
+ Feature Extraction
    + [Principal Component Analysis (PCA)](https://csh970605.github.io/posts/PCA/)<br>
    + [Linear Discriminant Analysis (LDA)](https://csh970605.github.io/posts/LDA/)<br>
    + [Kernel PCA](https://csh970605.github.io/posts/Kernel_PCA/)<br>


<br><br><br>

You can see my implementation on my [Github](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%209%20-%20Dimensionality%20Reduction)