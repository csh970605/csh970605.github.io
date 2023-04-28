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

In reinforcement learning, agent takes action to the environment and environment change the state and agent gets rewards like:
<center>
<img src="https://user-images.githubusercontent.com/28240052/233826821-39ff2306-4a63-4a72-aba5-f109ea0d0203.png" width=500>
</center>
<br><br>
And repeat the above process over and over again to understand what actions lead to positive rewards and favorable states and what actions lead to negative rewards and unfavorable states.<br><br>

Apply the [bellman equation](https://csh970605.github.io/posts/Bellman_Equation/) to the states collected through actions to calculate the probability of the action to be finally taken and take the action.
And also applies [Living Penalty](https://csh970605.github.io/posts/Living_Penalty/) to avoid infinite loop.
<br><br><br>

# Algorithm of Deep Reinforcement Learning

+ [Twin Delayed Deep Deterministic Policy Gradient(TD3)](https://csh970605.github.io/posts/TD3/)