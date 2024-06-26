---
title: Reinforcement Learning
author: SeHoon
date: 2023-04-23 14:22:30 +0900
categories: [Deep Reinforcement Learning, DRL_Introduction]
tags: [deep reinforcement learning, python]
math: true
mermaid: true
---

# What is Reinforcement Learning?

In reinforcement learning, an agent takes action in the environment, the environment changes the state, and the agent gets rewards, like:
<center>
<img src="https://user-images.githubusercontent.com/28240052/233826821-39ff2306-4a63-4a72-aba5-f109ea0d0203.png" width=500>
</center>
<br><br>
This process is repeated over and over again to understand what actions lead to positive rewards and favorable states and what actions lead to negative rewards and unfavorable states.<br>

Apply the [Bellman Equation](https://csh970605.github.io/posts/Bellman_Equation/) to the states collected through actions to calculate the probability of each action being taken and then take the action. Additionally, [Living Penalty](https://csh970605.github.io/posts/Living_Penalty/) is applied to avoid infinite loops.
<br><br><br>

# Algorithm of Deep Reinforcement Learning

+ [Twin Delayed Deep Deterministic Policy Gradient(TD3)](https://csh970605.github.io/posts/TD3/)

<br><br><br><br>

## Implementations
---
<br>

+ [Stock Prediction with TD3](https://github.com/csh970605/Complete-Guide-on-TensorFlow-2.0/tree/main/Section%208)

+ [Auto walking](https://github.com/csh970605/Deep-Reinforcement-Learning-2.0)

+ [Self driving car](https://github.com/csh970605/Self_Driving_Car)