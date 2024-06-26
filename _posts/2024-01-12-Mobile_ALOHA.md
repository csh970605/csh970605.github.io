---
title: Mobile ALOHA
author: SeHoon
date: 2024-01-12 10:42:30 +0900
categories: [Papers, DeepLearning]
tags: [Papers, DeepLearning, ImitationLearning, AMRLabs]
math: true
mermaid: true
---

# Mobile ALOHA
Mobile ALOHA is a low-cost, whole-body teleoperation system for data collection. It augments the [ALOHA](https://csh970605.github.io/posts/ALOHA/) system for data collection.<br>

With the data collected by Mobile ALOHA, perform supervised behavior cloning and co-training with existing static ALOHA datasets to boost performance on mobile manipulation tasks.<br>

According to the [paper](https://arxiv.org/abs/2401.02117), success rates increased by up to 90%, allowing Mobile ALOHA to autonomously complete complex mobile manipulation tasks.<br>

<br><br><br>

# Why Did They Make Mobile ALOHA?

Most traditional robots allow people to teach arbitrary skills to robots; however, many tasks in realistic, everyday environments require whole-body coordination of both mobility and dexterous manipulation, rather than just individual mobility or manipulation behaviors.<br>

To address this problem, the paper studied the feasibility of extending imitation learning to tasks that require whole-body control of bimanual mobile robots.<br>

<br><br><br>

# How Did They Make Mobile ALOHA?

They encountered two main factors that hinder the wide adoption of imitation learning for bimanual mobile manipulation while developing Mobile ALOHA.<br>

1. Lack of accessible, plug-and-play hardware for whole-body teleoperation:<br>
    - They used additional hardware and calibration to enable teleoperation on the robot platform, such as:<br>

    <center>
    <img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/b8297056-2532-4beb-9f6f-c4e89752898b" width="500" height="500">
    </center>
    <br><br>

2. Prior robot learning (ALOHA) works have not demonstrated high-performance bimanual mobile manipulation for complex tasks:<br>
    - To solve this problem, they decided to leverage data from the ALOHA datasets. Despite the differences in tasks and morphology, they achieved positive transfer in nearly all mobile manipulation tasks, attaining equivalent or better performance and data efficiency than policies trained using only Mobile ALOHA data.<br>

<br>
As a result, they achieved the following four outcomes:<br>

1. Mobile : The system can move at a speed comparable to human walking, around 1.42 m/s.<br>

2. Stable : It is stable when manipulating heavy household objects, such as pots and cabinets.<br>

3. Whole-body teleoperation: All degrees of freedom can be teleoperated simultaneously, including both arms and the mobile base. <br>

4. Untethered : Onboard power and compute.<br>

They chose the AgileX Tracer AGV ("Tracer") as the mobile base for "Mobile" and "Stable," as you can see above. For "Whole-body teleoperation", they selected a teleoperation system that allows simultaneous control of both the base and two arms. Finally, they solved the "Untethered" problem by attaching the battery and laptop to the robot, as shown below:<br>

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/b8297056-2532-4beb-9f6f-c4e89752898b" width="500" height="500">
</center><br><br><br><br>



# How Did They do Co-training with Static ALOHA Data?

To address the issue that policies trained on specialized datasets collected by human operators are often not robust to perceptual perturbations such as distractors or lighting changes due to the limited visual diversity in the datasets, they used a co-training pipeline that leverages the existing static ALOHA datasets to improve the performance of imitation learning.

<br><br>

## Formula of The Pipeline

<center>

$\mathbb{E}_{(o^{i}, a^{i}_{\text{arms}},a^{i}_{\text{base}}) \ \sim \ D^{m}_{\text{mobile}}}[L(a^{i}_{\text{arms}},a^{i}_{\text{base}},\pi^{m}(o^{i}))] \ + \\ \mathbb{E}_{(o^{i},a^{i}_{arms}) \ \sim \ D_{\text{static}}}[L(a^{i}_{\text{arms}},[0,0], \pi(o^{i}))]$<br>

</center>

where :<br>

+ $o^{i}$ : observation consisting of two wrist camera RGB observations

+ $a_{\text{arms}}$ : bimanual actions formulated as target joint positions $a_{arms} \in \mathbb{R}^{14}$.<br>

+ $a_{\text{base}}$ : the base actions formulated as target base linear and angular velocities $a_{\text{base}} \in \mathbb{R}^{2}$.<br>

+ $D^{m}_{\text{mobile}}$ : Mobile ALOHA dataset for a task $m$.<br>

+ $\pi^{m}(o^{i})$ : the training objective for a mobile manipulation policy $\pi^{m}$ for a task $m$.<br>

+ $D_{\text{static}}$ : static ALOHA data<br>
 
The Formula represents:<br>


+ The sum of the expected values of $L(a^{i}_{\text{arms}},[0,0], \pi^{m}(o^{i}))$ for $o^{i}$, $a^{i}_{\text{arms}}$, and $a^{i}_{\text{arms}}$ sampled from $D^{m}_\text{mobile}$ and the expected values of $L(a^{i}_{\text{arms}},[0,0], \pi^{m}(o^{i}))$ for $o^{i}$, $a^{i}_{\text{arms}}$ sampled from $D_{\text{static}}$.<br>


They sample with equal probability from $D_{\text{static}}$ and $D^{m}_{\text{mobile}}$ and set the batch size to 16.<br>
Since $D_{\text{static}}$ data points have no mobile base actions, they added zero-padding to the action labels to make the two datasets have the same dimensions.<br>
Also, they ignored the front camera in the $D_{\text{static}}$ data so that both datasets have three cameras.<br>
Finally, they normalized every action based on the statistics of $D^{m}_{\text{mobile}}$ alone.
<br>

In their experiments, they combined the co-training recipe with multiple base imitation learning approaches, including ACT, Diffusion Policy, and VINN.

<br><br><br><br>

# Tasks

They selected 6 tasks:

+ [Wipe Wine](https://csh970605.github.io/posts/Mobile_ALOHA/#wipe-wine)<br>

+ [Cook Shrimp](https://csh970605.github.io/posts/Mobile_ALOHA/#cook-shrimp)<br>

+ [Wash Pan](https://csh970605.github.io/posts/Mobile_ALOHA/#wash-pan)<br>

+ [Use Cabinet](https://csh970605.github.io/posts/Mobile_ALOHA/#use-cabinet)<br>

+ [Take Elevator](https://csh970605.github.io/posts/Mobile_ALOHA/#take-elevator)<br>

+ [Push Chairs](https://csh970605.github.io/posts/Mobile_ALOHA/#push-chairs)<br>

+ [High Five](https://csh970605.github.io/posts/Mobile_ALOHA/#high-five)<br>

<br><br>
Below, you can see all tasks:

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/d84b9dda-807c-49fd-91ed-b43d7a87117c">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/05d7aedb-0e61-464c-bfff-9daeb4c3cdbc">
</center>

<br><br>

## Wipe Wine

+ The robot base is initialized within a square of $1.5 m \times 1.5 m$ with a yaw of up to 30° (Init).<br>

+ It first navigates to the sink and picks up the towel hanging on the faucet (#1).<br>

+ It then turns around and approaches the kitchen island, picks up the wine glass (randomized in a $30 cm \times 30 cm$ area), and wipes the spilled wine (#2).<br>

+ It then puts down the wine glass on the table (#3).<br>

+ Each demo consists of 1300 steps or 26 seconds.<br>
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/091e6d7b-38ff-49df-bbf3-f2070f8661f6">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/459da415-bab6-4511-9562-0df94a148104">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/a52b6ea6-3df5-4125-ba1e-8bfd3b4b9a0e">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/1d0fedc7-8a4f-4349-9261-28fecdbd2041">
</center>

<br><br>

## Cook Shrimp
+ The robot's position is randomized up to 5 cm, and all objects' positions are randomized up to 2 cm (init).<br>
+ The right gripper first pours oil into the hot pan (#1).<br>
+ After that, it pours raw shrimp into the hot pan (#2).<br>
+ With the left gripper lifting the pan at an angle, the right gripper grasps the spatula and flips the shrimp (#3)..<br>
+ The robot then turns around and pours the shrimp into an empty bowl(#4).<br>
+ Each demo consists of 3750 steps or 75 seconds.<br>
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/b2f47b1c-cd01-4536-9267-d69fece67075">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/06c29bbe-4e71-4343-a615-a0cb368e66b8">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/f6d5a8ed-fa87-406c-ba2f-a633b56a4ccd">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/780c6c63-3731-4a00-a071-e885d13231f9">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/1e2ab957-a0d5-4f97-a18c-b2bbe443c499">
</center>

<br><br>

## Wash Pan
+ The pan's position is randomized up to 10 cm with a yaw of up to $45^{\circ}$.<br>
+ The left gripper grasps the pan (#1).<br>
+ he right gripper opens and then closes the faucet while the left gripper holds the pan to receive the water (#2).<br>
+ The left gripper then swirls the water inside the pan and pours it out (#3).<br>
+ Each demo consists of 110 steps or 22 seconds.<br>
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/d52a06ca-c072-4733-90b5-200bc730d928">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/ac6c360c-2679-4a59-82fc-bfc0b53dcc22">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0d86bb1c-7470-4f61-8c73-ea4425bbbc97">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/e0d45fa9-6958-41ba-b042-bfd5a4593ba1">
</center>

<br><br>

## Use Cabinet
+ TThe robot's position is randomized up to 10 cm, and the pots' positions are randomized up to 5 cm (init).<br>
+ The robot approaches the cabinet, grasps both handles, then backs up, pulling both doors open (#1).<br>
+ Both arms grasp the handles of the pot, move forward, and place it inside the cabinet (#2, #3).<br>
+ The robot backs up and closes both cabinet doors(#4).<br>
+ Each demo consists of 1500 steps or 30 seconds.<br>
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/92cc4b26-5c19-4117-9beb-bc12ecfc5342">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/00ef7d9e-2ff0-4550-a404-b6af06f72081">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/54069880-5fb2-4a3a-85ab-ddfd9006e3d5">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/39ab347c-1dad-471c-a899-ba02df2d70b4">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/1353c398-8225-4731-b17f-17ad78a292c1">
</center>

<br><br>

## Take Elevator
+ The robot starts 15 m from the elevator and is randomized across the 10 m wide lobby (init).<br>
+ The robot goes around a column to reach the elevator button (#1).<br>
+ The right gripper presses the button (#2).<br>
+ The robot enters the elevator (#3).<br>
+ Each demo consists of 2250 steps or 45 seconds.<br>
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/1330c6ed-3414-4fdb-ab46-304d7967e948">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3fadfe0d-a08d-4afc-8630-f035b0f7ec17">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/27e22abd-10b3-4dc8-9760-9fc9dc369f50">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/1c281376-fe4e-46b6-bf30-4695d7c4c0f7">
</center>

<br><br>

## Push Chairs
+ The robot's initial position is randomized up to 10 cm (init).<br>
+ The demonstration dataset contains the robot pushing the first 3 chairs (#1, #2, #3).<br>
+ Each demo consists of 2000 steps or 40 seconds.<br>
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0f8cec80-2619-4f80-8964-c90f05cf0e12">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/92ff0df7-b6b4-4fc9-952c-e2a17c24b8ec">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/3b1f2790-b24f-4347-9acf-a8da944428d7">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/07c61284-8e7b-467f-9d54-f60cd5006457">
</center>

<br><br>

## High Five
+ The robot base is initialized next to the kitchen island (init).<br>
+ The robot keeps moving around the kitchen island until a human is in front of it, then gives a high five to the human (#1, #2).<br>
+ Each demo consists of 2000 steps or 40 seconds.<br>
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/36d6836e-d2b7-468a-aadd-a4ecf22da1ba">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/54dd2d6c-31eb-41ef-8eb3-56fb641e9ca1">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/9d11a79d-4979-42ab-93bd-538def4c0ad4">
</center>

<br><br><br><br>

# Result

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/12f366bf-881d-43b3-9c11-0036dfd8e2e4">
</center>

It is a very clever idea to train robots through teleoperation. This method allows anyone, even without any knowledge about robots, to train precise motions through teleoperation. Additionally, Mobile ALOHA overcomes the disadvantages of traditional robot arm manipulation algorithms, such as KDL.