---
title: Reinforcement Learning
author: SeHoon
date: 2023-04-06 14:40:00 +0900
categories: [Machine Learning, ML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Reinforcement Learning?
Reinforcement Learning is a powerful branch of Machine Learning. It is used to solve interacting problems where the data observed up to time $t$ is considered to decide which action to take at time $(t+1)$. It is also used for Artificial Intelligence when training machines to perform tasks such as walking. Desired outcomes provide the AI with rewards, while undesired outcomes provide punishments. Machines learn through trial and error.<br>

<br><br><br>

# Algorithms


+ [Upper Confidence Bound(UCB)](https://csh970605.github.io/posts/UCB/)<br>
+ [Thompson Sampling](https://csh970605.github.io/posts/Thompson_Sampling/)<br>

<br><br>

# UCB VS Thompson Sampling

<center>

|UCB|Thompson Sampling|
|---|---|
|Deterministic algorithm.<br>Easy to modify.<br>Requires update at every round. | Probabilistic algorithm. = Result can be changed.<br>Can accommodate delayed feedback.<br>Better empirical evidence. |
</center>

<br><br>

You can see my implementation on my [Github](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%206%20-%20Reinforcement%20Learning)