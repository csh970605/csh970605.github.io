---
title: Casacade Classifier
author: SeHoon
date: 2023-03-10 15:10:00 +0900
categories: [Machine Learning, Vision ML]
tags: [machine learning, python]
math: true
mermaid: true
---

# Casacade Classifier

## Step 1
---

Prepare two sets of images.<br>
First set is positive images, while the second set is negative images.
## Step 2
---
Send all the images to a machine learning algorithm called [AdaBoost](https://csh970605.github.io/posts/AdaBoost/) so that it learns the features of the images as well as the details of a face.<br>
For example, a face consists of eyes, moth, nose and so on.<br>
## Step 3
---

<center>

<img src="https://user-images.githubusercontent.com/28240052/222949319-922710c1-b41c-4693-927a-01578783d0a6.png" width=800px><br>
[1]'casacade'<br>

</center>

this picture means if any of the features from C1 to CN is False, cascade returns 'No Detection'<br><br>




## Example Code
---

I'm going to detect faces of 'test image' below by openCV
<center>

<img src="https://user-images.githubusercontent.com/28240052/222977717-9ffdbd56-0e14-46a1-9c96-bcc03c7018bb.png" width=500px height=500px><br>
[2] 'test image'

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

---
[1] [casacade image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>
[2] [test image source](https://www.udemy.com/course/computer-vision-masterclass/)<br>