---
title: Gradient Descent
author: SeHoon
date: 2023-04-07 14:21:30 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---


# What is Gradient Descent?

Gradient Descent is the way to minimize cost *C*.<br>
And the formula of cost *C* is:
<center>
<font size=4>

$\frac{1*(\hat{y}-y)^{2}}{2}$
</font>
</center>

You can see the graph of *C* below.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230599136-4db3b944-ab3c-4cc0-ad5e-e19102cb7af6.png" width=400>
</center>
<br><br>
And let's assume that the first *C* value is the red point.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230599103-70f4bf24-68cc-4a20-b977-cb97f45d3808.png" width=400>
</center>
<br><br>
We are going to get the gradient of *C* value. As you can see the red point is going downhill.<br>
After that, the redpoint will roll naturally and stop at:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230599968-8a84beb3-c6ef-4fd8-988e-a24116b0bcbb.png" width=400>
</center>
<br><br>
After repeat the process above until *C* is minimized like:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230600129-ae25f494-7dfc-4687-94e0-dfb0e1ede561.png" width=400>
</center>
You will get well fitted weights.

<br><br>

## What is Stochastic Gradient Descent?
Stochastic Gradient Descent is to compensate for the disadvantage of Gradient Descent that cannot be implemented when there is not one convex place.<br>

Gradient Descent trains one dataset and then updates the weights, whereas Stochastic Gradient Descent updates the weights each time a row of the dataset is trained like:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230601336-2eac18b2-38c8-4e11-9d1a-148c59037bfa.png">
</center>
