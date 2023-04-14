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






<center>
<img src="" width=400>
</center>
<br><br>