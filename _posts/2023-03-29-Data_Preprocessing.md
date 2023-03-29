---
title: Data Preprocessing
author: SeHoon
date: 2023-03-29 15:30:00 +0900
categories: [Vision Machine Learning, Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Data Preprocessing?<br>
Real world data is gathered from various sources and processes and it may contain irregularities or corrupt data compromising the quality of the dataset.<br>
The typical data quality issues that arise are:

+ Incomplete: Data lacks attributes or containing missing values.<br>
+ Noisy: Data contains erroneous records or outliers.<br>
+ Inconsistent: Data contains conflicting records or discrepancies.<br><br>

Quality data is a prerequisite for quality predictive models.<br>
To avoid "garbage in, garbage out" and improve data quality and therefore model performance, it is imperative to conduct a data health screen to spot data issues early and decide on the corresponding data processing and cleaning steps.<br><br>

# How to deal with missing values?<br>
+ Deletion: Remove records with missing values<br>
There is an example of conducting Deletion<br>
```py
from sklearn.impute import SimpleImputer
import numpy as np

imputer = SimpleImputer()
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
```
<br>

+ Dummy substitution: Replace missing values with a dummy value: e.g, unknown for categorical or 0 for numerical values.<br>
There is an example of conducting Deletion<br>
```py
imputer = SimpleImputer(missing_values=np.nan, strategy='constant')
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
```
<br>

+ Mean substitution: If the missing data is numerical, replace the missing values with the mean.<br>
There is an example of conducting Deletion<br>
```py
from sklearn.impute import SimpleImputer
import numpy as np

imputer = SimpleImputer(missing_values=np.nan, strategy='mean')
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
```
<br>
<br>

+ Frequent substitution: If the missing data is categorical, replace the missing values with the most frequent item<br>
There is an example of conducting Deletion<br>
```py
from sklearn.impute import SimpleImputer
import numpy as np

imputer = SimpleImputer(missing_values=np.nan, strategy=most_frequent)
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
