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
 The reason for increasing the amount of computationis that there are too many nodes to calculate when the Boltzmann machine is applied in practice. So, for simplicity, [RBM](https://csh970605.github.io/posts/RBM/) is devised.
