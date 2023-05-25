---
title: Watershed
author: SeHoon
date: 2023-05-25 12:11:00 +0900
categories: [Vision Machine Learning, OpenCV]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Watershed Algorithm?
Any grayscale image can be viewed as a topographic surface where high intensity denotes peaks and hills while low intensity denotes valleys. This algorithm uses that analogy and starts filling those low points (valleys) with a different colored label.<br>
<br>
As the water rises, depending on the peaks (gradients) nearby, water from different valleys, obviously with different colors will start to merge. To avoid that, we build barriers in the locations where water merges. Continuing the work of filling water and building barriers until all the peaks are under water. Those barriers we created gives us the segmentation result. This is the "philosophy" behind the watershed.<br>
<br>
Their approach however, gives us oversegmented result due to noise or any other irregularities in the image. Thus, OpenCV implemented a marker-based watershed algorithm where you specify which are all valley points are to be merged and which are not. It gives different labels for our object we know. Label the region which we are sure of being the foreground or object with one color, label the region which we are sure of being background or non-object with another color and finally the region which we are not sure of anything, label it with 0. That is our marker.<br><br>
Then apply watershed algorithm. Then our marker will be updated with the labels we gave, and the boundaries of objects will have a value of -1.
<br><br><br><br>

## Steps of watershed
---
<br>

1. [Thresholding](https://csh970605.github.io/posts/Thresholding/)
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/b3af3ff7-9c6a-4e68-a372-ee0a072e241b" width=500>
</center>
<br><br>

2. Get foreground<br>
It can be done by thresholding the output of **cv2.distanceTransform(src, distanceType, markSize)** where<br>

    + src : 8-bit, single-channel (binary) source image. In my case I used [morphologied](https://csh970605.github.io/posts/Edge_Detecting/) image
    + distanceType : Type of distance
    + markSize : Size of the distance transform mask.

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/6fb2fee3-fb0f-4688-9eaa-fc5a31decbd5" width=500>
</center>
<br><br>

3. Get Background<br>
It can be done by [dilating](https://csh970605.github.io/posts/Edge_Detecting/) the thresholded original image.

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/b144ed71-a521-4f22-98a9-0669b1cf5d85" width=500>
</center>
<br><br>

4. Get unkown region.<br>
It can be done by **cv2.subtract(src1, src2)**.
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3043521a-cda1-4b60-a5bb-14fbd06b87d3" width=500>
</center>
<br><br>

5. Get boundaries<br>
Perform **cv2.connectedComponents(image)** with foreground that we got at step 2 to determines the connectivity of blob-like regions in a binary image. Then, make the all values to 1 except unkown area.

<br><br><br><br>

## Types of distance
---
<br>

+ DIST_USER : User defined distance.
+ DIST_L1 : distance = $|x1-x2| + |y1-y2|$
+ DIST_L2 : the simple euclidean distance
+ DIST_C : distance = $max(|x1-x2|,|y1-y2|)$
+ DIST_L12 : L1-L2 metric: distance = $2(\sqrt{1+x*\frac{x}{2}} - 1)$
+ DIST_FAIR : distance = $c^2(\frac{|x|}{c}-log(\frac{1+|x|}{c}))$, c = 1.3998
+ DIST_WELSCH : distance = $\frac{c^{2}}{2}(1-e^{-(x/c)^{2}}), c = 2.9846$
+ DIST_HUBER : distance = $|x|<c\ ?\ \frac{x^{2}}{2}\ :\ c(|x|-\frac{c}{2}), c=1.345$
<br><br><br><br>

## Distance Transform Masks
---
<br>

+ DIST_MASK_3 : mask = 3
+ DIST_MASK_5 : mask = 5
<br><br><br><br>

## Result
---
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/9f532b0b-971f-442a-bd0e-5624cf783336" width=500>
<br><br>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/5f131096-72f7-4de0-b924-0cd4214d9651" width=500>
</center>


<br><br><br><br>

# Implementation

+ []()

<center>
<img src="" width=500>
</center>
<br><br>