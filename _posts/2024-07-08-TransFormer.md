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

[Recurrent neural networks (RNN)](https://csh970605.github.io/posts/RNN/) typically factor computation along the symbol positions of the input and output sequences. Aligning the positions to steps in computation time, they generate a sequence of hidden state $h_{t}$, as a function of the previous hidden state $h_{t-1}$ and the input for position $t$.<br>

Attention mechanisms have become an integral part of compelling sequence modeling and transduction models in various tasks, allowing modeling of dependencies without reagrd to their distance in the input or output sequences. However, typical attention mechanisms are used in conjunction with a RNN.<br>

To use an attention mechanism itself, this paper proposes the Transformer, a model architecture eschewing recurrence and instead relying entirely on an attention mechanism to draw global dependencies between input and output.
<br><br><br><br>

# Methology

In this paper, they introduce 6 main methods which are:

+ Encoder and Decoder Stacks

+ Attention

+ Position-wise Feed-Forward Networks

+ Embeddings and Softmax

+ Positional Encoding

+ Model Architecture

<br><br>

## Encoder and Decoder Stacks

+ Encoder : The encoder is composed of a stack of $N = 6$ identical layers. Each layer has two sub-layers. The first is a multi-head self-attention mechanism, and the second is a simple, position-wise fully connected feed-forward network. Transformer employs a residual connection around each of the two sub-layers as:
    <center>

    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/038254f9-4b76-4111-82a0-eeec77eff02b">
    </center>

    That is, the output of each sub-layer is LayerNorm $(x + \text{Sublayer}(x))$, where $Sublayer(x)$ is the function implemented by the sub-layer itself. The dimensions of the output, $Q$, $K$, $V$, are all the same as an input's dimension.

+ Decoder : The decoder is also composed of a stack of $N=6$ identical layers, just like the encoder.". In addition to the two sub-layers in each encoder layer, the decoder inserts a third sub-layer, which performs multi-head attention over the output of the encoder stack. Note that the output of the encoder stack is a constant value. Additionally, as encoder does, decoder employs residual connections around each of the sub-layers as :
    <center>
    
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/ef9ae8cc-7877-4002-b70c-3b4db25904f8">
    </center>

    Transformer also modifies the self-attention sub-layer in the decoder stack to prevent positions from attending to subsequent positions. This masking, combined with the fact that the output embeddings are offset by one position, ensures that the predictions for position $i$ can depend only on the known outputs at positions less than $i$.

<br><br>

## Attention

<br><Br>

## Position-wise Feed-Forward Networks

<br><Br>

## Embeddings and Softmax

<br><Br>

## Positional Encoding

<br><Br>

## Model Architecture

<br><Br>