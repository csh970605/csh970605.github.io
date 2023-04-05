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
    <br><br>

+ Divisive<br>
Divisive is the up bottom approach and deviding into multiple.

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