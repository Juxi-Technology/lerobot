English | [简体中文](../zh-hans/index.md) | [繁體中文](../zh-hant/index.md) | [Deutsch](../de/index.md) | [Español](../es/index.md) | [Français](../fr/index.md) | [Italiano](../it/index.md) | [日本語](../ja/index.md) | [한국어](../ko/index.md) | [Português (BR)](../pt-br/index.md) | [Português (PT)](../pt-pt/index.md)

# Contents

## **Click the two icons in the top-left corner to expand the full chapter list**

![The image shows an icon made up of a dot and three parallel lines. This icon appears in a document introducing LeRobot, whose context describes LeRobot as HuggingFace's open-source embodied addCriterion embodied intelligent robot software framework that lowers the barrier to data collection, algorithm training and inference deployment for reinforcement learning and imitation learning (VLA), with imitation learning (VLA) being the main focus. This icon may represent the LeRobot software framework or a related feature.](../en/images/d02-01.png)

![The image shows a play-button icon, a white triangle, located in the lower-left corner of the frame. This icon relates to the document's introduction to LeRobot, which is HuggingFace's open-source embodied intelligent robot software framework that lowers the barrier to data collection, algorithm training and inference deployment for reinforcement learning and imitation learning (VLALA), with imitation learning (VLA) being the main focus. This icon may indicate video or demo content to help users understand the LeRobot material.](../en/images/d02-02.png)

![The image shows the text "Speedrunning Embodied Intelligence VLA" against a light gradient background. In the frame, one hand holds a white object while another hand operates a robotic arm with red wiring. A speech bubble reading "Grab!" appears in the lower-right corner. The image relates to the document's introduction to LeRobot, an embodied intelligent robot software framework that lowers the barrier to imitation learning (VLA)); this picture may be intended to visually present the use of VLA in robot manipulation and its role in imitation learning.](../en/images/d02-03.png)

## What Is Embodied Intelligence?

Intelligence with a body. It connects AI to various physical hardware entities, such as:

Quadruped robot dogs, bipedal humanoid robots, wheeled-legged robots, drones, self-driving cars

## What Is LeRobot?

LeRobot is HuggingFace's open-source `embodied intelligent robot software framework`

GitHub address: https://github.com/huggingface/lerobot

It lowers the barrier to **data collection, algorithm training and inference deployment** for reinforcement learning and **imitation learning (VLA)**, with **imitation learning (VLA)** being the main focus

- Which robots can be developed with LeRobot?

From the thousand-yuan-class SO-ARM 101 robotic arm and the LeKiwi cart, up to the tens-of-thousands-yuan AgileX piper arm, the Huaxinjing StarAI arm and the Hope-JR dexterous hand, and on to the hundreds-of-thousands-yuan Unitree G1 humanoid robot. LeRobot has become the standard for data collection and algorithm training in the embodied intelligence industry.

You can also adapt your own robot to the LeRobot framework.

- LeRobot datasets and models

LeRobot defines its own imitation-learning dataset format. You can view, use, download and train on all public datasets and models on HuggingFace, and you can also upload your own datasets to HuggingFace.

## What Is the SO-ARM 101 Robotic Arm?

This tutorial takes the SO-ARM 101 robotic arm as an example; it uses 3D-printed structural parts and Feetech servos, at a very low cost.

This is an embodied-intelligence body even a poor student can afford, and it is one of the bodies officially recommended by LeRobot.

The arm consists of two arms: a Leader arm and a Follower arm. Each arm has 5 degrees of freedom plus 1 gripper degree of freedom.

## What Computer Configuration Do I Need

An ordinary Windows laptop can handle everything up to training.

An ordinary Mac can handle everything.

An Ubuntu machine with an NVIDIA GPU can handle everything.

In this tutorial we use a [cloud GPU platform](https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1) to train models, so your own computer does not need a high-end configuration.

## What Is **Imitation Learning and VLA**?

Humans drag the robot to demonstrate and collect a dataset. That dataset is then used to train an imitation-learning algorithm, which is finally deployed on the robot, letting it imitate human actions autonomously and generalize to the real environment. No teleoperation or remote control is needed.

For example, in the video above, a human drags the SO-ARM robotic arm to grab a crayfish, dip it in seasoning and drop it into hot oil, and the arm ultimately performs this action on its own. Even with a new crayfish, it can react and complete the action at any time.

Imitation learning also has a cutting-edge, fashionable name: VLA (Vision-Language-Action large model). This is also the embodied-intelligence research field that is currently developing fastest, attracting the hottest investment, seeing the fiercest China-US competition, enjoying the most prosperous open-source ecosystem, drawing intense media attention, and drawing in countless master's and doctoral students.

The algorithms LeRobot mainly adapts are imitation-learning ones, such as ACT, Diffusion Policy, SmolVLA, Pi0, Pi0.5, Wall-OSS and others.

The imitation learning in this tutorial is exclusively VLA.
