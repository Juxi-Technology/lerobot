[English](README.md) | 简体中文

# 教程

完整的 **SO-ARM101** 教程：九步走完从安装 LeRobot 到部署训练好的策略，另有组装、仿真与参考资料。每一章都提供 **11 种语言**，且文件名在所有语言下完全一致。

从[教程首页](lerobot%20tutorials/zh-hans/index.md)开始。

## 九步主线

[第一步：安装Lerobot环境](lerobot%20tutorials/zh-hans/01-install-lerobot.md) ·
[第二步：查看串口设备端口号](lerobot%20tutorials/zh-hans/02-find-serial-port.md) ·
[第三步：校准机械臂](lerobot%20tutorials/zh-hans/03-calibrate-arm.md) ·
[第四步：遥操作](lerobot%20tutorials/zh-hans/04-teleoperation.md) ·
[第五步：连接摄像头的遥操作](lerobot%20tutorials/zh-hans/05-teleoperation-with-camera.md) ·
[第六步：采集数据集-真机](lerobot%20tutorials/zh-hans/06-collect-dataset-real.md) ·
[第七步：采集数据集-光轮智能LeIsaac仿真遥操](lerobot%20tutorials/zh-hans/07-collect-dataset-leisaac-sim.md) ·
[第八步：训练模型](lerobot%20tutorials/zh-hans/08-train-model.md) ·
[第九步：模型推理](lerobot%20tutorials/zh-hans/09-inference.md)

## 配套资料

[产品概览](lerobot%20tutorials/zh-hans/so-arm101-tutorial.md) ·
[散件组装](lerobot%20tutorials/zh-hans/so-arm101-assembly.md) ·
[基础知识](lerobot%20tutorials/zh-hans/basics.md) ·
[双从臂](lerobot%20tutorials/zh-hans/so-arm101-dual-arm.md) ·
[ROS2仿真控制](lerobot%20tutorials/zh-hans/ros2-simulation.md) ·
[舵机校准工具](lerobot%20tutorials/zh-hans/servo-calibration-tool.md) ·
[URDF文件及资料参考](lerobot%20tutorials/zh-hans/urdf-and-resources.md)

## 语言

每一章都有 **11 种语言**，且**文件名完全相同**——只有正文翻译，路径不翻译。

| 语言 | 教程首页 |
|---|---|
| English | [index.md](lerobot%20tutorials/en/index.md) |
| 简体中文 | [index.md](lerobot%20tutorials/zh-hans/index.md) |
| 繁體中文 | [index.md](lerobot%20tutorials/zh-hant/index.md) |
| Deutsch | [index.md](lerobot%20tutorials/de/index.md) |
| Español | [index.md](lerobot%20tutorials/es/index.md) |
| Français | [index.md](lerobot%20tutorials/fr/index.md) |
| Italiano | [index.md](lerobot%20tutorials/it/index.md) |
| 日本語 | [index.md](lerobot%20tutorials/ja/index.md) |
| 한국어 | [index.md](lerobot%20tutorials/ko/index.md) |
| Português (BR) | [index.md](lerobot%20tutorials/pt-br/index.md) |
| Português (PT) | [index.md](lerobot%20tutorials/pt-pt/index.md) |

## 目录结构

```
Tutorial/
├── README.md                        ← 你在这里
└── lerobot tutorials/               SO-ARM101 教程 —— 11 种语言
    ├── zh-hans/
    │   ├── index.md                 ← 从这里开始
    │   ├── 01-install-lerobot.md    ……一直到 09-inference.md
    │   ├── so-arm101-tutorial.md    产品概览
    │   ├── so-arm101-assembly.md    散件组装
    │   ├── basics/ 08-train-model/ 09-inference/ ……  各章的附属页面
    │   └── images/                  所有图片/视频只存这一份，各语言共用
    └── en/ zh-hant/ de/ es/ fr/ it/ ja/ ko/ pt-br/ pt-pt/
```

> 图片和视频**只在 `lerobot tutorials/en/images/` 存一份**，其它语言都引用这里。不要再往别的语言目录里拷一份。

## 相关链接

- [仓库主页](../README.md)——LeRobot 是什么、各机械臂的文档、资源
- SO-ARM101 产品页：<https://wiki.juxitech.com/tutorials/robot-arms/so-arm101/SO-ARM101-Tutorial>
- LeRobot 文档：<https://huggingface.co/docs/lerobot>
