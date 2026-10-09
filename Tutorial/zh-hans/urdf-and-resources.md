[English](../en/urdf-and-resources.md) | 简体中文 | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | [Español](../es/urdf-and-resources.md) | [Français](../fr/urdf-and-resources.md) | [Italiano](../it/urdf-and-resources.md) | [日本語](../ja/urdf-and-resources.md) | [한국어](../ko/urdf-and-resources.md) | [Português (BR)](../pt-br/urdf-and-resources.md) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>URDF文件及资料参考</title>

# Lerbot官方的[URDF文件](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf)



## URDF Studio

https://urdf.d-robotics.cc/



## ROS2 仿真控制（可自行实现）

https://github.com/holmsslk/so-arm-moveit-hardware



## LeRobot的官方图形界面

https://github.com/huggingface/leLab

LeLab是一款网页应用，它将 LeRobot 的全部工作流程——校准、远程操控、记录、训练、回放——整合到一个浏览器界面中。只需连接机械臂，打开应用，即可开始操作。无需繁琐的命令行操作，也无需键盘输入。

🤗 LeRobot 的原生网页入口，旨在让新用户在几分钟内完成从“开箱”到“训练他们的第一个保单”的整个过程。

🤗 只需一条命令即可安装并运行所有程序。



# 手机控制从动臂

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## 云端机器人研发：基于 AWS 实现 ROS 2 设备与 Isaac Sim 的 Lerobot 仿真及数据流

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## 网页端设置舵机ID和中位校准

https://bambot.org/feetech.js?lang=zh

1、根据舵机型号输入0或1，点击“连接”

![图片展示的是网页端设置舵机ID和中位校准时的连接界面。界面中有“连接”部分，包含波特率选择框，当前选中“1,000,000 bps (Index 0)”；协议端选择框，当前选中“0=STS/SMS”；以及“连接”按钮。界面底部显示“状态：已断开”。该图片与上下文紧密相关，是根据舵机型号输入0或1，点击“连接”后扫描ID 1~6的舵机，确认对应ID舵机操作流程中的关键展示界面。](../en/images/d68-01.png)

2、扫描ID 1\~6 的舵机，可以根据扫描结果里的FOUND确认对应ID舵机。例如图片里舵机 ID 1 被扫描到了

![图片展示的是Lerbot官方URDF Studio中扫描舵机界面。界面显示起始ID为1，结束ID为6，下方有“开始扫描”按钮。扫描结果部分，扫描ID1时，扫描到ID1239，其余扫描ID2至ID6均提示“ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!，Error code: 0”。该图片与上下文介绍的Lerbot官方URDF Studio中扫描舵机操作相关，直观呈现了扫描过程及结果。](../en/images/fix-01.png)

3、ID设置和中位校准

①当前舵机ID输入为被扫描到的舵机ID

②在“ID管理”中输入数字，点击“更改ID”即可设置ID

③中位校准（STS3215舵机中位是2047，SCS0009舵机中位是511）

STS舵机：在“位置控制”输入2047，并点击“Set”

SCS舵机：在“位置控制”输入511，并点击“Set”

![图片展示了Lerbot单个舵机控制界面。界面中“当前舵机ID”显示为1，下方“ID管理”处有数字1和“更改ID”按钮，下方提示“Success: ID changed to 1”。位置控制区域有“读取位置”按钮，显示位置为2047，旁边有“Set”按钮。该图片与文档中“ID设置和中位校准”部分内容相关，直观呈现了设置舵机ID及中位校准的操作界面，帮助用户了解如何在Lerbot中进行相关设置。](../en/images/d68-02.png)