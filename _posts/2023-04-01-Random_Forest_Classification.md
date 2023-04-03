---
title: Random Forest Classification
author: SeHoon
date: 2023-04-01 15:37:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Random Forest Classification?

It's basic algorithm is the same as [Random Forest Regression](https://csh970605.github.io/posts/Random_Forest_Regression/) except that predicting a value sets a category.<br><br><br>

# Example
<br><br>
## Code
---
<br>

```py
from sklearn.ensemble import RandomForestClassifier
from sklearn.preprocessing import StandardScaler

sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)

classifier = RandomForestClassifier(n_estimators = 100, criterion = 'entropy', random_state = 0)
classifier.fit(X_train, y_train)

y_pred = classifier.predict(X_test)
```

<br><br>

## Result
---
<br>

<center>
<img src="">
</center>