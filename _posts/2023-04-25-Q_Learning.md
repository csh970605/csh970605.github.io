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
Q-Learning is almost the same as the [MDP](https://csh970605.github.io/posts/MDP/). One key difference from MDP is that Q-Learning applies Temporal Difference to make changes happen gradually. Why do the changes happen gradually? It's because there are situations where less probable events occur. Using these Q-values, we can develop a deep learning algorithm called Deep Q-Learning.
<br><br><br><br>

# Formula of Q Learning

<center>

$ Q_{t}(s, a)\ =\ Q_{t-1}(s,a)\ +\ \alpha(R(s,a)\ +\ \gamma(maxQ(s',a')\ -\ Q_{t-1}(s,a))) $
</center>

<br><br><br><br>

# What is deep Q Learning?
Deep Q-Learning is a deep learning algorithm that uses Q-values. Deep Q-learning learns as:
<center>
<img src="https://user-images.githubusercontent.com/28240052/234835771-a3202160-f6c3-46f5-a0d3-67783004629c.png" width=700>
</center>
<br><br>

Q-Targets are the values calculated through [Q Learning](https://csh970605.github.io/posts/Q_Learning/#how-does-q-learning-learn-in-deep-learning). Deep Q-Learning aims to minimize $L$ by adjusting weights.
<br><br>

After learning is finished, Deep Q-Learning chooses an action through the [softmax function](https://csh970605.github.io/posts/Softmax/).
<center>
<img src="https://user-images.githubusercontent.com/28240052/234836858-2c974ffb-464e-46cf-bc35-43df3b884346.png" width=500>
</center>
<br><br>

