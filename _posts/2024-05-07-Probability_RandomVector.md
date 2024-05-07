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
$P\{A\}$, which means the probability that event $A$ will occur in sample space $S$, is defined by any number that satisfies the 3 axioms:

+ Axiom 1 : Probability is also bigger or equal than 0($P\{A\} \geq 0$).
+ Axiom 2 : Probability of sample space is 1($P\{S\}=1).
+ Axiom 3 : In the case of mutually exclusive events A and B, the relational expression of $P\{A \cup B\}=P\{A\}+P\{B\}$ is established. Where mutually exclusive events mean that $A \cap B = \varnothing$ and $\cup, \cap$ and $\varnothing$ means union, intersectionand empty respectively.<br>

Probability defined by a given case. Therefore, from 3 axioms above, we can know  $P\{\varnothing\}=0, P\{A\}=1-P\{ \bar{A} \}$ is established. Where $\bar{A}$ means that it is complementary event of $A$.