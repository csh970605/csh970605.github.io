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

Policy Gradient is used to update [actor model](https://csh970605.github.io/posts/Actor_Critic/) through the Q values optimized by [critic model](https://csh970605.github.io/posts/Actor_Critic/).

The goal of policy($\pi $) gradient is to optimize the expected return by optimizing $\theta$.<br>
Then how policy gradient update weights? The function is:

<center>
<font size=4>

$ \theta_{t+1}\ =\ \theta_{t}\ +\ \alpha \nabla_{\theta}J(\pi_{\theta})|_{\theta_{t}} $
<br>

$ \nabla_{\theta}J(\theta)\ =\ \nabla_{\theta}\Sigma_{s\in S}d^{\pi}(s)V^{\pi}(s)\ =\ \nabla_{\theta}\Sigma_{s\in S}d^{\pi}(s)\Sigma_{a \in A} \pi_{\theta}(a|s)Q^{\pi}(s,a) $

</font>
</center>
<br><br>

The return of policy gradient affects the reward of [bellman equation](https://csh970605.github.io/posts/Bellman_Equation/).<br>
The return of policy graddient is:

<center>
<font size=4>

$ R_{t}\ =\ \Sigma_{i=t}^{T} \gamma^{i-t}r(s_{i}, a_{i}) $
</font>
</center>
<br><br>
<br>
And the shape of Policy Gradient is:
<center>
<img src="https://user-images.githubusercontent.com/28240052/235079540-87c8ddfe-5f2d-422a-866a-bba49a308ead.png" width=500>
</center>
<br><br>

