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
Denoising autoencoder is a type of [autoencoder](https://csh970605.github.io/posts/Auto_Encoder/) to solve the probelm that has more hidden nodes than input nodes.<br>
Here is a simple structure of denoising autoencdoer.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232384354-b3dab1e2-0d43-4448-9c25-4c9d03d602af.png" width=600>
</center>
<br><br>
X1 ~ X4 is the real input, and copy those values to use as an input of denoising autoencoder.
And select a random number of nodes from the input nodes, 0 them out.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232385271-2af7b05c-9bec-40b4-ab06-8d45d3f1a2dd.png" width=600>
</center>
<br><br>
When you activate the autoencoder with the newly made input values, the output values are paired the real input values.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232386086-32e1c22e-862e-4601-9140-eb2410032452.png" width=600>
</center>
<br><br>
We can prevent the situation where autoencoder simply copies the input through the output.
