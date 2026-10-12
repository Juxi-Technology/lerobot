English | [简体中文](README_zh.md)

<p align="center">
  <img alt="LeRobot, Hugging Face Robotics Library" src="./media/readme/lerobot-logo-thumbnail.png" width="100%">
</p>

**LeRobot** aims to provide models, datasets, and tools for real-world robotics in PyTorch. The goal is to lower the barrier to entry so that everyone can contribute to and benefit from shared datasets and pretrained models.

🤗 A hardware-agnostic, Python-native interface that standardizes control across diverse platforms, from low-cost arms (SO-100) to humanoids.

🤗 A standardized, scalable LeRobotDataset format (Parquet + MP4 or images) hosted on the Hugging Face Hub, enabling efficient storage, streaming and visualization of massive robotic datasets.

🤗 State-of-the-art policies that have been shown to transfer to the real-world ready for training and deployment.

🤗 Comprehensive support for the open-source ecosystem to democratize physical AI.

## 📚 Tutorials

This repository ships the complete **SO-ARM101** course: nine steps from installing LeRobot to deploying a trained policy, plus assembly, simulation and reference material. Every chapter exists in **11 languages** under the same filename.

> 📁 **[Tutorial/README.md](Tutorial/README.md)** indexes the whole `Tutorial/` folder — both tutorial sets, all 11 languages.

| # | Chapter | What it covers |
|:--:|---|---|
| ★ | [**Course home**](Tutorial/lerobot%20tutorials/en/index.md) | What embodied AI, LeRobot and the SO-ARM101 are; what computer you need |
| 1 | [Install the LeRobot environment](Tutorial/lerobot%20tutorials/en/01-install-lerobot.md) | Setup on Windows, macOS or Ubuntu |
| 2 | [Find the serial port number](Tutorial/lerobot%20tutorials/en/02-find-serial-port.md) | Talk to the arm over USB |
| 3 | [Calibrate the arm](Tutorial/lerobot%20tutorials/en/03-calibrate-arm.md) | One-time calibration of the leader and follower arms |
| 4 | [Teleoperation](Tutorial/lerobot%20tutorials/en/04-teleoperation.md) | Drive the follower arm by hand-moving the leader arm |
| 5 | [Teleoperation with cameras](Tutorial/lerobot%20tutorials/en/05-teleoperation-with-camera.md) | Add the wrist and top cameras |
| 6 | [Collect a dataset — real hardware](Tutorial/lerobot%20tutorials/en/06-collect-dataset-real.md) | Record, replay and upload demonstrations |
| 7 | [Collect a dataset — LeIsaac simulation](Tutorial/lerobot%20tutorials/en/07-collect-dataset-leisaac-sim.md) | Collect data without a physical arm |
| 8 | [Train a model](Tutorial/lerobot%20tutorials/en/08-train-model.md) | ACT, Diffusion Policy, SmolVLA, π₀, π₀.₅, Wall-OSS — local and cloud GPU |
| 9 | [Model inference](Tutorial/lerobot%20tutorials/en/09-inference.md) | Run a trained policy on the arm |

**Companion material**

| Document | Contents |
|---|---|
| [SO-ARM101 Robotic Arm Tutorial](Tutorial/lerobot%20tutorials/en/so-arm101-tutorial.md) | Product overview, hardware design and full specifications |
| [Kit assembly tutorial](Tutorial/lerobot%20tutorials/en/so-arm101-assembly.md) | Build the arm from 3D-printed parts and Feetech servos |
| [Basics](Tutorial/lerobot%20tutorials/en/basics.md) | Dataset format, recommended camera mounts, 3D-print files, training resources |
| [Dual-arm tutorial](Tutorial/lerobot%20tutorials/en/so-arm101-dual-arm.md) | Run two follower arms |
| [ROS2 simulation control](Tutorial/lerobot%20tutorials/en/ros2-simulation.md) | Control the arm from ROS2 |
| [STS3215 servo calibration tool](Tutorial/lerobot%20tutorials/en/servo-calibration-tool.md) | Optional servo ID and calibration utility |
| [URDF files and reference resources](Tutorial/lerobot%20tutorials/en/urdf-and-resources.md) | URDF model and related downloads |

> 🐳 **Driving the robot from a Docker image?** See the [XLeRobot Docker tutorials](Tutorial/xlerobot-docker-tutorials/en/deployment/01-Overview.md) — pull the image, generate the NVIDIA CDI spec, then run XLeRobot or a single SO-ARM101.

### Other languages

The same chapters in the other ten languages — swap the locale folder in any link above:

[简体中文](Tutorial/lerobot%20tutorials/zh-hans/index.md) · [繁體中文](Tutorial/lerobot%20tutorials/zh-hant/index.md) · [Deutsch](Tutorial/lerobot%20tutorials/de/index.md) · [Español](Tutorial/lerobot%20tutorials/es/index.md) · [Français](Tutorial/lerobot%20tutorials/fr/index.md) · [Italiano](Tutorial/lerobot%20tutorials/it/index.md) · [日本語](Tutorial/lerobot%20tutorials/ja/index.md) · [한국어](Tutorial/lerobot%20tutorials/ko/index.md) · [Português (BR)](Tutorial/lerobot%20tutorials/pt-br/index.md) · [Português (PT)](Tutorial/lerobot%20tutorials/pt-pt/index.md)

## 📖 Product documentation

### 🤖 Robot Arms

| Product | GitHub | 📖 Wiki Tutorial |
|---------|--------|-----------------|
| **SO-ARM101** 6-Axis Desktop Arm | [Original Project](https://huggingface.co/docs/lerobot/so101) | [📖 Tutorial](https://wiki.juxitech.com/tutorials/robot-arms/so-arm101/SO-ARM101-Tutorial) |
| **AmazingHand** Bionic Dexterous Hand | [GitHub](https://github.com/Juxi-Technology/AmazingHand) | [📖 Tutorial](https://wiki.juxitech.com/tutorials/robot-arms/amazing-hand/AmazingHand-Interface-Control) |
| **Lekiwi** Omnidirectional Robot | [Original Project](https://huggingface.co/docs/lerobot/lekiwi) | [📖 Tutorial](https://wiki.juxitech.com/tutorials/robot-arms/lekiwi/Lekiwi-Tutorial) |

## 🛠️ Resources

- **[Documentation](https://huggingface.co/docs/lerobot/index):** The complete guide to tutorials & API.
- **[Chinese Tutorials: LeRobot+SO-ARM101中文教程-同济子豪兄](https://zihao-ai.feishu.cn/wiki/space/7589642043471924447)** Detailed doc for assembling, teleoperate, dataset, train, deploy. Verified by Seed Studio and 5 global hackathon players.
- **[Discord](https://discord.gg/q8Dzzpym3f):** Join the `LeRobot` server to discuss with the community.
- **[X](https://x.com/LeRobotHF):** Follow us on X to stay up-to-date with the latest developments.
- **[Robot Learning Tutorial](https://huggingface.co/spaces/lerobot/robot-learning-tutorial):** A free, hands-on course to learn robot learning using LeRobot.
- **[T-Shirt Folding Experiment](https://huggingface.co/spaces/lerobot/robot-folding):** An end-to-end demonstration of folding t-shirts with LeRobot.
- **[LeLab](https://github.com/huggingface/leLab):** A web interface for LeRobot — teleoperate, calibrate, record datasets, replay, and train your SO arm from the browser, no CLI required.
