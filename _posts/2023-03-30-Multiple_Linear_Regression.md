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
<br>
<br>

## Expected values
---
<br>

```
[[103015.2]
 [132582.28]
 [132447.74]
 [ 71976.1]
 [178537.48]
 [116161.24]
 [ 67851.69]
 [ 98791.73]
 [113969.44]
 [167921.07]]
```
<br>
<br>

## Predicted values
---
<br>

```
[[103282.38]
 [144259.4 ]
 [146121.95]
 [77798.83]
 [191050.39]
 [105008.31]
 [81229.06]
 [97483.56]
 [110352.25]
 [166187.94]]
```

<br><br><br><br>

# Implementation

+ [Github](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%202%20-%20Regression/Section%205%20-%20Multiple%20Linear%20Regression/Python)