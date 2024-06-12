---
title: Naive Bayes
author: SeHoon
date: 2023-04-01 15:36:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Bayes?
Bayesian analysis is a statistical paradigm that answers research questions about unknown parameters using probability statements. It can be expressed in the following formula:
<center>
<font size=4>

$ P(A\vert B) = $ $ P(B\vert A) * P(A) \over P(B) $ $ = $ $ P(A \cap B) \over P(A) $

</font>
</center>

And you can get more information about Bayes' Theroem in [here](https://csh970605.github.io/posts/Bayes_Theorem/)
<br><br>

# What is Naive bayes?

Classify the data based on the Bayesian theory. I will explain step by step below. Before starting steps, let's assume that we have a dataset like the one in the image.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229355657-a9928c9b-49b4-4bad-b0bd-b8c2d1da8873.png" width=500>
</center>
<br>
The gray dot represents a data point that we want to predict. Then we will predict the category between "Walks" and "Drives" based on probability:<br>

+ Walks probability:<br>

<center>

$ P(Walks \vert X) = $ $P(X \vert Walks) * P(Walks) \over P(X) $

</center>

+ Drives probability:
<center>

$ P(Drives \vert X) = $ $P(X \vert Drives) * P(Drives) \over P(X) $

</center>

<br><br>


## Steps of calculating probability.
---
<br>

+ Step 1<br>
Calculate probability of $ P(Walks \vert X) $

+ Step 2<br>
Calculate probability of $ P(Drives \vert X) $

+ Step 3<br>
Classify the data by the probabilities calculated in step 1 and step 2.


<br><br>

## How to calculate $ P(Walks \vert X) $?
---
<br>

+ Step 1<br>

<center>
<font size=4>

$P(Walks) = \frac{\text{Number of Walkers}}{\text{Total Observations}}$<br>

</font>
</center>

Thus, in this case, the probability of $P(Walks)$ will be $\frac{10}{30}$

+ Step 2<br>
To do this step, we must select a radius and we are going to draw a circle of your desired size around our observation like image below. Then, we will count all the points that are inside the circle. And it will be **the number of similar observations**. In this step, we are going to find P(X) which expressed by:<br>
<center>

<font size=4>

$P(X) = \frac{\text{Number of Similar Observations}}{\text{Total Observations}}$<br>
</font>

And in this case, $P(X)$ will be $\frac{4}{30}$ <br>

<img src="https://user-images.githubusercontent.com/28240052/229357205-b99be7ad-c742-4073-acbb-6330e51f2bba.png" width=400>

</center>

+ Step 3<br>

In this step, we will find $P(X \mid Walks)$, which is expressed as:<br>
<center>
<font size=4>

$P(X \mid Walks) = \frac{\text{Among those who Walk}}{\text{Total number of Walkers}} $
</font>

And in this case, $(X \mid Walks)$ will be $\frac{3}{10}$<br>
</center>

+ Step 4<br>

In this step we are going to find $P(Walks \vert X)$ and it will be:
<center>
<font size=4>

$P(Walks \mid X) = \frac{\frac {3}{10} \times \frac{10}{30}} {\frac{4}{30}} = 0.75$
</font>
</center>

# Example
<br><Br>

## Code
---
<br>

```py
from sklearn.preprocessing import StandardScaler
from sklearn.naive_bayes import GaussianNB

sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)
     
classifier = GaussianNB()
classifier.fit(X_train, y_train)

y_pred = classifier.predict(X_test)
```

<br><br>

## Result
---
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229357909-502dfc53-8cf6-4738-8b54-83820852be6e.png">
</center>
<br><br><br><br>

# Implementation

+ [Naive Bayes](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%203%20-%20Classification/Section%2018%20-%20Naive%20Bayes/Python)