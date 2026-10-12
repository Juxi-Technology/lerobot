[English](README.md) | 简体中文

<p align="center">
  <img alt="LeRobot, Hugging Face Robotics Library" src="./media/readme/lerobot-logo-thumbnail.png" width="100%">
</p>

**LeRobot** 致力于为真实机器人提供 PyTorch 模型、数据集与工具，目标是降低入门门槛，让每个人都能贡献并受益于共享数据集与预训练模型。

🤗 与硬件无关的 Python 原生接口，统一了从低成本机械臂（SO-100）到人形机器人的各类平台控制方式。

🤗 标准化的、可扩展的 LeRobotDataset 数据格式（Parquet + MP4 或图像），托管于 Hugging Face Hub，支持大规模机器人数据集的高效存储、流式读取与可视化。

🤗 业界领先的策略模型，已验证可迁移到真实世界，可直接用于训练与部署。

🤗 全面支持开源生态，推动物理 AI 的大众化。

## 📚 教程

本仓库自带一套完整的 **SO-ARM101** 教程：**九步**走完从安装 LeRobot 到部署训练好的策略，另有组装、仿真与参考资料。每一章都提供 **11 种语言**，且文件名在所有语言下完全一致。

> 📁 **[Tutorial/README_zh.md](Tutorial/README_zh.md)** 是 `Tutorial/` 目录的总索引——两套教程、11 种语言都在这里。

| # | 章节 | 内容 |
|:--:|---|---|
| ★ | [**教程首页**](Tutorial/lerobot%20tutorials/zh-hans/index.md) | 什么是具身智能、LeRobot、SO-ARM101；需要什么配置的电脑 |
| 1 | [第一步：安装Lerobot环境](Tutorial/lerobot%20tutorials/zh-hans/01-install-lerobot.md) | Windows / macOS / Ubuntu 三种系统的安装方式 |
| 2 | [第二步：查看串口设备端口号](Tutorial/lerobot%20tutorials/zh-hans/02-find-serial-port.md) | 通过 USB 与机械臂通信 |
| 3 | [第三步：校准机械臂](Tutorial/lerobot%20tutorials/zh-hans/03-calibrate-arm.md) | 主臂与从臂的一次性校准 |
| 4 | [第四步：遥操作](Tutorial/lerobot%20tutorials/zh-hans/04-teleoperation.md) | 手动拖动主臂，带动从臂运动 |
| 5 | [第五步：连接摄像头的遥操作](Tutorial/lerobot%20tutorials/zh-hans/05-teleoperation-with-camera.md) | 接入腕部相机与顶部相机 |
| 6 | [第六步：采集数据集-真机](Tutorial/lerobot%20tutorials/zh-hans/06-collect-dataset-real.md) | 录制、回放并上传示教数据 |
| 7 | [第七步：采集数据集-光轮智能LeIsaac仿真遥操](Tutorial/lerobot%20tutorials/zh-hans/07-collect-dataset-leisaac-sim.md) | 没有实机也能采数据 |
| 8 | [第八步：训练模型](Tutorial/lerobot%20tutorials/zh-hans/08-train-model.md) | ACT、Diffusion Policy、SmolVLA、π₀、π₀.₅、Wall-OSS，支持本地与云端 GPU |
| 9 | [第九步：模型推理](Tutorial/lerobot%20tutorials/zh-hans/09-inference.md) | 在机械臂上运行训练好的策略 |

**配套资料**

