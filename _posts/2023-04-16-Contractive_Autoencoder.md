---
title: Contractive Autoencoder
author: SeHoon
date: 2023-04-16 17:02:00 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is Contractive Autoencoder?
Contractive autoencoder is a type of [autoencoder](https://csh970605.github.io/posts/Auto_Encoder/) to solve the probelm that has more hidden nodes than input nodes.<br><br>
Contractive Autoencoder uses the entire training process to produce the output, compare it to the input, and gives a penalty when doing backpropagation using the log function.

<center>
<img src="https://user-images.githubusercontent.com/28240052/232393024-d67994ec-9407-4dd4-b46a-aa00d9811ac7.png" width=500 height=360>
</center>