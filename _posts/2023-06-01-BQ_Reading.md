---
title: Barcode & QR Reading
author: SeHoon
date: 2023-06-01 18:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# How to read Barcode & QR?
It can be done simply by **pyzbar.pyzbar.decode(input image) -> [tuple]**.<br>
The return tuple includes:

+ **data** : The data contained in a barcode or QR code. We can get the data by **decode(image).data.decode()**

+ **type** : Represent whether it is a barcode or QR code. We can get the type by **decode(image).type**

+ **rect** : Represent the bounding box of the detected barcode & QR code.

+ **polygon** :  Represent the detected area of barcode & QR code.

+ **quality** : The quality of the detected barcode & QR code.

+ **orientation** : There are five values of orientation which are :<br>

    + **UNKNOWN** : When pyzbar are unable to determine orientation.

    + **UP** : Upright, read left to right.

    + **RIGHT** : Sideways, read top to bottm.

    + **DOWN** : Upside-down, read right to left.

    + **LEFT** : Sideways, read bottom to top.

<br><br><br><br>
    
# Implementation

[Barcode Generation and Reading](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/32.%20Barcode%2C%20QR%20Generation%20and%20Reading.ipynb)

