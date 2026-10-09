[English](../../en/05-teleoperation-with-camera/windows.md) | 简体中文 | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Windows电脑

## 连接摄像头和电脑

```Shell
lerobot-find-cameras opencv
```

![这张图片是Windows系统的命令行窗口，显示了摄像头连接相关的错误信息与设备检测结果。窗口顶部有报错提示“ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range”，下方列出了检测到的摄像头信息，包括Camera #0、Camera #1的名称、类型、后端API、默认流配置、格式、源、宽高、帧率等内容，底部还有“lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0”等连接失败的报错。这段内容对应文档中提到的“摄像头连接不上，但在腾讯会议中切换摄像头，仍然能正常开启”的报错场景，是修改OpenCV后端代码前的实际运行错误反馈。](../../en/images/d32-01.png)

## 遥操作并显示摄像头画面

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

会打开rerun.io画面，实时显示各个舵机关节的轨迹，以及摄像头实时画面

并保存图像至`C:\Users\用户\outputs\captured_images`目录

![图片展示的是rerun.io画面，实时显示了各个舵机关节的轨迹及摄像头实时画面。画面左侧为蓝图界面，有“teleoperation”等选项。中间是轨迹图，显示了“observation_wrist_rot.pos”等关节位置数据。右侧是摄像头画面，呈现了机器人视角下的场景。画面右上角显示“Waiting for data on rerun: http://127.0.0.1:9876/remote...”，下方有数据源信息。该图与文档中介绍rerun.io画面实时显示摄像头画面的内容相关，直观呈现了画面效果。](../../en/images/d32-02.png)

## 如果遇到了下面这种报错

摄像头连接不上，但在腾讯会议中切换摄像头，仍然能正常开启

![图片展示的是Windows电脑命令行界面，显示了摄像头检测结果。界面上方显示“Detected Cameras”及摄像头相关信息，如名称、类型、ID、后端API等。下方有错误提示，指出在运行lerobot_find_cameras_openpyc时，OpenCV摄像头连接或配置失败，提示运行lerobot_find_cameras_opencv以查找可用摄像头，且无摄像头可连接，将中止图像保存。该图片与文档中遇到摄像头连接不上问题的上下文对应，直观呈现了报错情况。](../../en/images/d32-03.png)

修改`lerobot\src\lerobot\cameras\utils.py`文件，将OpenCV后端改为`cv2.CAP_SHOW`

![图片展示的是`lerobot\\src\\lerobot\\cameras\\utils.py`文件中`get_cv2_backend()`函数代码。当系统为Windows时，函数返回`int(cv2.CAP_DSHOW)`，用于在Windows上使用MSMF代替AVFOUNDATION。代码中还有对`cv2.CAP_MSMF`的注释，以及对Darwin（macOS）和Linux等其他系统的处理方式。该图片与文档中修改`lerobot\\src\\lerobot\\cameras\\utils.py`文件，将OpenCV后端改为`cv2.CAP_SHOW`的操作相关，是修改代码示例。](../../en/images/d32-04.png)

> 这是一个豆包都无法解决的bug，都怪lerobot库封装的太深了，初学者小白很难dubug

<figure view-type="Preview">[附件 / Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## 连接多个摄像头，遥操作并显示摄像头画面

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![图片展示了rerun.io画面，用于遥操作并显示摄像头画面。画面左侧是轨迹图，显示了多个关节的轨迹数据，如observation_wrist_l_pos、observation_wrist_r_pos等。右侧上方是摄像头实时画面，下方是腾讯会议画面。画面右上角显示“Waiting for data on rerun: http://127.0.0.1:9678/remote...”。该图与文档中连接多个摄像头，遥操作并显示摄像头画面的内容相关，直观呈现了画面效果。](../../en/images/d32-05.png)