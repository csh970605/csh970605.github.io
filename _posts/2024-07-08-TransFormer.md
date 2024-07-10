---
title: Transformer
author: SeHoon
date: 2024-07-08 10:00:30 +0900
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

An attention function is described as mapping a query and a set of key-value pairs to an output, where a query, keys, values, and an output are all vectors. The output is computed as a weighted sum of the values, where the weight assigned to each value is computed by a compatibility function of the query with the corresponding key. Two main features of attention are:

+ Scaled Dot-Product Attention
    

+ Multi-Head Attention

<br><br>

### Scaled Dot-Product Attention

The input consists of queries and keys of dimension $d_{k}$, and values of dimension $d_{v}$. Transformer computes the dot products of the query with all keys, divides each by $\sqrt{d_{k}}$, and applies a softmax function to obtain the weights on the values.<br>

In practice, transformer computes the attention function on a set of queries simultaneously, packed together into a matrix $Q$. The keys and values are also packed together into matrices $K$ and $V$. Then, transformer computes the matrix of outputs as:

<center>

$\text{Attention}(Q, K, V) = \text{softmax}\frac{QK^{T}}{\sqrt{d_{k}}}V$
</center>

The structure of the scaled dot-product attention is:

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/86d24315-984d-44a1-9700-e544ef1ff9e4">
</center>

<br><br>

### Multi-Head Attention

The transformer found it beneficial to linearly project the queries, keys, and values $h$ times with different, learned linear projections to $d_{k}, d_{k}, \text{and } d_{v}$ dimensions, respectively. On each of these projected versions of queries, keys and values then perform the attention function in parallel, yielding $d_{v}$-dimensional output values. These are concatenated and once again projected, resulting in the final values, as :

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/6a64eda0-a82b-493b-b117-29afdc493989">
</center>

Multi-head attention allows the model to jointly attend to information from different representation subspaces at different positions. The pseudocode of the multi-head attention is:

<center>

$\text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_{1}, \text{head}_{2}, \text{head}_{h}) W^{O}$<br>

where $\text{head}_{i} = \text{Attention}(QW_{i}^{Q}, KW_{i}^{K}, VW_{i}^{V})$
</center>

where

+ $W_{i}^{Q} \in \mathbb{R}^{d_{model}\times d_{k}}$

+ $W_{i}^{K} \in \mathbb{R}^{d_{model}\times d_{k}}$

+ $W_{i}^{V} \in \mathbb{R}^{d_{model}\times d_{v}}$

+ $W^{O} \in \mathbb{R}^{d_{model}\times hd_{v}}$

<br><br>

## Position-wise Feed-Forward Networks (FFN)

Each sub-layer in the transformer encoder and decoder contains a fully connected feed-forward network, which consists of two linear layers with a [ReLU](https://csh970605.github.io/posts/Activation_Function/#rectifier-function) activation in between. The equation of the FFN is:

<center>

$\text{FFN}(x) = \max(0, xW_{1} + b_{1})W_{2} + b_{2}$
</center>
<br><br>

## Embeddings and Softmax

Transformer uses learned embeddings to convert the input tokens and output tokens to vectors of dimension $d_{model}$. For example, in an encoder, assume that the input vector is "The cat sat on the mat", and all words are converted as:

+ "The" $\rightarrow$ [0.1, 0.2, 0.3, 0.4]

+ "cat" $\rightarrow$ [0.5, 0.6, 0.7, 0.8]

+ "sat" $\rightarrow$ [0.9, 1.0, 1.1, 1.2]

+ "on" $\rightarrow$ [1.3, 1.4, 1.5, 1.6]

+ "the" $\rightarrow$ [1.7, 1.8, 1.9, 2.0]

+ "mat" $\rightarrow$ [2.1, 2.2, 2.3, 2.4]
<br>

In the same way, in a decoder, assume that the output vector is "\<start> Hell", and all words including the \<start> token are converted as:

+ "\<start>" $\rightarrow$ [0.1, 0.2, 0.3, 0.4]

+ "H" $\rightarrow$ [0.5, 0.6, 0.7, 0.8]

+ "e" $\rightarrow$ [0.9, 1.0, 1.1, 1.2]

+ "l" $\rightarrow$ [1.3, 1.4, 1.5, 1.6]

+ "l" $\rightarrow$ [1.3, 1.4, 1.5, 1.6]

Through the output vector, to predict next-token probabilities, the transformer uses learned two linear layers and softmax function. The two linear layers have same the same weights, which are multiplied by $\sqrt{d_{model}}$.

<br><br>

## Positional Encoding

Since the transformer doesn't contain recurrence and convolution, it is hard to make use of the order of the sequence. The transformer must inject some information about the relative or absolute position of the tokens in the sequence. The positional encodings are derived to inject some information about the relative or absolute position of the tokens at the bottoms of the encoder and decoder stacks. The positional encodings have the same dimension $d_{model}$ as the embeddings, so that the two can be summed.

In the transformer, sine and cosine functions of different frequencies are used as:

<center>

$PE_{(pos, 2i)} = \sin(pos/10000^{\frac{2i}{d_{model}}})$<br>

$PE_{(pos, 2i+1)} = \cos(pos/10000^{\frac{2i}{d_{model}}})$
</center>

where

+ $pos$ : The position.

+ $i$ : The dimension.
<br><br>

## Model Architecture

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/9ec25be1-063d-4d81-a087-3c37ea0c5a08">
</center>

<br><br><br><br>


# Conclusion

In traditional NLP, RNN or [LSTM](https://csh970605.github.io/posts/LSTM/) models are used to predict the outputs. However, these models are often heavy and weak at generating perfect outputs. Transformer, which is introudced in this paper, makes NLP more efficient and powerful, enabling the creation of advanced language models such as [BERT](https://arxiv.org/abs/1810.04805) and [GPT](https://arxiv.org/abs/2005.14165).