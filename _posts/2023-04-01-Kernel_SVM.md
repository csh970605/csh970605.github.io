---
title: Kernel Support Vector Machine(Kernel SVM)
author: SeHoon
date: 2023-04-01 15:36:00 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is kernel SVM?

It is a concept that came out to compensate for the disadvantage that SVM cannot handle non linear datasets like image below.<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229292582-16000507-a769-45fb-9971-556652d1cae7.png" width=400>
</center>

<br><br>
Then, how kernel SVM classify non linear dataset? The answer is mapping to a higher dimension like image below.<br>
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229292858-a3b8faf2-edf1-4971-a8ed-e86514aeef72.png" width=500>
</center>

<br><br>

By mapping to a higher dimension, we can get a linearly separable dataset divided by hyperplane in the space.<br>
After going through the above process, if you project to the lower dimension again, you can get a result with a round hyperplane like the image below.

<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229293177-8c5bfff4-05d1-48f1-a51b-7d3048563c05.png" width=400>
</center>

<br><br>

If then, kernel SVM can classify more complex data set like image below?<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229293702-4fef8e9c-c9b6-474d-85c7-d991c3024a75.png" width=500>
</center>

The answer is YES. By adding more than two kernel formula like Gaussian RBF Kernel, it can classify data set.

There are simple Gaussian RBF kernel formula:<br>

<center>
<font size=4>

$K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{1} ) = $ $e^{-\vert \vec{x} - \vec{l} \vert^{2}\over 2\sigma^{2} }$

</font>
</center>

<br>
So, the result of kernel SVM will appear like this:
<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229294023-acb80d4f-4ba3-4691-b259-d8af7d7b07b8.png" width=500>
</center>

<br>

+ Green when:<br>
$K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{1} )$ $+ K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{2} ) > 0$
+ Red when:<br>
$K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{1} )$ $+ K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{2} ) = 0$


# Types of Kernel Function

+ Gaussian RBF Kernel<br>
<center>
<font size=4>

$K($ $\overrightarrow{x}$ $, \overrightarrow{l}^{1} ) = $ $e^{-\vert \vec{x} - \vec{l} \vert^{2}\over 2\sigma^{2} }$

</font>
<br>
<img src="https://user-images.githubusercontent.com/28240052/229349560-87dfa4f1-9c4c-4470-a620-683afda441fe.png" width=400>
</center>

+ Sigmoid Kerenel<br>
<center>
<font size=4>

$K(X, Y) = $ $\tanh(\gamma*X^{T}Y + r)$

</font>
<br>
<img src="https://user-images.githubusercontent.com/28240052/229349566-c33c86e5-bd69-4bf8-8264-2569c4cf132b.png" width=400>
</center>

+ Polynomial Kernel<br>
<center>
<font size=4>

$K(X,Y) = $ $(\gamma*X^{T}Y + r)^{d},r > 0$

</font>
<br>
<img src="https://user-images.githubusercontent.com/28240052/229349574-07be2253-3ac9-4fdf-9571-79eb88061f2b.png" width=400>
</center>

# Example
<br><br>

## Code
---
<br>

```py
from sklearn.preprocessing import StandardScaler
from sklearn.svm import SVC
sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)


classifier = SVC(kernel='rbf', random_state=0)
classifier.fit(X_train, y_train)

y_pred = classifier.predict(X_test)
```

<br><br>

## Result
---
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229349843-0c56decd-f08f-4866-b709-7394c13f3347.png">
</center>