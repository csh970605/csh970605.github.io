---
title: Random Forest Regression
author: SeHoon
date: 2023-03-30 20:34:00 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is random forest regression?

Random forest regression is a type of ensemble learning, which is the process of using multiple models, trained over the same data, averaging the results of each model to ultimately find a more powerful predictive/classification result.<br><br>

## The process of making a random forest regression
---
<br>

+ Step 1: Pick at random K data points from the Training set.<br>
+ Step 2: Build the decision tree associated with these K data points.<br>
+ Step 3: Choose the number of trees you want to build and repeat steps 1 and 2.<br>
+ Step 4: For a new data point, make each one of your trees predict the value of **Y** for the data point in question. Then, assign the new data point the average of all the predicted Y values.<br>

# Example
<br><br>

## Code
---
<br>

```py
from sklearn.tree import DecisionTreeRegressor
regressor = DecisionTreeRegressor()
regressor.fit(X, y)
regressor.predict(X)
```
<br><br>

## Result
---
<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229138964-12e1e078-c765-4a50-9250-b54c25f79216.png" width=500>
</center>

<br><br><br><br>

# Implementation

+ [Decision Tree Regression](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%202%20-%20Regression/Section%209%20-%20Random%20Forest%20Regression/Python)