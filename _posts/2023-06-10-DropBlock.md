---
title: DropBlock
author: SeHoon
date: 2023-06-10 17:32:00 +0900
categories: [Vision Machine Learning, VML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is DropBlock?
It is a way to perform [Regularization](https://csh970605.github.io/posts/Dropout/).
And it is almost same as [dropout](https://csh970605.github.io/posts/Dropout/). However, there is some difference that dropblock drops random "blocks" of feature to cover the disadvantage of dropout like:
<br>

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/9d3f1af7-caaa-4405-891e-64462563ba35" width=400>
</center>

<br><br>

# Usage

<br>

## PyTorch
---
<br>

**torchvision.ops.drop_block2d(input, p, block_size, inplcae=Fales, eps=1--06, training=True)->Tensor** where:

+ input : The input tensor or 4-dimensions with the first one being its batch.

+ p : Probability of an element to be dropped.

+ block_size : Size of the block to drop.

+ inplcae : If set to True, will do this operation in-place.

+ eps :  A value added to the denominator for numerical stability.

+ training : apply dropblock if is True.

+ Tensor : The randomly zeroed tensor after dropblock.

