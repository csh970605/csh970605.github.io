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
Then why do the changes happen slowly? It's because there are situations where other things happen that are less probable.<br><br>
Through these Q values, we can make deep learning algorithm called deep Q learning.
<br><br><br>

# Formula of Q Learning

<center>

$ Q_{t}(s, a)\ =\ Q_{t-1}(s,a)\ +\ \alpha(R(s,a)\ +\ \gamma(maxQ(s',a')\ -\ Q_{t-1}(s,a))) $
</center>

<br><br><br>

# What is deep Q Learning?
Deep Q learning is a deep learning algorithm which uses Q value.<br>
Deep Q learning learns as:
<center>
<img src="https://user-images.githubusercontent.com/28240052/234835771-a3202160-f6c3-46f5-a0d3-67783004629c.png" width=700>
</center>
<br><br>

Q-Targets are the values that we calculated through [Q Learning](https://csh970605.github.io/posts/Q_Learning/#how-does-q-learning-learn-in-deep-learning).<br>
Deep Q learning tries to make L lower by adjusting weights.
<br><br>

After learning finished, deep Q learning choose an action through [softmax function](https://csh970605.github.io/posts/Softmax/).
<center>
<img src="https://user-images.githubusercontent.com/28240052/234836858-2c974ffb-464e-46cf-bc35-43df3b884346.png" width=500>
</center>
<br><br>

