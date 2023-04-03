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
<img src="https://user-images.githubusercontent.com/28240052/229432544-a0c127ea-4ecb-42b5-8985-0e629d528213.png" width=500>
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
The K-Means random initialization trap is that the result is a bit more different than expected.

<center>
<img src="https://user-images.githubusercontent.com/28240052/229455796-23ca500b-9f1f-47e0-8a4c-ed6be81557bc.png" width=500>
</center>

<br>
How are clusters created in this dataset when K=3?<br><br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229447417-5ee0f01f-edad-415d-b8d8-4962e3ecd063.png" width=500>
</center>
<br>
Clustering like image above would be ideal.<br>
However, as we mentioned in [Step 2](https://csh970605.github.io/posts/KMeans_Clustering/#steps) the centroid can be made randomly.<br>
Then, if centroids are made like image below, is there any difference between what expected?
<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/229448112-6d8feb04-3b5e-4a97-b6d1-6d1d614620d7.png" width=500>
</center>
<br><br>
The answer is yes. As you can see image below, the result is a bit more different than we expected.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229448431-e947744f-66ff-4f8e-9411-71199f2a8374.png" width=500>
</center>
<br><br><br>

To solve this problem, K-Means++ exists, but it can still happen.<br>
So, it would be good idea to be aware of this issue.<br>
<br><br>

## How to choose the ideal numbers of K?
---
<br>

We can choose K by WCSS:

<center>
<font size=2>

$ WCSS = \displaystyle\sum_{P_{i} in Cluster 1}^{}{distance(P_{i},C{1})^2} + \displaystyle\sum_{P_{i} in Cluster 2}^{}{distance(P_{i},C{2})^2} + ... + \displaystyle\sum_{P_{i} in Cluster n}^{}{distance(P_{i},C{n})^2}$
</font>
</center>
<br><br>

**The lower value of WCSS, the more sophisticated the performance.<br>
Also, the lower value of WCSS, the longer the execution time.**<br>

<br>
Then, how to choose K?<br> 
What I recommend is to choose a value for K when there is no more significant change in WCSS value in the graph anymore.<br>
<br>
Look at this graph:
<center>
<img src="https://user-images.githubusercontent.com/28240052/229453020-844921e8-8db1-4e79-8ff2-bd90d78dfcac.png" width=500>
</center>
<br><br><br>

When K is 3, there is no more significant change in WCSS value in the graph.<br>
That's why I pick K as 3.<br>

# Example
<br><br>


## Code
---
<br>

```py
from sklearn.cluster import KMeans

wcss = []

for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init='k-means++', random_state=42)
    kmeans.fit(X)
    wcss.append(kmeans.inertia_)
```

<center>
<img src="https://user-images.githubusercontent.com/28240052/229454523-ed65c594-64e0-44c1-837b-86d8a9cd42a4.png" width=500>
</center>
<br><br>
As you can see, when K is 5, there is no more significant change in WCSS value.<br>
So, I set K to 5 and implemented it.<br><br>

```py
kmeans = KMeans(n_clusters=5, init='k-means++', random_state=42)
y_kmeans = kmeans.fit_predict(X)
```
<br><br>

## Result
---
<br><br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/229455063-1f68895e-64be-4fa1-877f-1fead2b310dd.png">
</center>