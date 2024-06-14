---
title: Sparse Autoencoder
author: SeHoon
date: 2023-04-16 17:00:00 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is Sparse Autoencoder?
A Sparse Autoencoder is a type of [autoencoder](https://csh970605.github.io/posts/Auto_Encoder/) used to extract more features (i.e., to have more hidden nodes) than input nodes. It is also effective in preventing overfitting. Here is a simple structure of a Sparse Autoencoder.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232287646-c05fdd2d-4f5b-422b-8c9a-4367106aaf16.png" width=400>
</center>
<br><br>
To prevent overcomplete hidden layers, a Sparse Autoencoder limits or penalizes the loss function to avoid using all hidden nodes at once. That is, the autoencoder can use only a limited number of hidden nodes at once.<br>
In the image above, the autoencoder can use only 2 nodes (white hidden nodes) at a time. The gray hidden nodes give very small values that they don't affect the result.<br>
However, not only the above 2 nodes are used in each step. For example, in the second step, another 3 nodes can be used.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232287879-c9a4f104-be32-4e95-9243-72f2bf7970d1.png" width=400>
</center>
<br><br>
In the third step, another 3 nodes can be used.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232287923-8cb19e05-2ca1-4ae5-a3d4-928b89d06a26.png" width=400>
</center>
<br><br>

That is, **sparse autoencoder uses a different node each time.**

