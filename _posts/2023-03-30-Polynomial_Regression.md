---
title: Polynomial Regression
author: SeHoon
date: 2023-03-30 20:32:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is polynomial regression?<br>

A simple linear regression algorithm only works when the relationship between the data is linear.<br>
However, if we have non-linear data, linear regression will not be able to draw a best-fit line.<br>
Simple regression analysis fails in such conditions.<br>
There is a dataset with a non-linear relationship, as shown in the image below. You can see that the linear regression results do not perform well, meaning they do not come close to reality. <br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229110371-52985448-6044-4e6a-8d83-3d9728c417d9.png" width=500>
</center>
<br>
To overcome this problem, we introduce polynomial regression, which helps identify the curvilinear relationship between independent and dependent variables.<br>

Polynomial regression is a form of linear regression where, due to the non-linear relationship between dependent and independent variables, we add some polynomial terms to linear regression to convert it into polynomial regression.<br>
As a result, the formula for multiple linear regression is expressed as the formula below.<br>
<center>
<font size="2">

$ y = b_{0} + b_{1}\times x + b_{2} \times x^{2}+ ... + b_{n} \times x^{n} $

</font>
</center>
<br><br>

# Example

## Code
---
<br>

```py
from sklearn.preprocessing import PolynomialFeatures
poly_reg = PolynomialFeatures(degree=4) #x^0, x^1, ~ x^n dgree
X_poly = poly_reg.fit_transform(X)
lin_reg_2 = LinearRegression()
lin_reg_2.fit(X_poly, y)
```

## Result
---
<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229107607-87fd872e-6551-4a22-a355-6892e8b8c13b.png">
</center>

<br><br><br><br>

# Implementation

+ [Polynomial Regression](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%202%20-%20Regression/Section%206%20-%20Polynomial%20Regression/Python)