| 文档 | 内容 |
|---|---|
| [SO-ARM101机械臂教程](Tutorial/lerobot%20tutorials/zh-hans/so-arm101-tutorial.md) | 产品概览、硬件设计与完整规格参数 |
| [SO-ARM101机械臂散件组装教程](Tutorial/lerobot%20tutorials/zh-hans/so-arm101-assembly.md) | 用 3D 打印件与飞特舵机装出整条机械臂 |
| [基础知识](Tutorial/lerobot%20tutorials/zh-hans/basics.md) | 数据集格式、推荐相机支架、3D 打印文件、训练资源 |
| [SO-ARM101双从臂教程](Tutorial/lerobot%20tutorials/zh-hans/so-arm101-dual-arm.md) | 同时驱动两条从臂 |
| [ROS2仿真控制](Tutorial/lerobot%20tutorials/zh-hans/ros2-simulation.md) | 从 ROS2 控制机械臂 |
| [舵机校准工具](Tutorial/lerobot%20tutorials/zh-hans/servo-calibration-tool.md) | So-ARM 系列 STS3215 舵机 ID 与校准工具，可跳过 |
| [URDF文件及资料参考](Tutorial/lerobot%20tutorials/zh-hans/urdf-and-resources.md) | URDF 模型与相关下载 |

### 其它语言

同样的章节，另外 10 种语言——把上面任一链接中的语言目录替换即可：

[English](Tutorial/lerobot%20tutorials/en/index.md) · [繁體中文](Tutorial/lerobot%20tutorials/zh-hant/index.md) · [Deutsch](Tutorial/lerobot%20tutorials/de/index.md) · [Español](Tutorial/lerobot%20tutorials/es/index.md) · [Français](Tutorial/lerobot%20tutorials/fr/index.md) · [Italiano](Tutorial/lerobot%20tutorials/it/index.md) · [日本語](Tutorial/lerobot%20tutorials/ja/index.md) · [한국어](Tutorial/lerobot%20tutorials/ko/index.md) · [Português (BR)](Tutorial/lerobot%20tutorials/pt-br/index.md) · [Português (PT)](Tutorial/lerobot%20tutorials/pt-pt/index.md)

## 📖 产品文档

### 🤖 机械臂

| 产品 | GitHub | 📖 Wiki 教程 |
|------|--------|-------------|
| **SO-ARM101** 6 轴桌面机械臂 | [原项目](https://huggingface.co/docs/lerobot/so101) | [📖 教程](https://wiki.juxitech.com/tutorials/robot-arms/so-arm101/SO-ARM101-Tutorial) |
| **AmazingHand** 仿生灵巧手 | [GitHub](https://github.com/Juxi-Technology/AmazingHand) | [📖 教程](https://wiki.juxitech.com/tutorials/robot-arms/amazing-hand/AmazingHand-Interface-Control) |
| **Lekiwi** 全向移动机器人 | [原项目](https://huggingface.co/docs/lerobot/lekiwi) | [📖 教程](https://wiki.juxitech.com/tutorials/robot-arms/lekiwi/Lekiwi-Tutorial) |

## 🛠️ 资源

- **[官方文档](https://huggingface.co/docs/lerobot/index)：** 完整的教程与 API 指南。
- **[中文教程：LeRobot+SO-ARM101中文教程-同济子豪兄](https://zihao-ai.feishu.cn/wiki/space/7589642043471924447)** 涵盖组装、遥操作、数据集、训练与部署的详细文档。已由 Seeed Studio 及 5 位全球黑客松选手验证。
- **[Discord](https://discord.gg/q8Dzzpym3f)：** 加入 `LeRobot` 服务器，与社区交流讨论。
- **[X](https://x.com/LeRobotHF)：** 关注我们的 X 账号，了解最新进展。
- **[机器人学习教程](https://huggingface.co/spaces/lerobot/robot-learning-tutorial)：** 免费的实操课程，学习如何使用 LeRobot 做机器人学习。
- **[折叠 T 恤实验](https://huggingface.co/spaces/lerobot/robot-folding)：** 用 LeRobot 折叠 T 恤的端到端演示。
- **[LeLab](https://github.com/huggingface/leLab)：** LeRobot 的 Web 界面——无需命令行，在浏览器中即可完成遥操作、标定、数据集录制、回放与 SO 机械臂训练。
