---
title: Activation Functions
author: SeHoon
date: 2023-04-07 14:22:30 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---


# What are Activation Functions?

Activation functions are used in 3rd step in the image below.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230564680-e8828b3e-fba4-4262-ab7e-5cf4ead2d0e9.png" width=600>
</center>
<br><br><br><br>

# Types of Activation Functions

There are 5 types of activation functions:<br><br><br>

## Threshold function

The threshold function returns 0 if the value is less than 0, and returns 1 if the value is greater than 0. It's a type of yes/no function. To express it in a formula:
<br>

<center>

$\phi(x)\ =\ \begin{cases} 1\ if\ x\geq0\\ 0\ if\ x < 0  \end{cases}$

</center>

And the graph will be:<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/230561302-b0941deb-a5d0-4424-8fb9-d1d903b1b880.png" width=400>
</center><br><br>

## Sigmoid function

The sigmoid function is useful in the final layer (output layer), especially when predicting probabilities. To express it in a formula:
<br>

<center>

$\phi(x)\ =\ \frac{1}{1\ +\ e^{-x}}$

</center>

And the graph will be:<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/230562601-806d267d-1331-4c32-ab90-5f61f091f074.png" width=400>
</center><br><br>

## Rectifier function (ReLU)

The rectifier function is one of the most popular functions for ANN. It returns 0 if the value is less than 0, and returns the value if the value is more than 0. To express it in a formula:
<br>

<center>

$\phi(x)\ =\ max(x,\ 0)$

</center>

And the graph will be:<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/230563301-2fb03fc1-8e1d-4377-a728-1007df2c4b07.png" width=400>
</center><br><br>

## Hyperbolic Tangent(tanh) function

It is similar to the sigmoid function, but it goes below 0. To express it in a formula:
<br>

<center>

$\phi(x)\ =\ \frac{1\ -\ e^{-2x}}{1\ +\ e^{-2x}}$

</center>

And the graph will be:<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/230563995-11ed5afa-0936-4d5e-9442-b4561bea9df8.png" width=400>
</center><br><br>

## Mish Activation

Mish avoids saturation due to capping because the graph tends towards positive infinity. Also, it can decrease overfitting, and strong regularization may appear because it is bounded below.<br>

<center>

$\phi(x)\ =\ xtanh(softplus(x))\ =\ xtanh(ln(1+e^{x}))$
</center>
<br><br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/de351852-b52f-437e-b1dd-fdd52d2e1379" width=400>
</center><br><br>

## SiLU Activation

The SiLU activation function avoids saturation due to capping because the graph tends towards positive infinity. It can also decrease overfitting, and strong regularization may appear because it is bounded below.<br>
<center>

$\phi(x)\ =\ x \times \theta(x)$ where $\theta(x)$ is the logistic sigmoid.
<br><br>

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/774ab84d-1f45-49da-8d95-82441f4fa4da" width=400>
</center><br><br>