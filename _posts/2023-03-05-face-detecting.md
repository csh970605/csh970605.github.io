---
title: Face Detecting
author: SeHoon
date: 2023-03-05 15:47:00 +0900
categories: [Machine Learning, Vision ML]
tags: [machine learning]
math: true
mermaid: true
---

# Algorithms

## Casacade Classifier
### Step 1
Prepare two sets of images.<br>
First set is positive images, while the second set is negative images.
### Step 2
Send all the images to a machine learning algorithm called AdaBoost so that it learns the features of the images as well as the details of a face.<br>
For example, a face consists of eyes, moth, nose and so on.<br>
### Step 3
<center>

<img src="https://user-images.githubusercontent.com/28240052/222949319-922710c1-b41c-4693-927a-01578783d0a6.png" width=800px><br>
[1]'casacade'<br>

</center>

this picture means if any of the features from C1 to CN is False, cascade returns 'No Detection'


### AdaBoost
AdaBoost select the features of the whole images from top left to the bottom right until it is possible to find a face.<br>
There is image below shows examples of features and the image consists of features.<br>
<center>

<img src="https://user-images.githubusercontent.com/28240052/222947707-6382c837-614f-4b9c-a55e-3ba3fa1c827d.png" width=300px height=300px><br>
[2]'examples of features'<br>

<img src="https://user-images.githubusercontent.com/28240052/222949169-c22d51bf-18b8-4427-9b22-f4dc956b8c82.png" width=500px height=500px><br>
[3]'image consists of features'<br>
</center>

at the end, we will have a matrix of numbers similar to this one below<br>

<center>
2 3 5 6<br>
8 9 2 1<br>
0 4 8 7<br>
Each number in the matrix means "white pixels - black pixels" in order in the 'examples of features' image.
</center>

### Example Code
<center>
<image src="https://user-images.githubusercontent.com/28240052/222977245-1dadabf9-7f7e-42b1-9dd8-b70f8a0ac247.png" width=500px><br>
[4] 'test image'
</center>

``` py
import cv2

face_detector = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')

image = cv2.imread('people1.jpg')
# Why use grayscale image?: Casacade detectors with opencv recommands to use grayscale images.
image_gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# scaleFactor: Image reduction ratio, default value is 1.1
# minNeighbors: Speicies how many neighboring squares must be detected to set it as the final   detection area. default is 3
# minSize: Minimum object size. (w, h) tuple
# maxSize: Maximum object size. (w, h) tuple
detections = face_detector.detectMultiScale(image_gray,
                                            scaleFactor=1.21,
                                            minNeighbors=None,
                                            minSize=None,
                                            maxSize=None)

for (x, y, w, h) in detections:
  cv2.rectangle(image, (x, y), (x+w, y+h), (0,255,0), 5)
  
cv2.imshow(image)
```
The result of code
<center>
<image src="https://user-images.githubusercontent.com/28240052/222977267-3e40e57b-1d43-4666-b1e2-f56f93ac3b5e.png" width = 500px><br>
</center>

## HOG(Histograms of Oriented Gradients)

### What is HOG?
Extract the edges of the image by color variation and consequently identify the object on the format

[1] [casacade image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[2] [examples of features image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[3] [image consists of features image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[4] [test image source](https://www.udemy.com/course/computer-vision-masterclass/)
