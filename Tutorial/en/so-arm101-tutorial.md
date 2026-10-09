English | [简体中文](../zh-hans/so-arm101-tutorial.md) | [繁體中文](../zh-hant/so-arm101-tutorial.md) | [Deutsch](../de/so-arm101-tutorial.md) | [Español](../es/so-arm101-tutorial.md) | [Français](../fr/so-arm101-tutorial.md) | [Italiano](../it/so-arm101-tutorial.md) | [日本語](../ja/so-arm101-tutorial.md) | [한국어](../ko/so-arm101-tutorial.md) | [Português (BR)](../pt-br/so-arm101-tutorial.md) | [Português (PT)](../pt-pt/so-arm101-tutorial.md)

<title>SO-ARM101 Robotic Arm Tutorial</title>

# Product Overview

The SO-ARM101 is a **low-cost, fully open-source 6-degree-of-freedom robotic arm** built by the LeRobot team under Hugging Face, designed for educational entry, research validation and lightweight industrial prototyping. With high flexibility and a complete open-source ecosystem, it lowers the barrier to applying embodied intelligence and robotics technology.

### 1. Hardware Design: High-Performance, Modular, Easy to Assemble and Customize

- **Structural material**: the core structure combines 3D-printed parts with reinforced load-bearing components, with optimized cable routing and joint design to avoid motion interference, balancing light weight and durability; users can print replacement or extension parts themselves.
- **Drive configuration**: the Follower arm carries **6 12V 30KG high-torque magnetic-encoder servos**, combined with 360° magnetic-encoder feedback and a PID control algorithm — silky, jitter-free motion, high repeat positioning accuracy, strong power and precise movement.
- **Vision system**: comes standard with a **dual-camera intelligent vision system**; the end-effector camera captures close-range grasping detail while the global camera covers the working environment. Fusing data from both cameras builds a 3D model and provides rich data support for imitation learning.
- **Control connection**: equipped with a servo driver board that connects directly to a PC or Raspberry Pi through a USB-C interface — plug and play, which simplifies the hardware connection process and lets you build the control environment quickly.

### 2. Software Ecosystem: Deeply Integrated with LeRobot, Zero-Barrier AI Development

- **Core framework compatibility**: deeply adapted to Hugging Face's **LeRobot open-source robot ML framework**, built on PyTorch, with built-in pretrained models, multi-scenario datasets and a simulation environment, and compatible with well-known open-source datasets such as Stanford ALOHA.
- **Low-latency communication**: uses the **DORA distributed dataflow engine** for low-latency interaction between hardware and algorithms; Python runs 17 times faster than ROS2, and hot code reloading is supported so you can adjust policies in real time without restarting.
- **Full-stack open source**: the hardware 3D print files, software control code, AI training scripts and the entire tutorial set are **completely open source**; users can freely modify and further develop them to quickly implement personalized feature extensions.

### 3. Core Application Scenarios: Full-Scenario Fit from Getting Started to Deployment

1. **Robotics education entry**: provides an end-to-end tutorial from arm assembly and basic programming to AI policy deployment, with a visual operation interface and example code, so beginners can quickly master robot control and AI application skills.
2. **Research algorithm validation**: focused on **imitation learning and reinforcement learning** research, with support for recording human operation data via VR to train the robot; a typical case: based on 50 clips of 15-second operation video, 2 hours of training is enough to master tasks such as folding clothes, inserting a key and sorting materials.
3. **Lightweight industrial prototyping**: low-cost validation of automation solutions, fitting scenarios such as **material handling, precision assembly and parts sorting**, delivering the core functions of an industrial-grade robotic arm at thousand-yuan-class cost for rapid prototype validation.

### 4. Product Advantages

- **Extreme value for money**: the basic version starts at about $100, and the open-source design lowers procurement and secondary-development costs, making it suitable for batch deployment by individuals, laboratories and small-to-medium businesses.
- **Full-chain open source**: hardware, software and tutorials are all fully open with no technical barriers, supporting free customization and feature extension to fit many scenarios quickly.
- **AI-development friendly**: backed by the LeRobot ecosystem, it calls pretrained models and datasets with one click, simplifying the whole flow from data collection and policy training to deployment, and accelerating the rollout of embodied-intelligence algorithms.

### 5. Product Specifications

