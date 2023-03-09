---
title: Face Detecting
author: SeHoon
date: 2023-03-05 15:47:00 +0900
categories: [Machine Learning, Vision ML]
tags: [machine learning, python]
math: true
mermaid: true
---

# Algorithms
<br>

## Casacade Classifier
---
<br>

### Step 1
---

Prepare two sets of images.<br>
First set is positive images, while the second set is negative images.
### Step 2
---
Send all the images to a machine learning algorithm called [AdaBoost](https://csh970605.github.io/posts/AdaBoost/) so that it learns the features of the images as well as the details of a face.<br>
For example, a face consists of eyes, moth, nose and so on.<br>
### Step 3
---

<center>

<img src="https://user-images.githubusercontent.com/28240052/222949319-922710c1-b41c-4693-927a-01578783d0a6.png" width=800px><br>
[1]'casacade'<br>

</center>

this picture means if any of the features from C1 to CN is False, cascade returns 'No Detection'<br><br>




### Example Code
---

I'm going to detect faces of 'test image' below by cv2
<center>

<img src="https://user-images.githubusercontent.com/28240052/222977717-9ffdbd56-0e14-46a1-9c96-bcc03c7018bb.png" width=500px height=500px><br>
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
The result of code.
<center>
<img src="https://user-images.githubusercontent.com/28240052/222977716-ab949ff9-f58b-4e02-b265-175fb176379b.png" width=500px height=500px><br>
</center><br><br>

## HOG(Histograms of Oriented Gradients)
---
### What is HOG?
---
Extract the edges of the image by color variation and consequently identify the object on the format.

There are two important concepts
- Derivative<br>
    Allows to measure the rate of changes(colors) and there are three options.
    + zero derivative<br>
        means there is no variation in the image.
    + small derivative<br>
        means there is small variation in the image.
    + high derivative derivative<br>
        means there is high variation in the image<br> EX) edge of the image.
    <br>  
    The zero derivative of the image is painted black instead of the original color like images below.<br>
    <br>
    <center>
    <img src="https://user-images.githubusercontent.com/28240052/222980227-d2ffe26c-6c6e-4afb-a39a-28af4266d3a9.png"> 
    </center>
    <br>
    So we can extract the edges of the image and consequently identify the object based on the formats.
- Gradient vector<br>
    Gradient vector indicates the direction in which the values increase.<br>
    For example, as image below shows, the gradient vector points upwards because this is where there is the greatest variation in colors from yellow to gray<br>
    <img src="https://user-images.githubusercontent.com/28240052/222979389-6b604da5-fc93-4be6-8954-6357e90e8284.png">[5] 'gradient vector image'<br><br>

    We select only that part of head, and can see several arrows pointing to where there is greater gradient vector. Also 'Gradient Direction'(direction of arrow) matrix and 'Gradient Magnitude'(size of arrow) can be made like image below.
    <br>
    <img src="https://user-images.githubusercontent.com/28240052/222981629-1d4d6447-c521-43b4-ae1e-1118bf247104.png">[8]<br>




<br>
<br>



<br>

[1] [casacade image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[2] [examples of features image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[3] [image consists of features image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[4] [test image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[5] [gradient vector image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[6] [runner image source](https://learnopencv.com/histogram-of-oriented-gradients/)<br>
[7] [converted runner image source](https://learnopencv.com/histogram-of-oriented-gradients/)<br>
[7] [converted runner image source](https://learnopencv.com/histogram-of-oriented-gradients/)<br>