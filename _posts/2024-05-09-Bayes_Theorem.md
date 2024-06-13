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

$n$ numbers of events $B_{i}, i=1, 2, \ldots , n$ are exclusive each other like image below, $P(B_{i}, B_{j})=0, \forall \  i \neq j$. 

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/25299ac0-9669-48c4-84d2-ff6cb8c8cd98">
</center>

And considering the entire sample space, $\Sigma_{i=1}^{n}P(B_{i})=1$. Then, the probability of a random event $A$ is expressed as formula [1]:

<center>

$P(A) = \Sigma_{i=1}^{n}P(A, B_{i})$<br>


<p align="center">
    <span>$=\Sigma_{i=1}^{n}P(A|B_{i})P(B_{i})$</span>
    <span style="float: right;">[1]</span>
</p>

</center>

Formula [1] is called a **total probability theorem**.<br>

In order to induce the bayes' theorem, we sholud know about the conditional probability. The conditional probability is:

<center>

$P(B_{i} \mid A) = \frac{P(A,B_{i})}{P(A)}$

<p align="center">
    <span>$=\frac{P(A \mid B_{i})P(B_{i})}{P(A)}$</span>
    <span style="float: right;">[2]</span>
</p>

</center>

If you substitute the total probability theorem into formula [2]:

<p align="center">
    <span>$=\frac{P(A \mid B_{i})P(B_{i})}{\Sigma_{i=1}^{n}P(A|B_{i})P(B_{i})}$</span>
    <span style="float: right;">[3]</span>
</p>

Formula [3] is called the **Bayes' theorem**.<br>

Of course, it can be expressed as [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) as formula [4].

<center>

$p_{X \mid Y}(x \mid y) = p_{Y \mid X}(y \mid x)p_{X}(x)$

<p align="center">
    <span>$=\frac{p_{Y \mid X}(y \mid x)p_{X}(x)}{\int_{-\infty}^{\infty}p_{Y \mid X}(y \mid x)p_{X}(x)dx}$</span>
    <span style="float: right;">[4]</span>
</p>

$= \frac{p_{XY}(x,y)}{p_{Y}(y)}$

</center>

where $p_{X}(x)$ is a prior probability density function, $p_{X \mid Y}(x \mid y)$ is a posterior probability density function.

Of course again, the occasion that events and random variables are mixed, the bayes' theorem is formula [5].

<p align="center">
    <span>$P(B_{i} \mid y) = \frac{p_{Y \mid B_{i}}(y \mid B_{i})P(B_{i})}{\Sigma_{j=1}^{n}p_{Y \mid B_{j}}(y \mid B_{j})P(B_{j})}$</span>
    <span style="float: right;">[5]</span>
</p>