---
title: Logistic Classification
author: SeHoon
date: 2023-04-01 15:34:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Logistic Regression?

Logistic regression is an example of supervised learning. It is used to calculate or predict the probability of a binary event occurring.<br><br>

Let's assume that you have a data set like image below.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229272192-58cc6629-5a1e-4380-b7d5-5246e02ec263.png" width=500>
</center>
<br>

How do you predict a value using linear regression, such as [Simple Linear Regression](https://csh970605.github.io/posts/Simple_Linear_Regression/) or [Multiple Linear Regression](https://csh970605.github.io/posts/Multiple_Linear_Regression/)?<br>
If you use linear regression on the data set above, you will get a graph like image below.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229272509-640be045-6204-4de1-b3e0-34290f6cf372.png" width=500>
</center>
<br><br>
But what hint does linear regression give us? As shown in the graph, as people get older, they take action more often, and when they are younger, they take action less often. <br>
<br>
So, if you draw a graph applying this to the extreme, you get a graph like the image below.
<br><br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229272859-9228569a-59f7-4029-90d1-16bbdf2b8d85.png" width=500>
</center>
<br><br>

To make the graph less extreme, we use the **sigmoid function** with the formula.<br>
Let's assume the formula for a straight line:

<center>
<font size=4>

$y = $ $b_{0} + b_{1}*1$

</font>
</center>

And the formula for the sigmoid function is:

<center>
<font size=4>

$p = \frac{1}{1 + e^{-y}}$

</font>
</center>

<br>
Combining the two formulas gives the formula shown below, which is the formula of logistic regression:
<br><br>

<center>
<font size=4>

$\ln \left(\frac{p}{1-p}\right) = b_{0} + b_{1}*1$

</font>
</center>
<br>
And the graph will be drawn like:
<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229273522-ee686681-5964-4e42-8c8d-24b5b3c42756.png" width=500>
<br><br>
</center>
<br>
So, how can we use this graph? You can get the probabilities for each age like image below.<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229273624-044ae587-480c-49ce-a001-0a933808db52.png" width=500>
</center>
<br><br>

After getting the probabilities, classify them as 0 or 1 based on a specific threshold, as shown in the image below.
<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229273727-10025abc-79fb-4ff6-bcc5-ce7ccafd3841.png" width=500>
</center>
<br><br>

# Example
<br><br>

## Code
---
<br>

```py
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression

sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)

classifier = LogisticRegression()
classifier.fit(X_train, y_train)

y_pred = classifier.predict(X_test)
```

<br><br>

## Result
---
<br>

<center>

<img src="https://user-images.githubusercontent.com/28240052/229273892-bc1cf78f-1299-4d96-a904-28b98eb66dad.png">

</center>
<br><br><br><br>

# Implementation

+ [Logistic Classification](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%203%20-%20Classification/Section%2014%20-%20Logistic%20Regression/Python)