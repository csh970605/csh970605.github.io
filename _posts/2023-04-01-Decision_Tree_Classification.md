---
title: Decision Tree Classification
author: SeHoon
date: 2023-04-01 15:37:00 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---


# What is Decision Tree Classification?

It's basic algorithm is the same as [Decision Tree Regression](https://csh970605.github.io/posts/Decision_Tree_Regression/).<br>
You can find the difference in the image below.
<br>
<center>
<font size=4>
Decision Tree Classification
<br>
<img src="https://user-images.githubusercontent.com/28240052/229423625-25378b8d-ba9d-43a9-be70-d280084b5b87.png" width=500>
<br><br>
Decision Tree Regression<br>
<img src="https://user-images.githubusercontent.com/28240052/229132724-57601288-8664-4d0c-bb66-695a38b71a48.png" width=500>
</font>
</center>

<br><br>

# Example
<br><Br>

## Code
---
<br>

```py
from sklearn.tree import DecisionTreeClassifier
from sklearn.preprocessing import StandardScaler

sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)

classifier = DecisionTreeClassifier(criterion = 'entropy', random_state = 0)
classifier.fit(X_train, y_train)

y_pred = classifier.predict(X_test)
```

<br><br>

## Result
---
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229425026-e5b37c40-4d8d-49ce-ad75-8ebef0b3b458.png">
</center>

<br><br><br><br>

# Implementation

+ [Decision Tree Classification](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%203%20-%20Classification/Section%2019%20-%20Decision%20Tree%20Classification/Python)