---
title: Face Detecting
author: SeHoon
date: 2023-03-05 15:47:00 +0800
categories: [Machine Learning, Vision ML]
tags: [machine learning]
math: true
mermaid: true
---

# Algorithms

## Casacade Classifier
### Step 1
Prepare two sets of images.<br>
First set is positive images, whiel the second set is negative images.
### Step 2
Send all the images to a machine learning algorithm called AdaBoost so that it learns the features of the images as well as the details of a face.<br>
For example, a face consists of eyes, moth, nose and so on.<br>
### Step 3
<center>

<img src="https://user-images.githubusercontent.com/28240052/222949319-922710c1-b41c-4693-927a-01578783d0a6.png" width=800px><sup id="a1">[1](#f1)</sup><br>

'casacade'<br>

</center>

this picture means if any of the features from C1 to CN is False, cascade returns 'No Detection'


### AdaBoost
AdaBoost select the features of the whole images from top left to the bottom right until it is possible to find a face.<br>
There is image below shows examples of features and the image consists of features.<br>
<center>

<img src="https://user-images.githubusercontent.com/28240052/222947707-6382c837-614f-4b9c-a55e-3ba3fa1c827d.png" width=300px height=300px><sup id="a2">[2](#f2)</sup><br>
'examples of features'<br>

<img src="https://user-images.githubusercontent.com/28240052/222949169-c22d51bf-18b8-4427-9b22-f4dc956b8c82.png" width=500px height=500px><sup id="a3">[3](#f3)</sup><br>
'image consists of features'<br>
</center>

at the end, we will have a matrix of numbers similar to this one below<br>
<center>

```text
2 3 5 6
8 9 2 1
0 4 8 7
Each number in the matrix means "white pixels - black pixels" in order in the 'examples of features' image.
```
</center>


## HOG(Histograms of Oriented Gradients)







<b id="f1">1</b> image source: https://www.udemy.com/course/computer-vision-masterclass/<br>
<b id="f2">2</b> image source: https://www.udemy.com/course/computer-vision-masterclass/<br>
<b id="f3">3</b> image source: https://www.udemy.com/course/computer-vision-masterclass/
