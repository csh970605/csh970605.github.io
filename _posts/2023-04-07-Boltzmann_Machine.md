---
title: Boltzmann Machine
author: SeHoon
date: 2023-04-07 14:23:30 +0900
categories: [Deep Learning, DL_Introduction]
tags: [deep learning, python]
math: true
mermaid: true
---

# What is Boltzmann Machine?
Boltzmann machine is unsupervised deep learning that used for recommendation systems.<br>
Here is a simple structure of boltzmann machine:
<center>
<img src="https://user-images.githubusercontent.com/28240052/231655119-112a4042-a5e5-49d1-8ee2-3f638da49690.png" width=400>
</center>
<br>

There are two big differences between boltzmann machine and other neural networks:
+ There is no output layer.
+ Everything is connected to everything = hyperconnectivity.
+ All connections are bidirectional = boltzmann machine is undirected model.<br>

Then, Let's start to understand boltzmann machine.<br><br>


## Why are the visible nodes connected?
---
<br>
Unlike other neural networks boltzmann machine doesn't expect the input datas. That is, boltzmann machine generate datas regardless of whether it is an input node or a hidden node.
Boltzmann machine doesn't distinguish between visible node and hidden nodes. It creates a state system and mutually influences the outcome of that machine.<br>
<br>

## How are datasets used?
---
<br>
It feeds the data set into the Boltzmann machine and adjusts the weights accordingly to help it resemble the system.<br>
<br>

## the benefit of boltzmann machine?
---
<br>
After the model finish the learning that is, all the weigths are adjusted, boltzmann machine understands how these parameters interact with each other and what kind of constraints must be placed on each other to make the system we are modeling.<br>
<br>

## The example of use of Boltzmann machine
---
<br>
Let's assume that we are modeling nuclear power plant system as boltzmann machine.<br><br>
After the modeling is done, we can use the boltzmann machine to monitor the nucler power plant.<br><br>
We know the steady state of a nuclear power plant because we model the normal behavior of a nuclear power plant, not the meltdown or explosion of a nuclear reactor. Then the Boltzmann machine helps us understand the abnormal behavior.
<br><br>
This is a great example of using unsupervised learning because you can't unsupervise the meltdown of a nuclear reactor because you can't have examples of meltdowns from various nuclear power plants all over the world.
<br><br>
It's impossible to create training data from real reactor meltdowns. You have to model them autonomously, and that's what Boltzmann machines do. With good examples, you can understand the steady state of a system, and then model what the system will look like in unsteady conditions. It can be used to monitor nuclear power plants because it can recognize the scenario.

<br><br><br>

# What is Restricted Boltzmann Machine(RBM)
RBM is devised to overcome the limitation of computation. The reason for increasing the amount of computationis that there are too many nodes to calculate when the Boltzmann machine is applied in practice. So, for simplicity, RBM is devised.
<br>
The simple structure of RBM:
<center>
<img src="https://user-images.githubusercontent.com/28240052/231674902-a0784900-9d56-496b-9aad-1da36dd149a4.png" width=700>
</center>
<br><br>
Boltzmann machine and RBM is mostly similar, but there are no connections between hidden nodes. Also, there are no connections between visible nodes.
<br><br><br>

## How is RBM used?
---
<br>

Let's assume we are making a movie recommendation system.<br>
During training of the RBM, we can help the Boltzmann machine represent our system by feeding it data through a process called [contrast divergence]().<br>
Through this process, RBM understand how to allocate hiddennodes to specific features. This process is similar to [CNN](https://csh970605.github.io/posts/CNN).<br>
<br>
For example, there are review scores about Moive 1~6.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/231678815-e1464789-42fc-4fbd-982d-b199dedab9d4.png" width=500>
</center>
<br><br>
If user liked the movie, score will be 1. If not, score will be 0. There is also a blank, meaning that user did not see that movie.<br><br>
By feeding this data into the limiting Boltzmann machine, the machine understands our system better, and as it adjusts itself, it can better represent our system and better understand and express the connectivity within it, because users have biases and tastes, and that's reflected in this data.<br><br>

Let's take a simple example.<br>
Movies 3, 4, and 6 generally have similar ratings. Most, but not always, user who liked movies 3 and 4 also liked movie 6, and user who liked movies 6 and 4 or 6 and 3 probably rated movies 4 or 3. If user liked 6 and 3, user will like 4, and if you didn't like movies 3 and 4, user will  hate 6 too.<br>
This is what RBM going to do.







<center>
<img src="" width=400>
</center>
<br><br>
