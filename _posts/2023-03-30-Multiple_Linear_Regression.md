---
title: Multiple Linear Regression
author: SeHoon
date: 2023-03-30 20:32:00 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Multiple Linear Regression?
Multiple linear regression is used to estimate the relationship between two or more independent variables(X) and one dependent variable(Y): <br>
+ X is regarded as the predictor, explanatory, or independent variable.
+ Y is regarded as the response, outcome, or dependent variable.
As a result, the formula for multiple linear regression is expressed as the formula below.<br>
<center>
<font size="2">

$ y = b_{0} + b_{1}*x_{1} + b_{2}*x_{2}+ ... + b_{n}*x_{n} $

</font>
</center>
You can use multiple linear regression when you want to know:<br>

+ How strong the relationship is between two or more independent variables and one dependent variable (e.g. how rainfall, temperature, and amount of fertilizer added affect crop growth).<br>
+ The value of the dependent variable at a certain value of the independent variables (e.g. the expected yield of a crop at certain levels of rainfall, temperature, and fertilizer addition).<br>
<br>

# Example<br>
<br>

## Code
---
<br>

```py
from sklearn.linear_model import LinearRegression
regressor = LinearRegression()
regressor.fit(X_train, y_train)
```
