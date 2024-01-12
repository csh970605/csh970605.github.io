---
title: Mobile ALOHA
author: SeHoon
date: 2024-01-15 10:42:30 +0900
categories: [Papers, DeepLearning]
tags: [Papers, DeepLearning, ImitationLearning, AMRLabs]
math: true
mermaid: true
---

# Mobile ALOHA

Mobile ALOHA is a low cost and whole body teleoperation system for data collection. It augments the [ALOHA]() system for data collection.<br>

With the data collected by Mobile ALOHA perform supervised behavior cloning and find co-training with existing static ALOHA datasets to booost performance on mobile manipulation tasks.<br>

According to the paper, they increased success rates by up to 90% allowing Mobile ALOHA to autonomously complete complex mobile manipulation tasks.<br>

<br><br><br>

# Why Did They Make Mobile ALOHA?

Most of the traditional robots allow people to teach arbitrary skills to robots so far, but many tasks in realistic, everyday environments require whole-body coordination of the both mobility and dexterous manipulation, rather than just individual mobility or manipulation behaviors.<br>

To solve that problem, paper studied the feasibility of extending imitation learning to tasks that require whole-body control of bimanual mobile robots.<br>

<br><br><br>

# How Did They Make Mobile ALOHA?

They encountered two main factors that hinder the wide adoption of imitation learning for bimanual mobile manipulation while they made Mobile ALOHA.<br>

1. Lack accessible, plug-and-play hardware for whole body teleoperation:<br>
    - They used additional hardware and calibration to enable teleoperation on the robot platform like:

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0313ac9c-c735-4d58-b30f-5d5a9684625e", width=500, height=500><br><br>
    </center>

2. Prior robot learning(ALOHA) works have not demonstrated high-performance bimanual mobile manipulation for complex tasks:<br>
    - To solve this problem, they decided to leverage data from the ALOHA datasets. Despite the differences in tasks and morphology, they got positive transfer in nearly all mobile manipulation tasks, attaining equivalent or better performance and data efficiency than policies trained using only Mobile ALOHA data.<br>

<br>
As a result, they got the following four results:<br>

1. Mobile : The system can move at a speed comparable to human walking, around 1.42m/s.<br>

2. Stable : It is stable when manipulating heavy household objects, such as pots and cabinets.<br>

3. Whole-body teleoperation: All degrees of freedom can be teleoperated simultaneously, including both arms and the mobile base. <br>

4. Untethered : Onboard power and compute.<br>

They choose AgileX Tracer AGV("Tracer") as the mobile base at "Mobile" and "Stable" as you can see above.<br>
For "Whole-body teleoperation", they selected a teleoperation system that allows simultaneous control of both the base and two arms.<br>
Finally, they soved the "Untetherd" problem by attaching the battery and laptop on the robot like:
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0313ac9c-c735-4d58-b30f-5d5a9684625e", width=500, height=500><br><br><br><br>
</center><br><br>

# How They Did Co-training with Static ALOHA Data?

To solve the problem that the policies trained on the specialized datasets which is collected by human operator are often not robust to the perceptual perturbations such as distractors or lighting changes due to the limited visual diversity in the datasets, they used a co-training pipeline that leverages the existing static ALOHA datasets to improve the performance of imitation learning.

<br><br>

## Formula of The Pipeline

<center>

$\mathbb{E}_{(o^{i}, a^{i}_{arms},a^{i}_{base}) \ \sim \ D^{m}_{mobile}}[L(a^{i}_{arms},a^{i}_{base},\pi^{m}(o^{i}))] \ + \\ \mathbb{E}_{(o^{i},a^{i}_{arms}) \ \sim \ D_{static}}[L(a^{i}_{arms},[0,0], \pi(o^{i}))]$<br>

</center>

where :<br>
+ $o^{i}$ : observation consisting of two wrist camera RGB observations

+ $a_{arm}$ : bimanual actions which is formulated as target joint positions $a_{arms} \in \mathbb{R}^{14}$.<br>

+ $a_{base}$ : the base actions that is formulated as target base linear and angular velocities $a_{base} \in \mathbb{R}^{2}$.<br>

+ $D^{m}_{mobile}$ : Mobile ALOHA dataset for a task m.<br>

+ $\pi^{m}(o^{i})$ : the training objective for a mobile manipulation policy $\pi^{m}$ for a task m<br>

+ $D_{static}$ : static ALOHA data<br>
 
The Formula means:
+ The sum of the expected values of $L(a^{i}_{arms},[0,0], \pi(o^{i}))$ for o, a, and $\pi^{m}(o^{i})$ sampled from $D^{m}_{mobile}$ and the expected values of L2 for a2, b2 sampled from D2