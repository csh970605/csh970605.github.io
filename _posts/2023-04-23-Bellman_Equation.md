---
title: Bellman Equation
author: SeHoon
date: 2023-04-23 16:22:30 +0900
categories: [Deep Reinforcement Learning, DRL_Theory]
tags: [deep reinforcement learning, python]
math: true
mermaid: true
---

# What is Bellman Equation
Bellman Equation writes the value of a decision problem at a certain point in time in terms of the payoff from some initial choices and the value of the remaining decision problem that results from those initial choices.
<br><br><br>

# The formula of Bellman Equation

<center>

$ V(s)\ =\ max(R(s,a)\ +\ \gamma V(s')) $
</center>

+ s : Current state or given state.
+ s' : The following state. = The state that ends after this state.
+ a : Action.
+ R(s, a) : Reward.

<br><br>
Since there are few things that are 100% sure in real world, there is more advanced formula based on [MDP](https://csh970605.github.io/posts/MDP/).

