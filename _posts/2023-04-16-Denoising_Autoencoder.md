---
title: Denoising Autoencoder
author: SeHoon
date: 2023-04-16 17:01:00 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is Denoising Autoencoder?
A Denoising Autoencoder is a type of [autoencoder](https://csh970605.github.io/posts/Auto_Encoder/) designed to solve the problem of having more hidden nodes than input nodes.<br>
Here is a simple structure of a Denoising Autoencoder.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232384354-b3dab1e2-0d43-4448-9c25-4c9d03d602af.png" width=600>
</center>
<br><br>
X1 to X4 are the real inputs. Copy those values to use as the input of the Denoising Autoencoder. Then, select a random number of nodes from the input nodes and set them to 0.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232385271-2af7b05c-9bec-40b4-ab06-8d45d3f1a2dd.png" width=600>
</center>
<br><br>
When you activate the autoencoder with the newly created input values, the output values are paired with the real input values.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232386086-32e1c22e-862e-4601-9140-eb2410032452.png" width=600>
</center>
<br><br>
This prevents the autoencoder from simply copying the input to the output.
