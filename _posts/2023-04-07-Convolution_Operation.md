---
title: Convolution Operation
author: SeHoon
date: 2023-04-07 14:30:30 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is Convolution Operation?
The formula of convolution is:
<center>

$(f \times g)(t)\ =\ \int_{-\infty}^{\infty}f(\tau)g(t\ -\ \tau)d\tau$
</center>
Convolution is the simple application of a filter, called a feature detector, to an input that results in an activation.<br>
Let's assume we have input image data:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230700853-f24a2e80-0458-46a7-92b8-83bc365a2eac.png" width=300>
</center>
<br>
And a feature detector:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230700886-22bf49f8-ee0c-41d3-9398-993159980a31.png" width=300>
</center>

We will create a feature map by multiplying the matrix extracted from the input image by the feature detector as follows:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230701710-6c057f37-5d14-4104-9b60-925bc316e893.png">
</center>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230701742-88d95a62-f62e-4d94-8a03-a2bf63107e7d.png">
</center><br><br>

Continuing this, we get the feature map:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230701780-163df4fb-a917-47a4-80b0-a7cadb5552fe.png" width=300>
</center><br><br>

And the shape of the return will be (N, $C_{out}$, $H_{out}$, $W_{out}$), where:<br>

<center>

$H_{out} = floor(\frac{H_{in}\ +\ 2\  \times \ \text{padding[0]}\ -\ \text{dilation[0]}\  \times \ (\text{kernelsize[0]}\ -\ 1)\ -\ 1}{\text{stride[0]}})\ + 1$
<br><br>

$W_{out} = floor(\frac{W_{in}\ +\ 2\  \times \ \text{padding[1]}\ -\ \text{dilation[1]}\  \times \ (\text{kernelsize[1]}\ -\ 1)\ -\ 1}{\text{stride[1]}})\ + 1$
</center>

```py
def cnn_calculator(w_in, h_in, kernel_size, padding=(0,0), stride=(1,1), dilation=(1,1)):
  w_out = math.floor((w_in + 2*padding[0] - dilation[0]*(kernel_size[0] - 1) - 1) / stride[0]) + 1
  h_out = math.floor((h_in + 2*padding[1] - dilation[1]*(kernel_size[1] - 1) - 1) / stride[1]) + 1
  return w_out, h_out
```
<br><br><br><br>

## Why we use feature detector?
---
<br>

+ By multiplying the input image and the feature detector, we can reduce the size of the image.
+ To detect some features in certain parts of the integrated image. For example, if the feature detector has pattern on it, the highest value in feature map is when that pattern is matched up.

## Is there only one feature map in the convolutional layer?
No, unlike the example, there are many feature maps in a convolutional layer.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230702130-be709476-279d-447e-9325-230925d34d73.png" width=600>
</center>
<br>
Because an image has lots of features, there is no way to represent an image with a single feature map. Each feature map represent one of the features in the image. For example, there are some images of Taj Mahal that have been feature extracted.<br>
Blur version:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230702357-346a54d3-90ae-46f5-b49d-99d7a73670b6.png" width=200>
</center>
<br>
Edge detected version:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230702387-2d072fd2-770c-43f4-bb76-cdf7aac18490.png" width=200>
</center>
<br><br><br>

Then, why do we have lots of versions? Because computer can choose the optimal version to carry out the command.
<br><br><br>

# ReLU layer?
In ReLU layer, apply rectifier function($\phi(x)\ =\ max(x,\ 0)$) to break linearity of convolutional layer.The reason why we want to break linearity is that images are non-linear. However, if you create a feature map by applying a convolution operation and activating the feature detector, there is a risk of creating linearity. That's why ReLu layer is applied.