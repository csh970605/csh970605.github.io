---
title: Classification
author: SeHoon
date: 2023-04-01 15:34:00 +0900
categories: [Machine Learning, ML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Regression?<br>
Regression models (both linear and non-linear) are used for predicting a real value.<br>
If your independent variable is time, then you are forecasting future values, otherwise your model is predicting present but unknown values.<br>
<br><br>

# Regression VS Classification

+ Regression : Used to predict continuous real values.
+ Classification : Used to predict categories or classes.
<br><br>

# Pros and cons of classification model

| Classification Model | Pros | Cons |
| -------------------- | ---- | ---- |
| [Logistic Regression](https://csh970605.github.io/posts/Rogistic_Regression/)  | Probabilistic approach.<br>Provides information on the statistical significance of features. | Logistic Regression Assumption.|
| [K Nearest Neighbors(KNN)](https://csh970605.github.io/posts/KNN/) | easy to understand.<br> fast and effective. | The number of neighbors k must be determined. |
| [Support Vector Machine(SVM)](https://csh970605.github.io/posts/SVM/) | Ideal.<br> Unbiased to outliers.<br> Not sensitive to overfitting. | Not suitable for non-linear data sets.<br> Not effective for datasets with many features. |
| [Kernel Support Vector Machine(Kernel SVM)](https://csh970605.github.io/posts/Kernel_SVM/) | High performance on nonlinear datasets.<br> Not prone to outliers.<br> Not sensitive to overfitting. | Not effective for datasets with many features.<br> complicated.|
| [Naive Bayes](https://csh970605.github.io/posts/Naive_Bayes/) |Effective. <br>Unbiased to outliers.<br>Suitable for nonlinear datasets.<br>probabilistic approach. | It should be based on the fact that the features have the same statistical relevance. |
| [Decision Tree Classification](https://csh970605.github.io/posts/Decision_Tree_Classification/) | Interpretability<br>No feature scaling required.<br>Works with both linear and non-linear data sets. | Worst results on small datasets.<br> Overfitting occurs frequently. |
| [Random Forest Classification](https://csh970605.github.io/posts/Random_Forest_Classification/) |Powerful and precise.<br> Shows good performance on non-linear datasets.| Uninterpretable.<br>Overfitting easily occurs.<br> You must select the number of trees.|

<br>

You can see my implementation on my [Github](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%203%20-%20Classification)