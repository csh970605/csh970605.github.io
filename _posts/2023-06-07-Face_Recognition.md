---
title: Face-Recognition
author: SeHoon
date: 2023-06-07 16:32:00 +0900
categories: [Vision Machine Learning, VML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Face-Recognition?
In this post, we are not talking about [face recognition](https://csh970605.github.io/posts/Face-Recognition/) theory. Instead, we are going to talk about the module face-recognition.
<br>
It works as same as face recognition. Let's see how to recognize face by the module.
<br><br><br><br>

## Steps of Face-Recognition
---
<br>

1. Load images and learn how to recognize it. The images can be loaded by **face_recognition.load_image_file(file)** where:<br>

    + file : image file name or file object to load.
    <br><br>

2. Convert the images to prepare comparsion group. The images can be converted by **face_recognition.face_encodings(face_image, known_face_locations=None, num_jitters=1, model='small')** where:<br>

    + face_image : Input image.

    + known_face_locations : The bounding boxes of each face if you already know them.

    + num_jilters : How many times to re-sample the face when calculating encoding.

    + model : Which model to use. "Large" or "Small"
    <br><br>

3. Create two lits of known face encodings and their names.

4. Get the face location of the target image by **face_recognition.face_locations(img, number_of_times_to_upsample=1, model='hog')** where:<br>

    + img : Input iamge.

    + number_of_times_to_upsample : How many times to upsample the image looking for faces.

    + model : Which face detection model to use. ['hog'](https://csh970605.github.io/posts/HOG/) is less accurate but faster on CPUs. ['cnn'](https://csh970605.github.io/posts/CNN/) is a more accurate deep-learning model which is GPU/CUDA accelerated.
    <br><br>

5. Encoding the image by using**face_recognition.face_encodings()** again. Note that we should use the tuples that obtain from Step 4.

6. Compare the data between we obtained at Step 5 and we prepared at Step 3 by using **face_recognition.compare_faces(known_face_encodings, face_encoding_to_check, tolerance=0.6)** where:<br>

    + known_face_encodings : A list of known face encodings.

    + face_encoding_to_check : A single face encoding to compare against the list.

    + tolerance : How much distance between faces to consider it a match.


<br><br><br><br>

# Implementation

+ [Face Recognition](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/40.%20Facial%20Recognition.ipynb)

