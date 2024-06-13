---
title: Kernel Principal Component Analysis (Kernel PCA)
author: SeHoon
date: 2023-04-06 21:19:30 +0900
categories: [Machine Learning, ML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Kernel PCA?

[PCA](https://csh970605.github.io/posts/PCA/) is a linear algorithm whereas Kernel PCA is a non-linear algorithm.

Kernel PCA is used for:
+ Noise filtering<br>
+ Visualization<br>
+ Feature extraction<br>
+ Stock market predictions<br>
+ Gene data analysis<br>

The goals of Kernel PCA are:
+ Identifying patterns in data.<br>
+ Detect the correlation between variables.<br>

The role of Kernel PCA is:
+ Standardize the data.
+ Obtain the eigenvectors and eigenvalues from the covariance matrix or correlation matrix, or perform Singular Value Decomposition (SVD).<br>
+ Sort eigenvalues in descending order and choose the $k$ eigenvectors that correspond to the $k$ largest eigenvalues where $k$ is the number of dimensions of the new feature subspace.<br>
+ Construct the projection matrix W from the selected $k$ eigen vectors.<br>
+ Transform the original data set X via W to obtain a k-dimensional feature subspace Y.<br>


Kernel PCA can be expressed as:

<center>
<img src="https://user-images.githubusercontent.com/28240052/230393154-21b96d94-29a6-4574-94e8-ad6b0f684595.png" width=400>
</center>

<br><br><br>

# Example
<br><br>

## Code
---
<br>

```py
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import KernelPCA
from sklearn.linear_model import LogisticRegression

sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)

kpca = KernelPCA(n_components=2, kernel='rbf')
X_train = kpca.fit_transform(X_train)
X_test = kpca.transform(X_test)

classifier = LogisticRegression(random_state = 0)
classifier.fit(X_train, y_train)

y_pred = classifier.predict(X_test)
```

<br><br>

## Result
---
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/230393501-3cd4c65d-3586-4a72-9229-4e6bd5402015.png">
</center>
<br><br><br><br>

# Implementation

+ [Kernel pca](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%209%20-%20Dimensionality%20Reduction/Section%2045%20-%20Kernel%20PCA/Python)