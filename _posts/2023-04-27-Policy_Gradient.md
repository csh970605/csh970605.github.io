---
title: Policy Gradient
author: SeHoon
date: 2023-04-27 19:33:30 +0900
categories: [Deep Reinforcement Learning, DRL_Theory]
tags: [deep reinforcement learning, python]
math: true
mermaid: true
---

# What is Policy Gradient?

Policy Gradient is one of the component of [TD3]().<br>

The goal of policy($\pi $) gradient is to optimize the expected return by optimizing $\theta$.<br>
Then how policy gradient calculate reward? The reward function is:

<center>
<font size=4>

$ J(\theta)\ =\ \Sigma_{s\in S}d^{\pi}(s)V^{\pi}(s)\ =\ \Sigma_{s\in S}d^{\pi}(s)\Sigma_{a \in A} \pi_{\theta}(a|s)Q^{\pi}(s,a) $
</font>
</center>
<br><br>

The return of policy gradient affects the reward of [bellman equation](https://csh970605.github.io/posts/Bellman_Equation/).<br>

<center>
<font size=4>

$ R_{t}\ =\ \Sigma_{i=t}^{T} \gamma^{i-t}r(s_{i}, a_{i}) $
</font>
</center>
<br><br>

<center>
<img src="" width=500>
</center>
<br><br>