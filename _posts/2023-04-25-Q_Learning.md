---
title: Q Learning
author: SeHoon
date: 2023-04-23 08:51:30 +0900
categories: [Deep Reinforcement Learning, DRL_Theory]
tags: [deep reinforcement learning, python]
math: true
mermaid: true
---

# What is Q Learning?
Q learning is almost same as [MDP](https://csh970605.github.io/posts/MDP/).<br>
One thing that differs from MDP is Q learning applies Temporal Difference to make changes happen slowly. <br>
Then why do the changes happen slowly? It's because there are situations where other things happen that are less probable.
<br><br><br>

# Formula of Q Learning

<center>
<font size=4>

$ Q_{t}(s, a)\ =\ Q_{t-1}(s,a)\ +\ \alpha(R(s,a)\ +\ \gamma(maxQ(s',a')\ -\ Q_{t-1}(s,a))) $
</font>
</center>




<center>
<img src="" width=500>
</center>
<br><br>