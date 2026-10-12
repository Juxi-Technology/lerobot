[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | 한국어 | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Windows 컴퓨터

## 카메라를 컴퓨터에 연결

```Shell
lerobot-find-cameras opencv
```

![이 이미지는 Windows 명령 줄 창으로, 카메라 연결 오류와 장치 감지 결과를 보여 줍니다. 상단에는 "ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range" 오류가 있습니다. 아래에는 Camera #0과 Camera #1을 포함하여 감지된 카메라가 이름, 유형, 백엔드 API, 기본 스트림 구성, 형식, 소스, 너비, 높이, 프레임 레이트와 함께 나열되며, 하단에는 "lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0" 같은 오류가 있습니다. 이는 문서에서 언급한 "카메라가 연결되지 않지만 Tencent Meeting에서 카메라를 바꾸면 정상적으로 열리는" 오류 시나리오에 해당하며, OpenCV 백엔드 코드를 수정하기 전의 실제 런타임 오류 피드백입니다.](../../en/images/d32-01.png)

## 카메라 화면을 표시하며 텔레오퍼레이션

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

rerun.io 창이 열리고, 각 서보 관절의 궤적이 실시간으로 표시되며 카메라 화면도 함께 보입니다

그리고 이미지를 `C:\Users\username\outputs\captured_images` 디렉터리에 저장합니다

![이 이미지는 서보 관절의 궤적과 실시간 카메라 화면을 실시간으로 표시하는 rerun.io 창을 보여 줍니다. 왼쪽은 "teleoperation" 같은 옵션이 있는 블루프린트 인터페이스입니다. 가운데는 "observation_wrist_rot.pos" 같은 관절 위치 데이터를 보여 주는 궤적 차트입니다. 오른쪽은 로봇 시점의 장면을 보여 주는 카메라 화면입니다. 오른쪽 상단에는 "Waiting for data on rerun: http://127.0.0.1:9876/remote..."가 표시되고 그 아래에 데이터 소스 정보가 있습니다. 이 이미지는 카메라 화면을 실시간으로 보여 주는 rerun.io 창을 설명하는 내용과 관련이 있으며, 그 효과를 시각적으로 보여 줍니다.](../../en/images/d32-02.png)

## 다음과 같은 오류가 발생하면

카메라가 연결되지 않지만 Tencent Meeting에서 카메라를 바꾸면 여전히 정상적으로 열립니다

![이 이미지는 카메라 감지 결과가 있는 Windows 명령 줄 인터페이스를 보여 줍니다. 상단에는 "Detected Cameras"와 이름, 유형, ID, 백엔드 API 같은 카메라 관련 정보가 표시됩니다. 아래에는 lerobot_find_cameras_openpyc를 실행할 때 OpenCV 카메라 연결 또는 구성에 실패했고, 사용 가능한 카메라를 찾으려면 lerobot_find_cameras_opencv를 실행하라고 안내하며, 연결할 수 있는 카메라가 없어 이미지 저장을 중단한다는 오류가 있습니다. 이 이미지는 카메라 연결 문제의 맥락에 해당하며, 오류를 시각적으로 보여 줍니다.](../../en/images/d32-03.png)

`lerobot\src\lerobot\cameras\utils.py` 파일을 수정하여 OpenCV 백엔드를 `cv2.CAP_SHOW`로 변경합니다

![이 이미지는 `lerobot\\src\\lerobot\\cameras\\utils.py` 파일에 있는 `get_cv2_backend()` 함수의 코드를 보여 줍니다. 시스템이 Windows일 때 함수는 `int(cv2.CAP_DSHOW)`를 반환하며, Windows에서 MSMF 대신 AVFOUNDATION을 사용하는 데 쓰입니다. 코드에는 `cv2.CAP_MSMF`에 대한 주석과 Darwin(macOS) 및 Linux 같은 다른 시스템을 처리하는 방법도 포함되어 있습니다. 이 이미지는 `lerobot\\src\\lerobot\\cameras\\utils.py` 파일을 수정하여 OpenCV 백엔드를 `cv2.CAP_SHOW`로 변경하는 작업과 관련이 있으며, 코드 수정 예시입니다.](../../en/images/d32-04.png)

> 이는 Doubao조차 해결할 수 없는 버그로, 모두 lerobot 라이브러리가 너무 깊게 감싸여 있어 초보자가 디버깅하기 매우 어렵기 때문입니다

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## 카메라 여러 대를 연결, 카메라 화면을 표시하며 텔레오퍼레이션

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![이 이미지는 카메라 화면과 함께 텔레오퍼레이션하는 데 사용되는 rerun.io 창을 보여 줍니다. 왼쪽은 observation_wrist_l_pos, observation_wrist_r_pos 같은 여러 관절의 궤적 데이터를 보여 주는 궤적 차트입니다. 오른쪽은 위쪽이 실시간 카메라 화면이고 아래쪽이 Tencent Meeting 창입니다. 오른쪽 상단에는 "Waiting for data on rerun: http://127.0.0.1:9678/remote..."가 표시됩니다. 이 이미지는 카메라 여러 대를 연결하고 텔레오퍼레이션 중에 카메라 화면을 보여 주는 내용과 관련이 있으며, 그 효과를 시각적으로 보여 줍니다.](../../en/images/d32-05.png)
