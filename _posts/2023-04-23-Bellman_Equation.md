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
The Bellman Equation expresses the value of a decision problem at a certain point in time in terms of the payoff from initial choices and the value of the remaining decision problem resulting from those initial choices.
<br><br><br><br>

# The Formula of the Bellman Equation

<center>

$ V(s)\ =\ max(R(s,a)\ +\ \gamma V(s')) $
</center>

+ s : Current state or given state.
+ s' : The following state. = The state that ends after this state.
+ a : Action.
+ R(s, a) : Reward.

<br><br>
Since few things are 100% certain in the real world, there is a more advanced formula based on the [MDP](https://csh970605.github.io/posts/MDP/).

