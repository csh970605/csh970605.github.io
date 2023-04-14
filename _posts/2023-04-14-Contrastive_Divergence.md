---
title: Contrastive Divergence
author: SeHoon
date: 2023-04-14 14:23:30 +0900
categories: [Deep Learning, DL_Theory]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is Contrastive Divergence?
Because [RBM](https://csh970605.github.io/posts/RBM/) is undirectional neural network, contrastive divergence is devised to adjust weights.
<br><br>
Here are the input nodes and hidden nodes for example:
<center>
<img src="https://user-images.githubusercontent.com/28240052/231993189-029c41fa-591b-42b1-9b76-09eb98f32dd0.png" width=180 height=60>  
<img src="https://user-images.githubusercontent.com/28240052/231993520-d9324ee7-0fd9-4f59-9301-690b0e41bdd1.png" width=200 height=60>
</center>
<br>
RBM calculate the hidden nodes through initially randomly assigned weights. And the hidden nodes reconstruct the input nodes.
<center>
<img src="https://user-images.githubusercontent.com/28240052/231994156-d5ad1709-c183-4c04-a993-73b18beb48f7.png" width=400>
</center>
<br>
It is important that the weights are the same as the initial state and input nodes are different from the initial state.
<br><br>
Then, why are the input nodes being different? It's because, input nodes are not connected to each other. For example, we are looking at 2nd visible node.
<center>
<img src="https://user-images.githubusercontent.com/28240052/231996605-d5f539af-2b26-46c7-b406-1233e9c07ebc.png" width=700>
</center>
<br>
Because the hidden nodes are not only affected by 2nd visible node but also affected by other visible nodes, the hidden nodes do not perfectly fit the 2nd visible node.<br>
And of course, the visible nodes that are reconstructed by hidden nodes are different even though the weights are the same.
<br><br>
This is why the contrastive divergence exists, and the two visible nodes are different.
<br><br>

RBM performs constrative divergence until the reconstructed visible nodes are the same as before.
This process is called **Gibbs sampling**.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232000048-3907fb89-6ec9-496d-8f23-394a6d98647b.png" width=700>
</center>
<br><br>
<br>

## How to adjust weights in contrastive divergence
---
<br>

First, let's say that the graph represents the randomly initialized weight
<center>
<img src="https://user-images.githubusercontent.com/28240052/232031849-b5140527-ae2d-428f-93d3-ac1e88f1e404.png" width=800>
</center>
<br>

We can know through the formula in the image above that how weights affect to $log$ probability.<br>

In RBM, energy is defined through weights. That is, energy dicate the shape of energy.<br>
<br>
So, let's see what happens during the steps of the contrastive divergence.<br>
<br><br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232037315-71595094-1db5-4cda-9aca-8c2a97c8d5db.png" width=600>
</center>
<br>
First, let's say the green dot represents the first weights which is randomly initialized.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232036986-cc71a9fb-d707-4c3f-9052-83b132a09b33.png" width=600>
</center>
<br>
And also, the red dot represents the reconstructed visual node's weights.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232036896-e1292cfa-ccdc-4b60-bf66-fc8f9577e930.png" width=600>
</center>
<br><br>
Through contrastive divergence, the dot keeps going toward the lowest energy.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232038094-fc090b13-113f-47a0-aa4d-789fde354810.png" width=500>
</center>
<br><br>
At the end of contrastive divergence, the location of dot will be:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232039173-7463d2c1-becb-4400-ab86-7e70e0411e53.png" width=500>
</center>
<br><br>
<br>
But in Hinton's short cut, just two steps are enough to understand how to adjust the curve at an early stage without waiting for the data to converge.<br>
To do this, adjust the weights so that the green dot has the lowest energy like:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232040181-fae076b4-1500-48a6-878c-a474cf26191f.png" width=500>
</center>
<br><br>
And the result will be:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232040317-52945c60-1155-4bd7-8779-01b5c33e95c3.png" width=500>
</center>
<br><br>




<center>
<img src="" width=400>
</center>
<br><br>