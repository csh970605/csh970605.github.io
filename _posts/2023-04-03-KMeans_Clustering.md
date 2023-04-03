---
title: K-Means Clustering
author: SeHoon
date: 2023-04-03 15:18:00 +0900
categories: [Machine Learning, ML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is K-Means Clustering?

K-Means Clustering is performed by changing the centroid based on the distance between the centroid and each data point.

## Steps
---
<br>

+ Step 1<br>
Choose the number K of clusters<br>
Let's assume that K is 2, and see the data set.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229432544-a0c127ea-4ecb-42b5-8985-0e629d528213.png"width=500>
</center>

+ Step 2<br>
Select at random K points, the centroids<br>
K points can be actual points in the data set or they can be just random points.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229432947-619682c4-9d74-46f3-9d3c-980d3b652b9e.png" width=500>
</center>

+ Step 3<br>
Assign each data point to the closest centroid.<br>
This step forms K clusters<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229433370-067eee59-39fb-48c1-b915-ba9444561695.png" width=500>
</center>

+ Step 4<br>
Compute and place the new centroid of each cluster.<br>
In other words, move the position of centroids to the center of each cluster.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229434856-ee6a5256-7624-4c95-b25a-6557b44b07da.png" width=500>
</center>

+ Step 5<br>
Reassign each data point to the new closest centroid.<br>
If any reassignment took place, go to Step4, otherwise K-Means_Clustering is done.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229435190-0d8cbb77-c4a0-4cf1-b30d-4d5000088e0b.png" width=500>
<br><br>
Repeat step 4 as the clusters of some points have changed.
<br>
<img src="https://user-images.githubusercontent.com/28240052/229435629-88ec9d12-6dc4-4bfd-8118-3629b7291831.png" width=500>
<br><br>
Repeat step 4 as the clusters of some points have changed.
<br>
<img src="https://user-images.githubusercontent.com/28240052/229435757-e8f61ac3-b63b-4696-9cb8-b9c103ebec5d.png" width=500>
<br><br>
Repeat step 4 as the clusters of some points have changed.
<br>
<img src="https://user-images.githubusercontent.com/28240052/229435891-fbd6782b-bd76-49fc-8706-f1767094658e.png" width=500>
<br><br>
Clustering is done because nothing has changed.<br>
<img src="https://user-images.githubusercontent.com/28240052/229436505-0aef864d-d0f5-4a98-bcb7-8fd80a45a247.png" width=500>
<br>
</center>



<br><br>

## The K-Means Random Initialization Trap
---
<br>

# Example
<br><br>


## Code
---
<br>

```py
```

<br><br>

## Result
---
<br><br>

<center>
<img src="">
</center>