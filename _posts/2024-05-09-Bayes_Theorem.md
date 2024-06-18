---
title: Bayes' Theorem
author: SeHoon
date: 2024-05-09 10:02:30 +0900
categories: [Mathematics, Statistics]
tags: [Mathematics, Statistics, Kalman Filter]
math: true
mermaid: true
---

# Bayes' Theorem

n events $B_{i}, i=1, 2, \ldots , n$, are mutually exclusive, as shown in the image below. Therefore, $P(B_{i}, B_{j})=0 \ \forall \ i \neq j$.

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/25299ac0-9669-48c4-84d2-ff6cb8c8cd98">
</center>

Considering the entire sample space, we have $\sum_{i=1}^{n}P(B_{i})=1$. Then, the probability of a random event $A$ is expressed as shown in equation [1]:

<center>

$P(A) = \sum_{i=1}^{n}P(A, B_{i})$<br>


<p align="center">
    <span>$=\sum_{i=1}^{n}P(A|B_{i})P(B_{i})$</span>
    <span style="float: right;">[1]</span>
</p>

</center>

Equation [1] is called the **total probability theorem**.<br>

In order to derive Bayes' theorem, we should understand conditional probability. The conditional probability is:

<center>

$P(B_{i} \mid A) = \frac{P(A,B_{i})}{P(A)}$

<p align="center">
    <span>$=\frac{P(A \mid B_{i})P(B_{i})}{P(A)}$</span>
    <span style="float: right;">[2]</span>
</p>

</center>

If we substitute the law of total probability into equation [2], we get:

<p align="center">
<span>$\frac{P(A \mid B_{i})P(B_{i})}{\sum_{i=1}^{n}P(A \mid B_{i})P(B_{i})}$</span>
<span style="float: right;">[3]</span>
</p>

Equation [3] is called the **Bayes' theorem**.<br>

It can also be expressed using the [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) as shown in equation [4].

<center>

$p_{X \mid Y}(x \mid y) = p_{Y \mid X}(y \mid x)p_{X}(x)$

<p align="center">
    <span>$=\frac{p_{Y \mid X}(y \mid x)p_{X}(x)}{\int_{-\infty}^{\infty}p_{Y \mid X}(y \mid x)p_{X}(x)dx}$</span>
    <span style="float: right;">[4]</span>
</p>

$= \frac{p_{XY}(x,y)}{p_{Y}(y)}$

</center>

where $p_{X}(x)$ is a prior probability density function, $p_{X \mid Y}(x \mid y)$ is a posterior probability density function.

When events and random variables are mixed, Bayes' theorem is given by equation [5].

<p align="center">
    <span>$P(B_{i} \mid y) = \frac{p_{Y \mid B_{i}}(y \mid B_{i})P(B_{i})}{\sum_{j=1}^{n}p_{Y \mid B_{j}}(y \mid B_{j})P(B_{j})}$</span>
    <span style="float: right;">[5]</span>
</p>