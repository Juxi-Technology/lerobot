[English](../../en/05-teleoperation-with-camera/mac.md) | 简体中文 | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Mac电脑

## 连接摄像头和电脑

```Shell
lerobot-find-cameras opencv
```

![图片展示了Mac电脑连接摄像头后的检测结果。画面中列出两个 自动生成的两个摄像头信息，分别是外接的摄像头和Mac自带的前置摄像头。外接摄像头的Fps为60.00024，自带摄像头的Fps为30.0。该图片与文档中介绍Mac电脑连接摄像头和电脑的内容相关，直观呈现了连接后摄像头的检测情况，帮助用户了解摄像头的类型、ID、后端API等信息，以及各摄像头的帧率。](../../en/images/d31-01.png)

## 一个摄像头，遥操作并显示摄像头画面

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

运行后启动遥操作

会打开rerun.io画面，实时显示各个舵机关节的轨迹，以及摄像头实时画面

并保存图像至`~/用户名/outputs/captured_images`目录

![图片展示了运行后启动遥操作时打开的rerun.io画面。画面左侧是多个舵机关节轨迹的图表，以曲线形式呈现不同关节的运动情况。画面右侧实时显示了摄像头捕捉的室内场景，能看到桌子、椅子和一些物品。画面下方还有一些条状信息。这张图片与上下文紧密相关，直观呈现了运行遥操作后舵机关节轨迹及摄像头实时画面的情况，同时也体现了图像会保存至指定目录这一功能。](../../en/images/d31-02.png)

## 多个摄像头，遥操作并显示摄像头画面

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 1920, height: 1080, fps: 30, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

![图片展示了rerun.io画面，用于遥操作并显示多个摄像头画面。画面中左侧为摄像头实时画面，显示了桌面上的物品；右侧是数据图表，展示了不同关节的轨迹，如observation_wip等。画面底部有Streams区域，列出多个关节数据。右上角有数据信息，如Application ID、Source IP等。该图与文档中“多个摄像头，遥操作并显示摄像头画面”内容对应，直观呈现了遥操作时画面和数据展示情况。](../../en/images/d31-03.png)