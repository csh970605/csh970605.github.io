---
title: Transformer
author: SeHoon
date: 2024-06-26 10:00:30 +0900
categories: [Papers, DeepLearning]
tags: [Papers, DeepLearning, NLP]
math: true
mermaid: true
---

# [Attention Is All You Need](https://arxiv.org/abs/1706.03762)

[Recurrent neural networks](https://csh970605.github.io/posts/RNN/) typically factor computation along the symbol positions of the input and output sequences. Aligning the positions to steps in computation time, they generate a sequence of hidden state $h_{t}$, as a function of the previous hidden state $h_{t-1}$ and the input for position $t$.<br>

Attention mechanisms have become an integral part of compelling sequence modeling and transduction models in various tasks, allowing modeling of dependencies without reagrd to their distance in the input or output sequences. However, typical attention mechanisms are used in conjunction with a RNN.<br>

o use an attention mechanism itself, this paper proposes the Transformer, a model architecture eschewing recurrence and instead relying entirely on an attention mechanism to draw global dependencies between input and output.
<br><br><br><br>

# Methology