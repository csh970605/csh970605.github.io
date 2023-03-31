---
title: Decision Tree Regression
author: SeHoon
date: 2023-03-30 20:33:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is decision tree regression?

The entire data set (parent node) is divided into two data sets (child nodes) based on the reference value.<br>
Repeat the above steps for each child node to create child nodes until only one class of data exists in the child node.<br>

There are example images below that shows step by step how nodes are made.<br>

## Step 1
---
<br>
The data set is scattered across a graph with axes X<sub>1</sub> and X<sub>2</sub>.<br>
<br>
<img src="https://user-images.githubusercontent.com/28240052/229128756-ab197b8e-8562-4532-a684-b12eacce65b4.png">

<br><br>

## Step 2
---
<br>

Make a split 1 by reference value(X<sub>1</sub> < 20)<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229129540-78388bd2-9b8f-41d3-adb3-e207a1927497.png" width=500>
<br><br><br>
<img src="https://user-images.githubusercontent.com/28240052/229130283-99771b50-821d-4717-95a4-f006f2029acb.png" width=500>
<br><br>
</center>

## Step 3
---
<br>

Make a split 2 by reference value(X<sub>2</sub> < 170)<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229130931-f7a6df86-0e24-4b9a-9331-2c1cfff1e3be.png" width=500>
<br><br><br>
<img src="https://user-images.githubusercontent.com/28240052/229131405-ac932f3c-437d-4afb-805d-53389beeadda.png" width=500>
<br><br>
</center>

## Step 4
---
<br>
Make a split 3 by reference value(X<sub>2</sub> < 170)<br><br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229131654-a44519f5-efb0-4dca-bbd0-415c054eb9f8.png" width=500>
<br><br><br>
<img src="https://user-images.githubusercontent.com/28240052/229132446-bb941561-91c2-4dd9-a6b3-dcfacdb58195.png" width=500>
<br><br>
</center>

## Step 5
---
<br>
Make a split 4 by reference value(X<sub>1</sub> < 40)<br><br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229135492-ad5e5a75-3aaa-4803-83d3-aa07afd66b3b.png" width=500>
<br><br><br>
<img src="https://user-images.githubusercontent.com/28240052/229132724-57601288-8664-4d0c-bb66-695a38b71a48.png" width=500>
<br><br>
</center>


# Example
<br><br>

## Code
---
<br>

```py
from sklearn.tree import DecisionTreeRegressor
regressor = DecisionTreeRegressor(random_state=0)
regressor.fit(X, y)
X_pred = regressor.predict(X_grid)
```
<br><br>

## Result
---
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229133296-912a6c73-4569-47e5-9dcf-72e6aa332472.png" width=500>
</center>