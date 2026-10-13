English | [简体中文](README_zh.md)

# Tutorials

Three independent tutorial sets live in this folder. Pick by your hardware, or by whether you want a browser interface.

| Set | Folder | For | Languages |
|---|---|---|---|
| **SO-ARM101 course** | [`lerobot tutorials/`](lerobot%20tutorials/en/index.md) | A single SO-ARM101 arm (12 servos), on a laptop or desktop | 11 |
| **XLeRobot Docker** | [`xlerobot-docker-tutorials/`](xlerobot-docker-tutorials/README.md) | A Jetson board running the prebuilt Docker image | 11 |
| **leLab** | [`lelab/`](lelab/README.md) | The same SO-101 workflow, driven from a browser instead of the command line | 2 |

All three use LeRobot. What differs is how much they set up for you:

- The **SO-ARM101 course** is the from-scratch path — install LeRobot yourself, then calibrate, collect data, train and deploy from the command line.
- The **XLeRobot Docker** set skips installation — the environment and the robot code are already inside the image.
- **leLab** replaces the command line with a web UI: calibrate, teleoperate, record, train and run inference by clicking. It installs LeRobot as a dependency.

---

## 1. SO-ARM101 course — [`lerobot tutorials/`](lerobot%20tutorials/en/index.md)

Nine steps, from installing LeRobot to running a trained policy on the arm:

[01 Install LeRobot](lerobot%20tutorials/en/01-install-lerobot.md) ·
[02 Find the serial port](lerobot%20tutorials/en/02-find-serial-port.md) ·
[03 Calibrate the arm](lerobot%20tutorials/en/03-calibrate-arm.md) ·
[04 Teleoperation](lerobot%20tutorials/en/04-teleoperation.md) ·
[05 Teleoperation with cameras](lerobot%20tutorials/en/05-teleoperation-with-camera.md) ·
[06 Collect a dataset — real hardware](lerobot%20tutorials/en/06-collect-dataset-real.md) ·
[07 Collect a dataset — LeIsaac simulation](lerobot%20tutorials/en/07-collect-dataset-leisaac-sim.md) ·
[08 Train a model](lerobot%20tutorials/en/08-train-model.md) ·
[09 Model inference](lerobot%20tutorials/en/09-inference.md)

Companion documents: [product overview](lerobot%20tutorials/en/so-arm101-tutorial.md) ·
[kit assembly](lerobot%20tutorials/en/so-arm101-assembly.md) ·
[basics](lerobot%20tutorials/en/basics.md) ·
[dual-arm](lerobot%20tutorials/en/so-arm101-dual-arm.md) ·
[ROS2 simulation control](lerobot%20tutorials/en/ros2-simulation.md) ·
[STS3215 servo calibration tool](lerobot%20tutorials/en/servo-calibration-tool.md) ·
[URDF and resources](lerobot%20tutorials/en/urdf-and-resources.md)

## 2. XLeRobot Docker — [`xlerobot-docker-tutorials/`](xlerobot-docker-tutorials/README.md)

Everything runs inside a prebuilt image on an **NVIDIA Jetson** board with **JetPack 7.2** — you do not install LeRobot or the robot code yourself.

Read the four folders in this order:

| # | Folder | Contents |
|:--:|---|---|
| 1 | [`deployment/`](xlerobot-docker-tutorials/en/deployment/01-Overview.md) | Pull the image and start the container — read `01-Overview` → `02-Environment-Setup` → `03-Deployment` in order |
| 2 | [`xlerobot/`](xlerobot-docker-tutorials/en/xlerobot/01-Operation.md) | Operation commands for a whole XLeRobot (two arms + base, 17 servos) |
| 3 | [`lerobot/`](xlerobot-docker-tutorials/en/lerobot/01-Operation.md) | Operation commands for a single SO-101 / SO-100 arm (12 servos) or a LeKiwi |
| 4 | [`troubleshooting/`](xlerobot-docker-tutorials/en/troubleshooting/01-Troubleshooting.md) | Common problems and a quick-reference cheat sheet |

> Folders 2 and 3 are **alternatives** — pick the one that matches your hardware. It is the same environment either way, so you can switch at any time without reinstalling anything.

## 3. leLab — [`lelab/`](lelab/README.md)

The SO-101 workflow in a browser, instead of the `lerobot-*` command line. Seven pages:

[01 Overview](lelab/en/01-overview.md) ·
[02 Install and run](lelab/en/02-install.md) ·
[03 Connect and calibrate](lelab/en/03-calibration.md) ·
[04 Teleoperation](lelab/en/04-teleoperation.md) ·
[05 Record a dataset](lelab/en/05-record-dataset.md) ·
[06 Train and run inference](lelab/en/06-train-and-inference.md) ·
[07 Troubleshooting](lelab/en/07-troubleshooting.md)

Install with:

```bash
uv tool install --with-executables-from huggingface_hub git+https://github.com/Juxi-Technology/leLab.git && lelab
```

## Languages

Every chapter of the SO-ARM101 course and the XLeRobot Docker set exists in all 11 languages with **identical filenames** — only the body text is translated, never the path.

| Language | SO-ARM101 course | XLeRobot Docker |
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

**leLab** exists in English and Simplified Chinese so far: [en](lelab/en/01-overview.md) · [zh-hans](lelab/zh-hans/01-overview.md).

## Folder layout

```
Tutorial/
├── README.md                        ← you are here
├── lerobot tutorials/               SO-ARM101 course — 11 languages
│   ├── en/
│   │   ├── index.md                 ← start here
│   │   ├── 01-install-lerobot.md    … through 09-inference.md
│   │   ├── so-arm101-tutorial.md    product overview
│   │   ├── so-arm101-assembly.md    kit assembly
│   │   ├── basics/ 08-train-model/ 09-inference/ …   per-chapter sub-pages
│   │   └── images/                  all media lives here, shared by every language
│   └── zh-hans/ zh-hant/ de/ es/ fr/ it/ ja/ ko/ pt-br/ pt-pt/
├── xlerobot-docker-tutorials/       XLeRobot Docker — 11 languages
│   ├── README.md                    language index for this set
│   ├── en/
│   │   ├── deployment/              01-Overview · 02-Environment-Setup · 03-Deployment
│   │   ├── xlerobot/                01-Operation
│   │   ├── lerobot/                 01-Operation
│   │   └── troubleshooting/         01-Troubleshooting
│   └── zh-hans/ zh-hant/ de/ es/ fr/ it/ ja/ ko/ pt-br/ pt-pt/
└── lelab/                           leLab — English + Simplified Chinese
    ├── README.md  README_zh.md      index, one per language
    └── en/ zh-hans/                 01-overview … 07-troubleshooting
```

> Media is stored **once** under `lerobot tutorials/en/images/`; every other language references it there. Do not duplicate images into other language folders.

## Related

- [Repository README](../README.md) — what LeRobot is, robot-arm documentation, and resources
- leLab repository: <https://github.com/Juxi-Technology/leLab>
- SO-ARM101 product page: <https://wiki.juxitech.com/tutorials/robot-arms/so-arm101/SO-ARM101-Tutorial>
- XLeRobot project: <https://github.com/Vector-Wangel/XLeRobot>
- LeRobot documentation: <https://huggingface.co/docs/lerobot>
