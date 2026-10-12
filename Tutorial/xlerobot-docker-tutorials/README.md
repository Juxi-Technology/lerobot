# XLeRobot Docker 教程 / XLeRobot Docker Tutorials

XLeRobot Docker 使用教程，**11 种语言**。
Available in **11 languages**.

---

## 语言 / Languages

| 语言 | Language | 目录 |
|---|---|---|
| 简体中文 | Simplified Chinese | [zh-hans/](zh-hans/) |
| English | English | [en/](en/) |
| 繁體中文 | Traditional Chinese | [zh-hant/](zh-hant/) |
| 日本語 | Japanese | [ja/](ja/) |
| 한국어 | Korean | [ko/](ko/) |
| Deutsch | German | [de/](de/) |
| Français | French | [fr/](fr/) |
| Español | Spanish | [es/](es/) |
| Italiano | Italian | [it/](it/) |
| Português (Brasil) | Portuguese (Brazil) | [pt-br/](pt-br/) |
| Português (Portugal) | Portuguese (Portugal) | [pt-pt/](pt-pt/) |

---

## 目录结构 / Structure

**每个主题一个独立文件夹。** 所有语言的文件夹名和文件名**完全一致**——所以
`ja/xlerobot/01-Operation.md` 和 `zh-hans/xlerobot/01-Operation.md`
是同一篇的不同语言版本。

One folder per topic. Folder and file names are identical in every language.

| # | 文件夹 | 内容 | Folder |
|:---:|---|---|---|
| 1 | `deployment/` | **拉取镜像、运行镜像** | Deployment |
| 2 | `xlerobot/` | **XLeRobot 整机运行指令** | XLeRobot operation |
| 3 | `lerobot/` | **原版 LeRobot 运行指令** | Original LeRobot operation |
| 4 | `troubleshooting/` | 常见问题与速查 | Troubleshooting |

> ⚠️ **`xlerobot/` 和 `lerobot/` 是二选一**——看你的硬件：
> 整机（双臂 + 底盘）进 `xlerobot/`；单条 SO-101 / SO-100 臂或 LeKiwi 进 `lerobot/`。
>
> `xlerobot/` and `lerobot/` are **alternatives**: whole robot → `xlerobot/`,
> single SO-101/SO-100 arm or LeKiwi → `lerobot/`.

### `deployment/` 里按顺序读三篇 / Read these three in order

| # | 文件 | 简体中文标题 | English title |
|:---:|---|---|---|
| 1 | `01-Overview.md` | 总览 | Overview |
| 2 | `02-Environment-Setup.md` | 环境准备 | Environment Setup |
| 3 | `03-Deployment.md` | 部署 | Deployment |

另外三个文件夹各只有一篇：`xlerobot/01-Operation.md`、
`lerobot/01-Operation.md`、`troubleshooting/01-Troubleshooting.md`。

别跳 `deployment/02`（镜像加速）——那是最常卡住的地方。

Don't skip the mirror accelerator in `deployment/02` — that's where people get stuck.

---

## 命名约定 / Naming convention

沿用 [wiki.juxitech.com](https://wiki.juxitech.com) 的约定：

- **文件名用英文 slug + 数字前缀**（`NN-Kebab-Case.md`），
  在所有语言下**保持一致**——只有正文翻译，路径不翻译
- 语言目录用标准 locale 代码（`zh-hans`、`pt-br`……）
- 每篇开头有「上一篇 / 下一篇」导航，末尾指向下一篇

Follows the [wiki.juxitech.com](https://wiki.juxitech.com) convention:

- **English slug + numeric prefix** (`NN-Kebab-Case.md`), identical across all
  languages — only the body text is translated, never the path
- Language directories use standard locale codes
- Each page has prev/next navigation

---

## 其它文档 / Other docs

- 上级目录索引 / Index for the parent folder：[../README.md](../README.md)
- SO-ARM101 九步教程 / Nine-step SO-ARM101 course：
  [简体中文](../lerobot%20tutorials/zh-hans/index.md) ·
  [English](../lerobot%20tutorials/en/index.md)
- 仓库主页 / Repository README：[../../README.md](../../README.md)
