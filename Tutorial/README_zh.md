[English](README.md) | 简体中文

# 教程

这个目录下有两套互相独立的教程，解决的问题不同——按你的硬件选。

| 教程 | 目录 | 适用 | 语言 |
|---|---|---|---|
| **SO-ARM101 教程** | [`lerobot tutorials/`](lerobot%20tutorials/zh-hans/index.md) | 单条 SO-ARM101 机械臂（12 个舵机），在笔记本或台式机上跑 | 11 种 |
| **XLeRobot Docker** | [`xlerobot-docker-tutorials/`](xlerobot-docker-tutorials/README.md) | 一块 Jetson 板子，跑现成的 Docker 镜像 | 11 种 |

两套都用 LeRobot，区别在于**环境由谁装**：

- **SO-ARM101 教程**是从零开始的路径——你自己装 LeRobot，然后校准、采数据、训练、部署。
- **XLeRobot Docker**跳过安装——环境和机器人代码已经打包进镜像里了。

---

## 1. SO-ARM101 教程 —— [`lerobot tutorials/`](lerobot%20tutorials/zh-hans/index.md)

九步走完，从安装 LeRobot 到在机械臂上运行训练好的策略：

[第一步：安装Lerobot环境](lerobot%20tutorials/zh-hans/01-install-lerobot.md) ·
[第二步：查看串口设备端口号](lerobot%20tutorials/zh-hans/02-find-serial-port.md) ·
[第三步：校准机械臂](lerobot%20tutorials/zh-hans/03-calibrate-arm.md) ·
[第四步：遥操作](lerobot%20tutorials/zh-hans/04-teleoperation.md) ·
[第五步：连接摄像头的遥操作](lerobot%20tutorials/zh-hans/05-teleoperation-with-camera.md) ·
[第六步：采集数据集-真机](lerobot%20tutorials/zh-hans/06-collect-dataset-real.md) ·
[第七步：采集数据集-光轮智能LeIsaac仿真遥操](lerobot%20tutorials/zh-hans/07-collect-dataset-leisaac-sim.md) ·
[第八步：训练模型](lerobot%20tutorials/zh-hans/08-train-model.md) ·
[第九步：模型推理](lerobot%20tutorials/zh-hans/09-inference.md)

配套资料：[产品概览](lerobot%20tutorials/zh-hans/so-arm101-tutorial.md) ·
[散件组装](lerobot%20tutorials/zh-hans/so-arm101-assembly.md) ·
[基础知识](lerobot%20tutorials/zh-hans/basics.md) ·
[双从臂](lerobot%20tutorials/zh-hans/so-arm101-dual-arm.md) ·
[ROS2仿真控制](lerobot%20tutorials/zh-hans/ros2-simulation.md) ·
[舵机校准工具](lerobot%20tutorials/zh-hans/servo-calibration-tool.md) ·
[URDF文件及资料参考](lerobot%20tutorials/zh-hans/urdf-and-resources.md)

## 2. XLeRobot Docker —— [`xlerobot-docker-tutorials/`](xlerobot-docker-tutorials/README.md)

全部在现成的镜像里运行，面向 **NVIDIA Jetson** 板子 + **JetPack 7.2**——你不需要自己装 LeRobot，也不用装机器人代码。

四个文件夹按这个顺序读：

| # | 文件夹 | 内容 |
|:--:|---|---|
| 1 | [`deployment/`](xlerobot-docker-tutorials/zh-hans/deployment/01-Overview.md) | 拉取镜像、启动容器——按 `01-Overview` → `02-Environment-Setup` → `03-Deployment` 顺序读 |
| 2 | [`xlerobot/`](xlerobot-docker-tutorials/zh-hans/xlerobot/01-Operation.md) | XLeRobot 整机运行指令（双臂 + 底盘，17 个舵机） |
| 3 | [`lerobot/`](xlerobot-docker-tutorials/zh-hans/lerobot/01-Operation.md) | 单条 SO-101 / SO-100 臂（12 个舵机）或 LeKiwi 的运行指令 |
| 4 | [`troubleshooting/`](xlerobot-docker-tutorials/zh-hans/troubleshooting/01-Troubleshooting.md) | 常见问题与速查 |

