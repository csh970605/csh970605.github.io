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
A Boltzmann machine is an unsupervised deep learning model used for recommendation systems. Here is a simple structure of a Boltzmann machine:
<center>
<img src="https://user-images.githubusercontent.com/28240052/231655119-112a4042-a5e5-49d1-8ee2-3f638da49690.png" width=400>
</center>
<br>

There are four significant differences between a Boltzmann machine and other neural networks:
+ There is no output layer.
+ Everything is connected to everything = hyperconnectivity.
+ All connections are bidirectional = boltzmann machine is undirected model.
+ A Boltzmann machine always tries to find the lowest energy state using [EBM](https://csh970605.github.io/posts/EBM/)<br>

Now, let's start to understand Boltzmann machines.<br><br>


## Why are the visible nodes connected?
---
<br>
Unlike other neural networks, a Boltzmann machine doesn't expect input data. That is, a Boltzmann machine generates data regardless of whether it is an input node or a hidden node.
Boltzmann machine doesn't distinguish between visible nodes and hidden nodes. It creates a state system and mutually influences the outcome of the machine.<br>
<br>

## How are datasets used?
---
<br>
It feeds the data set into the Boltzmann machine and adjusts the weights accordingly to help it resemble the system.<br>
<br>

## The benefits of a Boltzmann machine
---
<br>
"After the model finishes learning, that is, after all the weights are adjusted, a Boltzmann machine understands how these parameters interact with each other and what kind of constraints must be placed on each other to model the system.<br>
<br>

## The example of use of Boltzmann machine
---
<br>
Let's assume that we are modeling a nuclear power plant system using a Boltzmann machine.<br><br>
After the modeling is done, we can use the Boltzmann machine to monitor the nuclear power plant.<br><br>
We know the steady state of a nuclear power plant because we model the normal behavior of a nuclear power plant, not the meltdown or explosion of a nuclear reactor. Then the Boltzmann machine helps us understand the abnormal behavior.
<br><br>
This is a great example of using unsupervised learning because you can't unsupervise the meltdown of a nuclear reactor because you can't have examples of meltdowns from various nuclear power plants all over the world.
<br><br>
It's impossible to create training data from real reactor meltdowns. You have to model them autonomously, and that's what Boltzmann machines do. With good examples, you can understand the steady state of a system, and then model what the system will look like in unsteady conditions. It can be used to monitor nuclear power plants because it can recognize the scenario.

<br><br><br>
The reason for increasing the amount of computation is that there are too many nodes to calculate when the Boltzmann machine is applied in practice. So, for simplicity, [RBM](https://csh970605.github.io/posts/RBM/) is devised.
