English | [简体中文](README_zh.md)

# Tutorials

The complete **SO-ARM101** course: nine steps from installing LeRobot to deploying a trained policy, plus assembly, simulation and reference material. Every chapter exists in **11 languages** under the same filename.

Start at the [course home](lerobot%20tutorials/en/index.md).

## The nine steps

[01 Install LeRobot](lerobot%20tutorials/en/01-install-lerobot.md) ·
[02 Find the serial port](lerobot%20tutorials/en/02-find-serial-port.md) ·
[03 Calibrate the arm](lerobot%20tutorials/en/03-calibrate-arm.md) ·
[04 Teleoperation](lerobot%20tutorials/en/04-teleoperation.md) ·
[05 Teleoperation with cameras](lerobot%20tutorials/en/05-teleoperation-with-camera.md) ·
[06 Collect a dataset — real hardware](lerobot%20tutorials/en/06-collect-dataset-real.md) ·
[07 Collect a dataset — LeIsaac simulation](lerobot%20tutorials/en/07-collect-dataset-leisaac-sim.md) ·
[08 Train a model](lerobot%20tutorials/en/08-train-model.md) ·
[09 Model inference](lerobot%20tutorials/en/09-inference.md)

## Companion documents

[Product overview](lerobot%20tutorials/en/so-arm101-tutorial.md) ·
[kit assembly](lerobot%20tutorials/en/so-arm101-assembly.md) ·
[basics](lerobot%20tutorials/en/basics.md) ·
[dual-arm](lerobot%20tutorials/en/so-arm101-dual-arm.md) ·
[ROS2 simulation control](lerobot%20tutorials/en/ros2-simulation.md) ·
[STS3215 servo calibration tool](lerobot%20tutorials/en/servo-calibration-tool.md) ·
[URDF and resources](lerobot%20tutorials/en/urdf-and-resources.md)

## Languages

Every chapter exists in all 11 languages with **identical filenames** — only the body text is translated, never the path.

| Language | Course home |
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

## Folder layout

```
Tutorial/
├── README.md                        ← you are here
└── lerobot tutorials/               SO-ARM101 course — 11 languages
    ├── en/
    │   ├── index.md                 ← start here
    │   ├── 01-install-lerobot.md    … through 09-inference.md
    │   ├── so-arm101-tutorial.md    product overview
    │   ├── so-arm101-assembly.md    kit assembly
    │   ├── basics/ 08-train-model/ 09-inference/ …   per-chapter sub-pages
    │   └── images/                  all media lives here, shared by every language
    └── zh-hans/ zh-hant/ de/ es/ fr/ it/ ja/ ko/ pt-br/ pt-pt/
```

> Media is stored **once** under `lerobot tutorials/en/images/`; every other language references it there. Do not duplicate images into other language folders.

## Related

- [Repository README](../README.md) — what LeRobot is, robot-arm documentation, and resources
- SO-ARM101 product page: <https://wiki.juxitech.com/tutorials/robot-arms/so-arm101/SO-ARM101-Tutorial>
- LeRobot documentation: <https://huggingface.co/docs/lerobot>
