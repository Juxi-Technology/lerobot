[English](../../en/09-inference/common-bugs.md) | 简体中文 | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# 常见Bug及解决

## 摄像头获取失败

![图片展示的是Lerobot机器人相关代码运行时的终端输出信息。其中，`INFO`日志显示了OpenCV摄像头打开、Follower断连等信息；`ERROR`日志则指出在`camera_opencv.py`文件中，`read`函数因`OpenCVCamera(0) read failed`而引发`RuntimeError`。该图片与文档中“摄像头获取失败”问题相关，直观呈现了代码运行时出现的问题，辅助理解摄像头获取失败的具体原因。](../../en/images/d65-01.png)

检查一下腕部摄像头的接线是否松动，特别是靠近摄像头那端的接线，非常容易接触不良

## 摄像头断连

![图片展示的是L /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py 代码运行界面。界面上方显示了时间、进程ID等信息，下方是 /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py 等代码路径及报错信息，如“INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.”等。关键部分是“raise TimeoutError”及“TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.”，表明摄像头获取失败。该图片与文档中“摄像头获取失败”问题相关，直观呈现了报错情况。](../../en/images/d65-02.png)

重新启动一下命令行

## 舵机通信问题1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![图片展示的是](../../en/images/d65-03.png)

解决方案，把`lerobot/src/lerobot/motors/motors_bus.py`代码中所有`num_retry`都改成99，特别是报错行对应的

![图片展示的是LeroBot项目中`motors_bus.py`代码文件内容。文件中`MotorsBusABC`类的`write`方法被高亮显示，其中`num_retry`变量被修改为`99`。该图片与文档中“舵机通信问题1”部分相关，对应解决方案中提到的把`lerobot/src/lerobot/motors/motors_bus.py`代码中所有`num_retry`都改成99的操作，特别是报错行对应的代码部分。](../../en/images/d65-04.png)

## 舵机通信问题2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![图片展示的是在macOS系统下，使用zsh终端执行命令行操作的界面。终端中显示了多个文件路径及代码行号，如`/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`等。其中，`/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py`文件的第587行代码引发`ConnectionError`，提示在id=1上写入`Torque_Enable`失败，且无状态包。该图片与文档中“舵机通信问题2”内容相关，直观呈现了报错时的代码执行情况。](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![图片展示的是在macOS系统下，使用zsh终端执行命令行操作的界面。终端显示了多个文件路径及代码行号，如`/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`等。其中，`/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot 自动生成](../../en/images/d65-06.png)
</column>
</grid>

解决方法：重新校准机械臂