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

Policy Gradient is used to update the [actor model](https://csh970605.github.io/posts/Actor_Critic/) using the Q-values optimized by the [critic model](https://csh970605.github.io/posts/Actor_Critic/). The goal of the policy $\pi_{\phi}$ gradient is to optimize the expected return by optimizing $\phi$. How does the policy gradient update weights? The function is:

<center>

$ \phi_{t+1}\ =\ \phi_{t}\ +\ \alpha \nabla_{\phi}J(\pi_{\phi})|_{\phi_{t}} $
<br>

$ \nabla_{\phi}J(\phi)\ =\ \nabla_{\phi}\sum_{s\in S}d^{\pi}(s)V^{\pi}(s)\ =\ \nabla_{\phi}\sum_{s\in S}d^{\pi}(s)\sum_{a \in A} \pi_{\phi}(a|s)Q^{\pi}(s,a) $

</center>
<br><br>

The return of the policy gradient affects the reward in the [Bellman Equation](https://csh970605.github.io/posts/Bellman_Equation/).<br>
The return of the policy graddient is:

<center>

$ R_{t}\ =\ \sum_{i=t}^{T} \gamma^{i-t}r(s_{i}, a_{i}) $
</center>
<br><br>
<br>
The structure of the Policy Gradient is::
<center>
<img src="https://user-images.githubusercontent.com/28240052/235079540-87c8ddfe-5f2d-422a-866a-bba49a308ead.png" width=500>
</center>
<br><br>

