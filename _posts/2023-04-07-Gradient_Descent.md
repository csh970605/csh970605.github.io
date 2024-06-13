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

Gradient Descent is a method to minimize the cost $C$. The formula for the cost $C$ is:

<center>

$\frac{1 \times (\hat{y}-y)^{2}}{2}$
</center>

The graph of $C$ is shown below.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230599136-4db3b944-ab3c-4cc0-ad5e-e19102cb7af6.png" width=400>
</center>
<br><br>
Let's assume that the initial value of $C$ is at the red point.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230599103-70f4bf24-68cc-4a20-b977-cb97f45d3808.png" width=400>
</center>
<br><br>
We are going to calculate the gradient of $C$. As you can see, the red point is going downhill. After that, the red point will roll naturally and stop at:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230599968-8a84beb3-c6ef-4fd8-988e-a24116b0bcbb.png" width=400>
</center>
<br><br>
By repeating the process above until $C$ is minimized, you will get well-fitted weights.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230600129-ae25f494-7dfc-4687-94e0-dfb0e1ede561.png" width=400>
</center>

<br><br>

## What is Stochastic Gradient Descent?
Stochastic Gradient Descent compensates for the disadvantage of Gradient Descent, which cannot be implemented when there is no single convex region.<br>

Gradient Descent trains on the entire dataset and then updates the weights, whereas Stochastic Gradient Descent updates the weights each time a row of the dataset is trained, as follows:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230601336-2eac18b2-38c8-4e11-9d1a-148c59037bfa.png">
</center>