| **Specification** | **Details** |
|-|-|
| Degrees of freedom | 6 axes (shoulder pan / tilt, elbow flexion, wrist flexion / rotation, gripper open/close) |
| Structural material | 3D-printed parts (PLA+) |
| Drive motors | 12 \* Feetech STS3215 servo motors (12V supply)  <br/>Follower arm STS3215-C018 gear ratio: 1/345  <br/>Leader arm STS3215-C001 gear ratio: 1/345 (shoulder), STS3215-C044 1/191 (elbow), STS3215-C046 1/147 (wrist) |
| Payload capacity | Max end-effector payload 200g (gripper closed) |
| Repeat positioning accuracy | ±1.5mm (affected by calibration and motor backlash) |
| Working radius | Max end-effector reach 350mm |
| Power requirements | Leader: 5V 6A adapter; Follower: 12V 5A adapter (for high-torque demands) |
| Communication interface | USB-C direct connection to PC (control-command transfer) |
| Vision system | Camera (1080P@30FPS, FOV86° undistorted, or fixed-focus 1080P@60FPS FOV100°) |
| Gripper type | PLA+ gripper, TPU gripper, two-finger parallel gripper supported, 0-50mm opening range, max gripping force 5N |
| Control framework | Python-based LeRobot library, providing a motor control API (lerobot.control) |
| Pretrained models | Supports imitation-learning algorithms such as ACT (Action Chunking Transformer) and Diffusion Policy |
| Lightweight model | SmolVLA vision-language-action model (450M parameters): ・Real-time CPU inference (runs on MacBook) ・30% faster asynchronous response ・Only 64 visual tokens per frame ・State visualization: real-time monitoring with the rerun library |
| Overall weight | ≈1.2kg (including motors and cables) |
| Assembled dimensions | Base diameter 120mm, height (fully extended) 650mm |
| Operating temperature | 0℃–40℃ (servo motor limit) |
| Noise level | <45dB (no-load operation) |
| Beginner tutorial | Yes |
| Official GITHUB | Yes |

![The image shows dimension diagrams of the SO-ARM101 robotic arm's Leader and Follower arms, along with the product name, material, dimensions and other information. The dimension diagrams label the size of each part, for example the Leader arm is 525mm long and the Follower arm is 532mm long. The product material is topologically optimized PLA+ and the product dimensions are 111x239x525mm (Leader) and 111x173x532mm (Follower). This image corresponds to the Product Specifications section of the document and visually presents the arm's dimensional specifications.](../en/images/d01-01.png)

| **Item / package name** | **Function / description** |
|-|-|
| LeRobot library | Version: ≥0.1.0 Core control framework: • Python API (lerobot.control) ・Real-time motion planning ・Sensor data stream processing |
| PyTorch | Version: ≥2.0 Deep-learning inference engine (supports models such as SmolVLA) |
| Transformers | Version: ≥4.40.0 Hugging Face model library (loads pretrained ACT/Diffusion Policy) |
| rerun | Version: ≥0.16.0 Real-time robot state visualization tool (3D joint angle / trajectory rendering) |
| ROS 2 | Version: Humble/Foxy Optional: ROS2 driver interface (soarm100_ros package) |
| ACT | Action Chunking Transformer, long-sequence action prediction (e.g. continuous grasping tasks) |
| Diffusion Policy | Diffusion policy, robust control in high-dimensional action spaces (disturbance-resistant manipulation) |
| SmolVLA | Vision-language-action model, multimodal instruction execution (e.g. "grab the red block") ・450M parameters, works on CPU/GPU |

| **Function category** | **Function description** |
|-|-|
| Joint-level control | ・6-axis independent angle / speed control (±180° range) ・Joint soft-limit protection ・Real-time feedback of motor temperature / voltage |
| Cartesian-space control | ・End-effector XYZ coordinate positioning (accuracy ±1.5mm) ・Euler-angle orientation adjustment (Roll/Pitch/Yaw) |
| Gripper operation | ・Stepless 0-50mm opening adjustment ・Dynamic grip-force adjustment (0.1-5N) ・Object-thickness-adaptive gripping |
| Leader/Follower mode | ・Leader arm manual teaching → Follower arm real-time imitation ・Action data recording / playback |

| **Function category** | **Function description** |
|-|-|
| Imitation learning | ・Recording of human demonstration data → training of ACT/Diffusion Policy models ・Support for multi-task policy transfer (e.g. block stacking → object sorting) |
| Multimodal interaction | ・SmolVLA model parses natural-language instructions (e.g. "grab the blue block") ・End-to-end vision-action execution |
| Reinforcement learning interface | ・Gymnasium-compatible environment ・Custom reward functions (e.g. task completion time / energy optimization) |
| Calibration system | ・Leader/Follower zero-point calibration ・Camera-arm hand-eye calibration ・Automatic joint torque compensation |
| Data stream management | ・Recording / playback of datasets in .h5 format ・Hugging Face Hub cloud sync ・Sensor data timestamp alignment |
| Real-time monitoring | ・rerun visualization of joint angles / end-effector trajectory ・Motor abnormality alarms (overheating / stall) ・Communication latency diagnostics |
| ROS 2 integration | ・Publish joint states (/joint_states) ・Subscribe to control commands (/arm_controller) ・Point-cloud stream transfer (/depth_points) |
| Cross-platform deployment | • Linux/Windows/macOS (Python API) ・Docker containerization ・Web remote control (FastAPI interface) |
