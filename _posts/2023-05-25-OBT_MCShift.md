---
title: Motion Tracking with Mean Shift & CAM SHIFT
author: SeHoon
date: 2023-05-25 20:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Mean Shift?
Mean shift is a hill climbing algorithm which involves shifting this kernel iteratively to a higher density region until convergence. Every shift is defined by a mean shift vector. The mean shift vector always points toward the direction of the maximum increase in the density.<br><br>

Consider we have a set of points. We are given a small window and we have to move that window to the area of maximum pixel density. It takes several steps given below:
<br><br><br><br>

## Steps of Meanshift Object Tracking
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/e50fb457-b8ef-4c99-8da9-6dc71fc3ada2" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/31981580-a933-4db2-bb8c-99b797c6d9c4" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3dd6271a-98a9-4d19-b3bd-2900e8c2b6bb" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/008491db-6109-4e92-9e4f-40417b0d5490" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/8aa235dd-f952-445d-ab5b-9b7a2be7b6dd" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/f27ba0af-b61d-4dd3-b738-1ba6ebd560fe" width=500 height=500>
<br><br>
</center>

During those steps, we use two main methods :
+ **cv2.calBackProject(images, channels, hist, ranges, scale)** : This method calculates the back project of the histogram. That is, at each location (x, y) the function collects the values from the selected channels in the input images and finds the corresponding histogram bin. But instead of incrementing it, the function reads the bin value, scales it by scale , and stores in backProject(x,y).<br>

    + images : input image. But the image must be in [].
    + channels : The list of channels used to compute the back projection. But it must be in [].
    + hist : Input histogram that can be dense or sparse.
    + ranges : Array of arrays of the histogram bin boundaries in each dimension.
    + scale : Optional scale factor for the output back projection.
<br><br>

+ **cv2.meanShift(probImage, window, criteria)** : Finds an object on a back projection image.<br>

    + probImage : Back projection of the object histogram from calBackProject.
    + window : Initial search window.
    + criteria : Stop criteria for the iterative search algorithm. It has three parameters as an input which is:<br>

        + type : 
            + cv2.TERM_CRITERIA_EPS = Stop iteration until reach at the epsilon.
            + cv2.TERM_CRITERIA_MAX_ITER = Stop iteration until reach at the max_iter.
            + cv2.TERM_CRITERIA_EPS + cv2.TERM_CRITERIA_MAX_ITER = Stop iteration until one of the two conditions is fulfilled.
        + max_iter : Max iteration number.
        + epsilon : Accuracy.

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/f4e1d41e-cfa1-4f59-b387-6862a85651f2" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/bee6bb19-2525-491a-b9a4-ce4d9a2f02b7" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/a6840381-c6c9-4b7c-ba55-04a049aa4b9f" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/fff8641a-6346-42bc-b194-798586cea46c" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/5f495d69-9f4e-47f7-98e4-41dc604626ce" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/65225303-bbc0-432c-b323-b2651eec3c2b" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/73398615-f1a4-4615-be73-e722bdeecf89" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/031504c9-80b3-4bf0-b0de-90d4c905c98c" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/cad9c65c-f423-4142-a682-c8ac6d08a2d5" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/7606208f-47d1-4408-9512-4c4b01d5339c" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/6ed9bbf5-b013-4638-883a-91cd74316cbf" width=500 height=500>
</center>

<br><br><br><br>


# What is Cam Shift Object Tracking?
It is almost same as meanshift, but it returns a rotated rectangle and box parameters (used to be passed as search window in next iteration). It takes several steps given below:
<br><br><br><br>

## Steps of Cam Shift
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/991ae5bd-24fb-4f4b-a0cd-2c40d08e5f1a" width=500 height=500>
<br><br>
</center>

During those steps, we use two main methods :
+ **cv2.calBackProject(images, channels, hist, ranges, scale)** : This method calculates the back project of the histogram. That is, at each location (x, y) the function collects the values from the selected channels in the input images and finds the corresponding histogram bin. But instead of incrementing it, the function reads the bin value, scales it by scale , and stores in backProject(x,y).<br>

    + images : input image. But the image must be in [].
    + channels : The list of channels used to compute the back projection. But it must be in [].
    + hist : Input histogram that can be dense or sparse.
    + ranges : Array of arrays of the histogram bin boundaries in each dimension.
    + scale : Optional scale factor for the output back projection.
<br><br>

+ **cv2.camShift(probImage, window, criteria)** : Finds an object on a back projection image.<br>

    + probImage : Back projection of the object histogram from calBackProject.
    + window : Initial search window.
    + criteria : Stop criteria for the iterative search algorithm. It has three parameters as an input which is:<br>

        + type : 
            + cv2.TERM_CRITERIA_EPS = Stop iteration until reach at the epsilon.
            + cv2.TERM_CRITERIA_MAX_ITER = Stop iteration until reach at the max_iter.
            + cv2.TERM_CRITERIA_EPS + cv2.TERM_CRITERIA_MAX_ITER = Stop iteration until one of the two conditions is fulfilled.
        + max_iter : Max iteration number.
        + epsilon : Accuracy.

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/599e9c9e-15ed-46b9-8bb2-538ed5dfef57" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/6041fa11-2a5f-4572-a227-ade3f82086e5" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/81296a1d-8394-471d-84a3-b7b28b404525" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/dbe4bd39-3953-427e-a42d-b1565d3344d1" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/998e8c90-0cfe-4cea-a776-2ea3f91281de" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/fdd8265e-030c-417d-a6d8-f620d226afe6" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/4425b9a1-3f41-4313-8690-506cbd842104" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3c946abc-70c2-4bcb-ad55-ff8bb2ec583d" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/37693566-bd0b-433f-ac8d-7632b56b5627" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/1acd5e01-5726-4d3f-b0ed-50a0e3bd090c" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/b464a512-6399-4adc-ab4f-745af7b6a507" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/b4c86fa0-b1cf-4d82-9b2f-b82a2390a7a2" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/18c4d3b4-c271-4385-a77f-8a27d80b074e" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/019aa73d-3e34-4b7b-990b-916d7c07046c" width=500 height=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/a30a78ad-8436-4369-bc91-b9e20137c310" width=500 height=500>
</center>
<br><br><br><br>

# Implementation

+ [Motion Tracking with Mean Shift and CAMSHIFT](https://github.com/csh970605/Modern_Computer_Vision/blob/main/OpenCV/24.%20Motion%20Tracking%20with%20Mean%20Shift%20and%20CAMSHIFT.ipynb)