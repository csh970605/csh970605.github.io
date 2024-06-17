---
title: Actor-Critic
author: SeHoon
date: 2023-04-28 16:20:30 +0900
categories: [Deep Reinforcement Learning, DRL_Theory]
tags: [deep reinforcement learning, python]
math: true
mermaid: true
---

# What is Actor-Critic?

Actor-Critic is a component of [TD3](https://csh970605.github.io/posts/TD3/). As you can guess from the name, Actor-Critic is composed of two networks:

<br><br>

## Actor network<br>
The Actor is the same as the [policy gradient](https://csh970605.github.io/posts/Policy_Gradient/). The Actor decides on actions when states are given. The shape of the Actor is:
<center>
<img src="https://user-images.githubusercontent.com/28240052/235081848-144d93a8-a22b-44d9-b63e-52bfec3c75ab.png" width=500>
</center>
<br><br>



## Critic network<br>
The Critic evaluates the quality of states. The shape of the Critic is:
<center>
<img src="https://user-images.githubusercontent.com/28240052/235081722-1135c4e5-9ad0-466d-821d-e7588ef0af12.png" width=500>
</center>
<br><br>

Both of networks update the policy parameters through gradient ascent like policy gradient:
<center>

$ \theta_{t+1}\ =\ \theta_{t}\ +\ \alpha \nabla_{\theta}J(\pi_{\theta})|_{\theta_{t}} $
<br>

$ \nabla_{\theta}J(\theta)\ =\ \nabla_{\theta}\sum_{s\in S}d^{\pi}(s)V^{\pi}(s)\ =\ \nabla_{\theta}\sum_{s\in S}d^{\pi}(s)\sum_{a \in A} \pi_{\theta}(a|s)Q^{\pi}(s,a) $

</center>