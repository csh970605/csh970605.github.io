---
title: Hierarchical Clustering
author: SeHoon
date: 2023-04-03 15:19:00 +0900
categories: [Machine Learning, ML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Hierarchical Clustering?

Hierarchical Clustering gives results very similar to [K-means clsutering](https://csh970605.github.io/posts/KMeans_Clustering/). But the whole process is different.<br>
<br>
And there are two type of hierarchical clustering:<br>

+ Agglomerative<br>
Agglomerative is the bottom up approach and deviding into multiple.<br>
There are several steps to doing agglomerative approach.<br>

    + Step 1. <br>
    Make each data point a single-point cluster. That forms N clusters.<br><br>

    <center>
    <img src="https://user-images.githubusercontent.com/28240052/230056661-24655520-6832-457d-b964-2f5e680c0b71.png" width=400>
    </center><br>

    + Step 2.<br>
    Take the two closest data points and make them one cluster. That forms N-1 clusters.<br><br>
    <center>
    <img src="https://user-images.githubusercontent.com/28240052/230056979-c78d9d3d-e4e4-4a8f-ad48-28458b26ca2d.png" width=400>
    </center><br>

    + Step 3.<br>
    Take the two closest clusters and make them one cluster. That forms N-2 Clusters.<br>

    <center>
    <img src="https://user-images.githubusercontent.com/28240052/230057069-4fb165cb-23b5-4b69-a3ea-8c0f8767161d.png" width=400>
    </center><br>

    + Step 4.<br>
    Repeat Step 3 until there is only one clusters.<br>
    <center>
    <img src="https://user-images.githubusercontent.com/28240052/230057375-80862a2d-2085-47d2-ab64-6f9f8da46dc1.png" width=400>
    <br><br>
    <img src="https://user-images.githubusercontent.com/28240052/230057529-225d706b-aa11-4991-ba68-210d03a71c76.png" width=400>
    </center><br>

    + Fin<br>
    <center>
    <img src="https://user-images.githubusercontent.com/28240052/230057916-06228128-4f44-41cf-8d03-41a1e58510b2.png" width=400>
    </center>
    <br><br><br><br>

+ Divisive<br>
Divisive is the up bottom approach and deviding into multiple.

    + Step 1.<br>
    All points in the dataset belong to one single cluster.<br>
    <center>
    <img src="https://user-images.githubusercontent.com/28240052/230057916-06228128-4f44-41cf-8d03-41a1e58510b2.png" width=400>
    </center><br>

    + Step 2.<br>
    Partition the cluster into two least similar cluster based on SSE(Sum of Squared Errors).<br>
    <center>
    <img src="https://user-images.githubusercontent.com/28240052/230057529-225d706b-aa11-4991-ba68-210d03a71c76.png" width=400>
    </center><br>

    + Step 3.<br>
    Repaet Step 2 until the desired number of clusters are obtained
    <br><br>
    + Fin<br>
    Because, the number we wanted to obatin is 3, Divisive is done.<br>
    <center>
    <img src="https://user-images.githubusercontent.com/28240052/230057375-80862a2d-2085-47d2-ab64-6f9f8da46dc1.png" width=400>
    </center>
    <br>



<br>
<br>

## How to calculate the distance between clusters?
---
<br>
There are 4 ways to calculate distance.<br><br>

+ Option 1: <br>
The distance between closest points in the clusters.<br>
+ Option 2: <br>
The distance between furthest points in the clusters.<br>
+ Option 3: <br>
Average of all the distances between all points in the clusters.<br>
+ Option 4: <br>
The distance between centroids.<br><br>


These ways can significantly affect the output.<br>
<br>

## The purpose of agglomerative or divisive?
---
<br>
The purpose of hierarchical clustering, the way the hierarchical clustering works, is to maintain a memory of how we went through those porcesses.<br>
And that memory is stored in a dendrogram. 

<br><br>

# What is Dendrogram?<br>

We created clusters above and the dendrogram will help us get the desired result from those clusters.<br>

Let's assume that we have 6 data points and apply agglomerative hierachical clustering.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230084437-cb8fbcdc-782f-4979-aae5-de318270f2fe.png" width=400>
</center>
<br><br>
As we see above, find two closest points and put them into one cluster.
<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230087437-4b1840f3-127e-40a1-98f4-a72373d695c3.png" width=400>
</center>
<br><br>
Then, Dendrogram will record the distance between two points.<br>
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/230088557-2e4f376c-b617-412a-96b5-544774d44a08.png" width=400>
</center>
<br><br>

After that, follow the steps of agglomerative. I'll show you the progress by image.<br>
<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230088495-f73ea4e7-d1f5-473e-8e65-08329bb8aa4f.png">
<br><br>
<img src="https://user-images.githubusercontent.com/28240052/230088885-f57b1ac7-9a2f-47f5-bedf-19aca4ad563f.png" >
<br><br>
<img src="https://user-images.githubusercontent.com/28240052/230089075-ec45d340-ab42-4e18-9fc6-435b64b9f111.png" >
<br><br>
<img src="https://user-images.githubusercontent.com/28240052/230089181-e687898d-2b37-4bfb-ab8f-9c194f49ff44.png" >
<br><br>
</center>
<br>

# How to choose clusters?

When a straight line parallel to the X-axis is drawn on the dendrogram obtained through the above process, the point where the graph intersects is the number of clusters.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230090171-91e227bb-3070-4e7e-9179-50050ea11a2d.png" width=400>
</center>
<br><br>

**The optimal number of clusters is the place where the most flat straight lines can be drawn on the X-axis without changing the number of clusters.** <br>
In other words, in our results, it is appropriate when the number of clusters is 2.<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/230090894-1d79e71e-a03c-408d-9e4e-24522c558018.png" width=400>
</center>
<br><br>


# Example
<br><br>

## Code
---
<br>

```py
import scipy.cluster.hierarchy as sch
dendrogram = sch.dendrogram(sch.linkage(X, method='ward'))
```
<br>

As you can see in the [result](https://csh970605.github.io/posts/Hierarchical_Clustering/#result) below.
<br>
<br>

```py
from sklearn.cluster import AgglomerativeClustering
hc = AgglomerativeClustering(n_clusters=5, affinity='euclidean', linkage='ward')
y_hc = hc.fit_predict(X)
```

<br><br>

## Result
---
<br>

<center>
Dendrogram
<br>
<img src="https://user-images.githubusercontent.com/28240052/230091599-22407bfb-8414-43f0-988f-fe896ac5d347.png">
<br><br>

Clustering<br>
<img src="https://user-images.githubusercontent.com/28240052/230091936-abdc0e40-4cc8-4e8a-914f-8a888ecb1c42.png">
</center>