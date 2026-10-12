[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | 한국어 | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Mac 컴퓨터

## 카메라를 컴퓨터에 연결

```Shell
lerobot-find-cameras opencv
```

![이 이미지는 Mac에 카메라를 연결한 뒤의 감지 결과를 보여 줍니다. 자동으로 생성된 두 카메라, 즉 외장 카메라와 Mac의 내장 전면 카메라가 나열됩니다. 외장 카메라의 Fps는 60.00024이고 내장 카메라의 Fps는 30.0입니다. 이 이미지는 Mac에 카메라를 연결하는 내용과 관련이 있으며, 연결 후의 감지 결과를 시각적으로 보여 주어 사용자가 각 카메라의 유형, ID, 백엔드 API, 프레임 레이트를 이해하는 데 도움을 줍니다.](../../en/images/d31-01.png)

## 카메라 한 대, 카메라 화면을 표시하며 텔레오퍼레이션

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

실행하면 텔레오퍼레이션이 시작됩니다

rerun.io 창이 열리고, 각 서보 관절의 궤적이 실시간으로 표시되며 카메라 화면도 함께 보입니다

그리고 이미지를 `~/username/outputs/captured_images` 디렉터리에 저장합니다

![이 이미지는 실행 후 텔레오퍼레이션이 시작될 때 열리는 rerun.io 창을 보여 줍니다. 왼쪽에는 여러 서보 관절의 궤적 차트가 있으며, 서로 다른 관절의 움직임을 보여 주는 곡선으로 표시됩니다. 오른쪽에는 실내 장면의 카메라 화면이 실시간으로 표시되며, 테이블, 의자, 몇 가지 물체를 볼 수 있습니다. 하단에는 막대 모양의 정보도 있습니다. 이 이미지는 본문과 밀접하게 관련되어 있으며, 텔레오퍼레이션 중의 서보 관절 궤적과 실시간 카메라 화면을 시각적으로 보여 주고, 이미지가 지정된 디렉터리에 저장된다는 것도 설명합니다.](../../en/images/d31-02.png)

## 카메라 여러 대, 카메라 화면을 표시하며 텔레오퍼레이션

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

![이 이미지는 카메라 화면을 여러 개 표시하며 텔레오퍼레이션하는 데 사용되는 rerun.io 창을 보여 줍니다. 왼쪽은 실시간 카메라 화면으로 책상 위의 물체를 보여 줍니다. 오른쪽은 observation_wip 같은 서로 다른 관절의 궤적을 보여 주는 데이터 차트입니다. 하단에는 여러 관절의 데이터를 나열하는 Streams 영역이 있습니다. 오른쪽 상단에는 Application ID, Source IP 같은 데이터 정보가 있습니다. 이 이미지는 "카메라 여러 대, 카메라 화면을 표시하며 텔레오퍼레이션" 내용에 해당하며, 텔레오퍼레이션 중의 화면과 데이터를 시각적으로 보여 줍니다.](../../en/images/d31-03.png)
