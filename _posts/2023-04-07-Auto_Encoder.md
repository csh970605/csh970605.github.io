---
title: Auto Encoder
author: SeHoon
date: 2023-04-07 14:24:30 +0900
categories: [Deep Learning, DL_Introduction]
tags: [deep learning, python]
math: true
mermaid: true
---


# What is Auto Encoder?
Auto encoder is an unsupervised deep learning that is used for:
+ Feature detections.<br>
When auto encoder encodes datas, the hidden layer represents important features. And we can use the features.
+ Recommendation system.<br>
+ Encoding.<br>

Auto encoder encodes itself. So, auto encoder takes some inputs, put it to the hidden layer, and then gets the outputs with the same number as the inputs.<br>

Here is a simple structure of auto encoder:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232176425-4140165a-ac3e-4d9c-8357-795a847c33a0.png" width=400>
</center>
<br>

Auto encoder is directed types of neural network unlike [boltzmann machine](https://csh970605.github.io/posts/Boltzmann_Machine/).<br>
<br>

# How does Auto Encoder works?
Here is a simplified auto encoder:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232210406-0781ef41-ce2a-4cd7-9cbb-edf5f99ea38f.png" width=600>
</center>
<br><br>

We are going to encode the ratings of movies that people have rated. "1" means they liked the movie and "0" means they didn't like the movie.<br>
And then, as an example, set the weights like:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232227829-684dd24f-1111-4a5a-a078-ebc5d4588ff9.png" width=600>
</center>
<br><br>
Though we set the weights like in the image above as an example, in auto encoder, hyperbolic tangent usually used to set weights.<br>
<br><br>
And we get input "[1 0 0 0]".
<center>
<img src="https://user-images.githubusercontent.com/28240052/232228496-1b3ad1b5-232e-4965-9781-207dade786b0.png" width=600>
</center>
<br><br>
Computing the input with the weights gives the output "[2 0 0 -2]".
<center>
<img src="https://user-images.githubusercontent.com/28240052/232228547-8720f456-0d2d-470a-a837-6717dcb71455.png" width=600>
</center>
<br><br>

But, this is not the end. By using [softmax function](), the output is "[1 0 0 0]"

<center>
<img src="https://user-images.githubusercontent.com/28240052/232228892-b8512a68-c66b-418f-b5ad-9ceca9cf8766.png" width=400>
</center>
<br><br>

In this case, the input is the same as the output.




# Training steps of an Auto Encoder
# Overcomplete Hidden Layers
# Types of Auto Encoders




<center>
<img src="" width=400>
</center>
<br><br>