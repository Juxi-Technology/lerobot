English | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Mac Computer

## Connect the Camera to the Computer

```Shell
lerobot-find-cameras opencv
```

![The image shows the detection result after connecting a camera to a Mac. It lists the two automatically generated cameras, the external camera and the Mac's built-in front camera. The external camera's Fps is 60.00024 and the built-in camera's Fps is 30.0. This image relates to the content on connecting a camera to a Mac, visually presenting the detection result after connection and helping users understand each camera's type, ID, backend API and frame rate.](../../en/images/d31-01.png)

## One Camera, Teleoperation with the Camera Feed Displayed

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

After running, teleoperation starts

The rerun.io window opens, showing the trajectory of each servo joint in real time, along with the live camera feed

and saves the images to the `~/username/outputs/captured_images` directory

![The image shows the rerun.io window opened when teleoperation starts after running. On the left are charts of the trajectories of several servo joints, presented as curves showing the motion of different joints. On the right, the camera feed of the indoor scene is shown in real time, where a table, chairs and some objects can be seen. There is also some bar-shaped information at the bottom. This image is closely related to the context, visually presenting the servo joint trajectories and the live camera feed during teleoperation, and it also illustrates that images are saved to the specified directory.](../../en/images/d31-02.png)

## Multiple Cameras, Teleoperation with the Camera Feeds Displayed

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

![The image shows the rerun.io window used for teleoperation with multiple camera feeds. On the left is the live camera feed, showing objects on a desk; on the right are data charts showing the trajectories of different joints, such as observation_wip. At the bottom is a Streams area listing data for several joints. In the top right there is data information such as Application ID and Source IP. This image corresponds to the "Multiple cameras, teleoperation with camera feeds" content, visually presenting the feeds and data during teleoperation.](../../en/images/d31-03.png)