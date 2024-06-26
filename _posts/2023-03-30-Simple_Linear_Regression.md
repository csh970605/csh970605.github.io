---
title: Simple Linear Regression
author: SeHoon
date: 2023-03-30 20:31:00 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Simple Linear Regression?
Simple linear regression is a statistical method that allows us to summarize and study relationships between two continuous (quantitative) variables:<br>
+ The first variable $X$ is regarded as the predictor, explanatory, or independent variable.
+ The second variable $Y$ is regarded as the response, outcome, or dependent variable.

As a result, the formula for simple linear regression is expressed as the formula below.

<center>

$y = ax + b$

</center>
You can use simple linear regression when you want to know:<br>

+ How strong the relationship is between two variables (e.g., the relationship between rainfall and soil erosion).<br>
+ The value of the dependent variable at a certain value of the independent variable (e.g., the amount of soil erosion at a certain level of rainfall).

<br>
<br>


## How is the formula made?
---
<br>
<img src="https://user-images.githubusercontent.com/28240052/228837755-7d5f25f7-6019-40f0-ad0f-2dc8ea71eaaf.png"><br><br>

As you can see in the image above, there are **red crosses (y<sub>i</sub>)** representing actual salaries based on experience. The **green crosses (y<sub>i</sub><sup>^</sup>)** are the modeled values, representing the salary at a given experience level. The **green lines** represent the difference between the actual salary and the modeled salary.The goal is to find the straight line where the sum of the distances of the green lines is minimized, which becomes the **black line**.


<br><br><br><br>

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

## Test Result
---
<br>

<img src="https://user-images.githubusercontent.com/28240052/228832522-e0c51a1d-e67b-46e3-91e7-be3f0585c228.png">
<br><br>

## Prediction Result
---
<br>
<img src="https://user-images.githubusercontent.com/28240052/228832697-0753bf0b-877b-46e2-9578-91ce5208f19e.png">


<br><br><br><br>

# Implementation
+ [Simple Linear Regression 1](https://github.com/csh970605/TensorFlow-2.0-Practical/blob/main/Section%202/Develop_A_Single_Neuron_Model_to_Convert_C_to_F.ipynb) 

+ [Simple Linear Regression 2](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%202%20-%20Regression/Section%204%20-%20Simple%20Linear%20Regression/Python)