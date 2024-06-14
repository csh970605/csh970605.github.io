---
title: Living Penalty
author: SeHoon
date: 2023-04-23 08:50:30 +0900
categories: [Deep Reinforcement Learning, DRL_Theory]
tags: [deep reinforcement learning, python]
math: true
mermaid: true
---

# What is Living Penalty?
A living penalty is applied to avoid infinite loops in [Reinforcement Learning](https://csh970605.github.io/posts/Reinforcement_Learning/). Let's assume that we are trying to find a way out of a maze:
<center>
<img src="https://user-images.githubusercontent.com/28240052/234143616-0e6fbcab-0d0b-4b5d-a403-797cb84efbeb.png" width=500>
</center>
<br><br>

At first, we set the living penalty to 0 ($R(s) = 0$). Then, the $V(s)$ will be:
<center>
<img src="https://user-images.githubusercontent.com/28240052/234143918-70dd7260-68aa-4f5a-9d83-9c199f83f85a.png" width=500>
</center>
<br><br>

If we set the living penalty to -0.04($R(s) = -0.04$).
<center>
<img src="https://user-images.githubusercontent.com/28240052/234144252-0d234d31-03ba-4d4b-af55-f343018f762e.png" width=500>
</center>
<br><br>
One thing to note is that the living penalty is applied when the agent leaves the box. Then, the V(s) will be:
<center>
<img src="https://user-images.githubusercontent.com/28240052/234145023-8fd9c988-46dd-4b66-90c2-c31b85256ff2.png" width=500>
</center>
<br><br>

If we set the living penalty to -0.5 ($R(s) = -0.5$), then the $V(s)$ will be:
<center>
<img src="https://user-images.githubusercontent.com/28240052/234145320-0b2ade42-da29-4f55-880a-aedffc0340a3.png" width=500>
</center>
<br><br>

This is more suitable than $R(s) = -0.04$ or $R(s) = 0$. But if we set $R(s) = -2.0$, then the $V(s)$ will be:
<center>
<img src="https://user-images.githubusercontent.com/28240052/234145791-1a821fc2-1419-4664-a27a-9c441826a536.png" width=500>
</center>
<br><br>
This is because living for a long time incurs a bigger penalty than going through the red box.
