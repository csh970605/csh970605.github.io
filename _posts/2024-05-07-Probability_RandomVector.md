---
title: Probability and Random Vector
author: SeHoon
date: 2024-04-16 10:02:30 +0900
categories: [Papers, DeepLearning]
tags: [Papers, DeepLearning, MultiObjectTracking]
math: true
mermaid: true
---

# Probability
Experiments in which the results are not known in advance are called **random experiments**, although we can all know what are likely to happen. And a set of outcomes from a random experiment is called **event**. And a **sample space** is a set of all possible outcomes in a random experiment.<br>
$P(A)$, which means the probability that event $A$ will occur in sample space $S$, is defined by any number that satisfies the 3 axioms:

+ Axiom 1 : Probability is also bigger or equal than 0($P(A) \geq 0$).
+ Axiom 2 : Probability of sample space is 1($P(S)=1).
+ Axiom 3 : In the case of mutually exclusive events A and B, the relational expression of $P(A \cup B)=P(A)+P(B)$ is established. Where mutually exclusive events mean that $A \cap B = \varnothing$ and $\cup, \cap$ and $\varnothing$ means union, intersectionand empty respectively.<br>

Probability defined by a given case. Therefore, from 3 axioms above, we can know  $P(\varnothing)=0, P(A)=1-P(\bar{A})$ is established. Where $\bar{A}$ means that it is complementary event of $A$.

<br><br><br><br>

# Random Variable

Random variable $X\equiv X(e)$ is defined as a function that corresponds to one real number to each element($e$) constituting a sample space. Random variable is written in upper case and the value that random variable will actually take is written in lower case.

e.g. $X(e)=x$ means that the real number of the random variable corresponding to the random experience is x. In short, it can be written as $X=x$.

The domain of random variable is sample space and the range is $-\infty \leq X \leq \infty$, the whole real number area.

Since an event is a set of $e$ as an element, which is the result of random experiment, there is a corresponding real number interver $I$ for each event $A$. Therefore, if the probability of event A is $P(A)$, the probability that random variable $X$ of belonging to the real number interver is $P(X \in I) = P(A)$.

And also, if random variable($X$) takes a discrete value, it is called a discrete random varaible, if it takes a continous value, it is called a continuous random variable.

<br><br><br><br>

# Probability Distribution Function and Probability Density Function

<br><br>

## Probability Distribution Function

Since $(X \leq x)$ means an event, calculating the probability $P(X \leq x)$ for that event is possible. The probability distribution function of random variable $X$ ($F_{X}(x)$) is defined as $P(X \leq x)$.

The state-space equation is expressed as follows:
<p align="center">
    <span>$\therefore F_{X}(x) = P(X \leq x)$</span>
    <span style="float: right;">[1]</span>
</p>

According to the definition, $F_{X}(-\infty) = 0, F_{X}(\infty) = 1$. Also, if $\Delta x \geq 0$, $F_{X}(x+\Delta x) \geq F_{X}(x)$.

<br><br>

## Probability Density Function

The probability density function of $p_{X}(x)$ defines the following integral expression[2] as a function that satisfies.

<p align="center">
    <span>$int^{x}_{-infty}p_{X}(x)dx = P(X \leq x) = F_{X}(x)$</span>
    <span style="float: right;">[1]</span>
</p>