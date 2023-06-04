---
title: Regression
author: SeHoon
date: 2023-03-30 20:30:00 +0900
categories: [Machine Learning, ML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Regression?<br>
Regression finds correlations between dependent and independent variables. <br>
Therefore, regression algorithms help predict continuous variables such as house prices, market trends, weather patterns, oil and gas prices, etc.<br>
If your independent variable is time, then you are forecasting future values, otherwise your model is predicting present but unknown values.<br>
<br>

# Regression VS Classification

+ Regression : Used to predict continuous real values.
+ Classification : Used to predict categories or classes.
<br><br>

# Pros and cons of regression model

| Regression Model | Pros | Cons |
| --- | --- | --- |
| [Linear Regression](https://csh970605.github.io/posts/Simple_Linear_Regression/) & [Multi Linear Regression](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%202%20-%20Regression/Section%205%20-%20Multiple%20Linear%20Regression/Python) | Regardless of the size of the data set.<br>Provides information about the relevance of features. | The Linear Regression Assumptions |
| [Polynomial Regression](https://csh970605.github.io/posts/Multiple_Linear_Regression/) | Regardless of the size of the data set.<br>Works well for non-linear structures. | Choose the correct polynomial degree for a good bias/variance trade-off. |
| [Support Vector for Regression(SVR)](https://csh970605.github.io/posts/SVR/) | Adapts easily.<br>Works well for non-linear structures.<br> Not biased towards outliers. | Need to do feature scaling.<br>Not well known.<br>Hard to understand. |
| [Decision Tree Regression](https://csh970605.github.io/posts/Decision_Tree_Regression/) | Ideal.<br>No feature scaling required.<br>Works well with linear and non-linear structures. | Poor results on small datasets.<br>Easy to be overfitted. |
| [Random Forest Regression](https://csh970605.github.io/posts/Random_Forest_Regression/) | Powerful and accurate.<br>Gives good results on many data sets. | Not ideal.<br>Easy to be overfitted.<br>Number of trees to be determined. |

<br>
<br>
<br>
<br>

# Implementation

+ [Regression](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%202%20-%20Regression)