> 第 2 个和第 3 个文件夹是**二选一**——看你的硬件走哪条。两条路用的是同一套环境，随时能切，不用重装任何东西。

## 语言

每一章都有 **11 种语言**，且**文件名完全相同**——只有正文翻译，路径不翻译。

| 语言 | SO-ARM101 教程 | XLeRobot Docker |
|---|---|---|
| English | [index.md](lerobot%20tutorials/en/index.md) | [01-Overview.md](xlerobot-docker-tutorials/en/deployment/01-Overview.md) |
| 简体中文 | [index.md](lerobot%20tutorials/zh-hans/index.md) | [01-Overview.md](xlerobot-docker-tutorials/zh-hans/deployment/01-Overview.md) |
| 繁體中文 | [index.md](lerobot%20tutorials/zh-hant/index.md) | [01-Overview.md](xlerobot-docker-tutorials/zh-hant/deployment/01-Overview.md) |
| Deutsch | [index.md](lerobot%20tutorials/de/index.md) | [01-Overview.md](xlerobot-docker-tutorials/de/deployment/01-Overview.md) |
| Español | [index.md](lerobot%20tutorials/es/index.md) | [01-Overview.md](xlerobot-docker-tutorials/es/deployment/01-Overview.md) |
| Français | [index.md](lerobot%20tutorials/fr/index.md) | [01-Overview.md](xlerobot-docker-tutorials/fr/deployment/01-Overview.md) |
| Italiano | [index.md](lerobot%20tutorials/it/index.md) | [01-Overview.md](xlerobot-docker-tutorials/it/deployment/01-Overview.md) |
| 日本語 | [index.md](lerobot%20tutorials/ja/index.md) | [01-Overview.md](xlerobot-docker-tutorials/ja/deployment/01-Overview.md) |
| 한국어 | [index.md](lerobot%20tutorials/ko/index.md) | [01-Overview.md](xlerobot-docker-tutorials/ko/deployment/01-Overview.md) |
| Português (BR) | [index.md](lerobot%20tutorials/pt-br/index.md) | [01-Overview.md](xlerobot-docker-tutorials/pt-br/deployment/01-Overview.md) |
| Português (PT) | [index.md](lerobot%20tutorials/pt-pt/index.md) | [01-Overview.md](xlerobot-docker-tutorials/pt-pt/deployment/01-Overview.md) |

## 目录结构

```
Tutorial/
├── README.md                        ← 你在这里
├── lerobot tutorials/               SO-ARM101 教程 —— 11 种语言
│   ├── zh-hans/
│   │   ├── index.md                 ← 从这里开始
│   │   ├── 01-install-lerobot.md    ……一直到 09-inference.md
│   │   ├── so-arm101-tutorial.md    产品概览
│   │   ├── so-arm101-assembly.md    散件组装
│   │   ├── basics/ 08-train-model/ 09-inference/ ……  各章的附属页面
│   │   └── images/                  所有图片/视频只存这一份，各语言共用
│   └── en/ zh-hant/ de/ es/ fr/ it/ ja/ ko/ pt-br/ pt-pt/
└── xlerobot-docker-tutorials/       XLeRobot Docker —— 11 种语言
    ├── README.md                    本套教程的语言索引
    ├── zh-hans/
    │   ├── deployment/              01-Overview · 02-Environment-Setup · 03-Deployment
    │   ├── xlerobot/                01-Operation
    │   ├── lerobot/                 01-Operation
    │   └── troubleshooting/         01-Troubleshooting
    └── en/ zh-hant/ de/ es/ fr/ it/ ja/ ko/ pt-br/ pt-pt/
```

> 图片和视频**只在 `lerobot tutorials/en/images/` 存一份**，其它语言都引用这里。不要再往别的语言目录里拷一份。

## 相关链接

- [仓库主页](../README.md)——LeRobot 是什么、各机械臂的文档、资源
- SO-ARM101 产品页：<https://wiki.juxitech.com/tutorials/robot-arms/so-arm101/SO-ARM101-Tutorial>
- XLeRobot 项目：<https://github.com/Vector-Wangel/XLeRobot>
- LeRobot 文档：<https://huggingface.co/docs/lerobot>
