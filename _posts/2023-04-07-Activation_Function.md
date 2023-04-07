---
title: Activation Function
author: SeHoon
date: 2023-04-07 14:22:30 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---


# What is Activation Function?
Activation function is used in 3rd step in the image below.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230564680-e8828b3e-fba4-4262-ab7e-5cf4ead2d0e9.png" width=600>
</center>
<br>
There are four types of activation function:<br>

+ **Threshold function**<br>
Threshold function returns 0 if the value is less than 0, and returns 1 if the value is more than 0.<br>
It's a type of yes/no function.<br>
To express it in a formula:
<center>
<font size=4>

$\phi(x)\ =\ \begin{cases} 1\ if\ x\geq0\\ 0\ if\ x < 0  \end{cases}$

</font>
</center>
&emsp; &emsp; &nbsp;And the graph will be:<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230561302-b0941deb-a5d0-4424-8fb9-d1d903b1b880.png" width=400>
</center>

+ **Sigmoid function**<br>
Sigmoid function is useful in the final layer(output layer) especially when predict probability<br>
To express it in a formula:
<center>
<font size=4>

$\phi(x)\ =\ \frac{1}{1\ +\ e^{-x}}$

</font>
</center>
&emsp; &emsp; &nbsp;And the graph will be:<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230562601-806d267d-1331-4c32-ab90-5f61f091f074.png" width=400>
</center>

+ **Rectifier function**<br>
Rectifier function is one of the most popular function for ANN.<br>
It returns 0 if the value is less than 0, and returns the value if the value is more than 0.<br>
To express it in a formula:
<center>
<font size=4>

$\phi(x)\ =\ max(x,\ 0)$

</font>
</center>
&emsp; &emsp; &nbsp;And the graph will be:<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230563301-2fb03fc1-8e1d-4377-a728-1007df2c4b07.png" width=400>
</center>

+ **Hyperbolic Tangent(tanh) function**<br>
It's smiliar to sigmoid function, but it goes below 0.<br>
To express it in a formula:
<center>
<font size=4>

$\phi(x)\ =\ \frac{1\ -\ e^{-2x}}{1\ +\ e^{-2x}}$

</font>
</center>
&emsp; &emsp; &nbsp;And the graph will be:<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230563995-11ed5afa-0936-4d5e-9442-b4561bea9df8.png" width=400>
</center>