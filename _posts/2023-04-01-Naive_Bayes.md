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
Bayesian analysis is a statistical paradigm that answers research questions about unknown parameters using probability statements.<br>
It can be expressed in the following formula:
<center>
<font size=4>

$ P(A\vert B) = $ $ P(B\vert A) * P(A) \over P(B) $ $ = $ $ P(A \cap B) \over P(A) $

</font>
</center>
<br><br>

# What is Naive bayes?

Classify the data based on the Bayesian theory. I will explain step by step below.<br>
Before starting steps, let's assume that we have a data set like image.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229355657-a9928c9b-49b4-4bad-b0bd-b8c2d1da8873.png" width=500>
</center>
<br>
Green dot is a data that we want to predict.<br>
Then we will predict the category between "Walks" and "Drives" by probability:<br>

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

$ P(Walks) = $ $ Number of Walkers \over Total Observations$<br>

</font>
</center>

Thus, in this case P(Walks)'s probability will be 
<font size=4>
$ 10 \over 30 $
</font>

+ Step 2<br>
To do this step, we must select a radius and we are going to draw a circle of your desired size around our observation like image below.<br>
Then, we are going to count all the points that are inside the circle.<br>
And it will be **number of similzr observations**.<br>
In this step, we are going to find P(X) which expressed by:<br>
<center>

<font size=4>

$ P(X) = $ $ Number of Similar Observations \over Total Observations $<br>
</font>

And in this case, P(X) will be $ 4 \over 30 $ <br>

<img src="https://user-images.githubusercontent.com/28240052/229356365-8e146f78-d768-412d-90aa-c367476d78c5.png"width=400><br>

</center>



+ Step 3<br>
+ Step 4<br>

# Example
<br><Br>

## Code
---
<br>

```py
```

<br><br>

## Result
---
<br>




<center>
<img src="">
</center>