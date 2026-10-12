[English](../en/urdf-and-resources.md) | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | [Español](../es/urdf-and-resources.md) | [Français](../fr/urdf-and-resources.md) | [Italiano](../it/urdf-and-resources.md) | [日本語](../ja/urdf-and-resources.md) | 한국어 | [Português (BR)](../pt-br/urdf-and-resources.md) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>URDF 파일 및 참고 리소스</title>

# Lerbot 공식 [URDF 파일](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf)



## URDF Studio

https://urdf.d-robotics.cc/



## ROS2 시뮬레이션 제어 (직접 구현)

https://github.com/holmsslk/so-arm-moveit-hardware



## LeRobot 공식 그래픽 인터페이스

https://github.com/huggingface/leLab

LeLab은 캘리브레이션, 원격조작, 기록, 학습, 재생 등 LeRobot의 모든 워크플로를 하나의 브라우저 인터페이스에 담은 웹 앱입니다. 로봇 팔을 연결하고 앱을 열기만 하면 바로 작업을 시작할 수 있습니다. 번거로운 명령줄 작업도, 키보드 입력도 필요하지 않습니다.

🤗 LeRobot의 네이티브 웹 진입점으로, 신규 사용자가 "개봉 직후" 상태에서 몇 분 만에 "첫 정책 학습"까지 도달하도록 설계되었습니다.

🤗 단 하나의 명령으로 모든 것을 설치하고 실행합니다.



# 스마트폰으로 Follower 암 제어하기

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## 클라우드 로보틱스 개발: AWS에서의 ROS 2 디바이스와 Isaac Sim LeRobot 시뮬레이션 및 데이터 스트리밍

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## 웹 UI에서 서보 ID 설정 및 중심 캘리브레이션

https://bambot.org/feetech.js?lang=zh

1. 서보 모델에 따라 0 또는 1을 입력한 뒤 "Connect"를 클릭합니다

![이 이미지는 웹 UI에서 서보 ID 설정과 중심 캘리브레이션을 위한 연결 인터페이스를 보여줍니다. 인터페이스에는 "Connect" 섹션이 있으며, 여기에는 현재 "1,000,000 bps (Index 0)"로 설정된 보드레이트 드롭다운, 현재 "0=STS/SMS"로 설정된 프로토콜 엔드 드롭다운, 그리고 "Connect" 버튼이 있습니다. 인터페이스 하단에는 "Status: Disconnected"가 표시됩니다. 이 이미지는 서보 모델에 따라 0 또는 1을 입력하고 "Connect"를 클릭하면 ID 1~6의 서보를 스캔하여 해당 ID 서보를 확인하는 흐름과 밀접하게 연결된 핵심 인터페이스입니다.](../en/images/d68-01.png)

2. ID 1\~6의 서보를 스캔합니다. 스캔 결과에서 FOUND를 사용해 해당 ID 서보를 확인합니다. 예를 들어 이미지에서는 서보 ID 1이 발견되었습니다

![이 이미지는 Lerbot 공식 URDF Studio의 서보 스캔 인터페이스를 보여줍니다. 인터페이스에는 시작 ID 1과 종료 ID 6이 표시되고, 그 아래에 "Start scan" 버튼이 있습니다. 스캔 결과에서는 ID1을 스캔했을 때 ID1239가 발견되며, ID2부터 ID6까지를 스캔하면 각각 "ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0"이라고 보고됩니다. 이 이미지는 문맥에서 설명하는 Lerbot 공식 URDF Studio의 서보 스캔 작업과 관련이 있으며, 스캔 과정과 그 결과를 시각적으로 제시합니다.](../en/images/fix-01.png)

3. ID 설정 및 중심 캘리브레이션

① 현재 서보 ID 입력란을 스캔한 서보의 ID로 설정합니다

② "ID management"에 숫자를 입력하고 "Change ID"를 클릭해 ID를 설정합니다

③ 중심 캘리브레이션 (STS3215 서보의 중심은 2047, SCS0009 서보의 중심은 511입니다)

STS 서보: "Position control"에 2047을 입력하고 "Set"을 클릭합니다

SCS 서보: "Position control"에 511을 입력하고 "Set"을 클릭합니다

![이 이미지는 Lerbot의 단일 서보 제어 인터페이스를 보여줍니다. "Current servo ID"는 1로 표시되며, 아래의 "ID management"에는 숫자 1과 "Change ID" 버튼이 있고 그 아래에 "Success: ID changed to 1"이라는 메시지가 표시됩니다. Position Control 영역에는 위치 2047을 표시하는 "Read position" 버튼이 있고 그 옆에 "Set" 버튼이 있습니다. 이 이미지는 문서의 "ID 설정 및 중심 캘리브레이션" 섹션과 관련이 있으며, 서보 ID 설정과 중심 캘리브레이션을 위한 인터페이스를 시각적으로 제시하여 사용자가 Lerbot에서 이러한 설정을 수행하는 방법을 이해하도록 돕습니다.](../en/images/d68-02.png)
