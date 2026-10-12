English | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Windows Computer

## Connect the Camera to the Computer

```Shell
lerobot-find-cameras opencv
```

![This image is the Windows command line window, showing camera connection errors and device detection results. At the top there is an error: "ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range". Below it lists the detected cameras, including Camera #0 and Camera #1, with their name, type, backend API, default stream configuration, format, source, width, height and frame rate; at the bottom there are errors such as "lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0". This corresponds to the error scenario mentioned in the document, "the camera cannot connect, but switching cameras in Tencent Meeting still opens normally", and is the actual runtime error feedback before modifying the OpenCV backend code.](../../en/images/d32-01.png)

## Teleoperation with the Camera Feed Displayed

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

The rerun.io window opens, showing the trajectory of each servo joint in real time, along with the live camera feed

and saves the images to the `C:\Users\username\outputs\captured_images` directory

![The image shows the rerun.io window, displaying the trajectories of the servo joints and the live camera feed in real time. On the left is the blueprint interface with options such as "teleoperation". In the middle is the trajectory chart, showing joint position data such as "observation_wrist_rot.pos". On the right is the camera feed, showing the scene from the robot's perspective. In the top right it shows "Waiting for data on rerun: http://127.0.0.1:9876/remote...", with data source information below. This image relates to the content describing the rerun.io window showing the camera feed in real time, visually presenting the effect.](../../en/images/d32-02.png)

## If You Run into the Following Error

The camera cannot connect, but switching cameras in Tencent Meeting still opens normally

![The image shows the Windows command line interface with camera detection results. At the top it shows "Detected Cameras" and camera-related information such as name, type, ID and backend API. Below there is an error stating that when running lerobot_find_cameras_openpyc, the OpenCV camera failed to connect or be configured, prompting you to run lerobot_find_cameras_opencv to find an available camera, and that no camera can be connected so image saving will abort. This image corresponds to the context of the camera connection problem, visually presenting the error.](../../en/images/d32-03.png)

Modify the `lerobot\src\lerobot\cameras\utils.py` file to change the OpenCV backend to `cv2.CAP_SHOW`

![The image shows the code of the `get_cv2_backend()` function in the `lerobot\\src\\lerobot\\cameras\\utils.py` file. When the system is Windows, the function returns `int(cv2.CAP_DSHOW)`, used to use MSMF instead of AVFOUNDATION on Windows. The code also contains a comment about `cv2.CAP_MSMF`, and how other systems such as Darwin (macOS) and Linux are handled. This image relates to the operation of modifying the `lerobot\\src\\lerobot\\cameras\\utils.py` file to change the OpenCV backend to `cv2.CAP_SHOW`, and is a code modification example.](../../en/images/d32-04.png)

> This is a bug that even Doubao cannot solve; it is all because the lerobot library is wrapped too deeply, and it is very hard for beginners to debug

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## Connecting Multiple Cameras, Teleoperation with the Camera Feeds Displayed

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![The image shows the rerun.io window used for teleoperation with camera feeds. On the left is a trajectory chart showing trajectory data for several joints, such as observation_wrist_l_pos and observation_wrist_r_pos. On the right, the top is the live camera feed and the bottom is the Tencent Meeting window. In the top right it shows "Waiting for data on rerun: http://127.0.0.1:9678/remote...". This image relates to the content on connecting multiple cameras and showing camera feeds during teleoperation, visually presenting the effect.](../../en/images/d32-05.png)