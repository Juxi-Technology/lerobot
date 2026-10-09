[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | 한국어 | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# 흔한 버그와 해결 방법

## 카메라 캡처 실패

![이 이미지는 LeRobot 로봇 코드가 실행될 때의 터미널 출력을 보여줍니다. `INFO` 로그는 OpenCV 카메라가 열리고 Follower가 연결 해제되는 것을 보여주며, `ERROR` 로그는 `camera_opencv.py` 파일에서 `read` 함수가 `OpenCVCamera(0) read failed`로 인해 `RuntimeError`를 발생시켰다고 지적합니다. 이 이미지는 "카메라 캡처 실패" 문제와 관련되어, 코드 실행 시 나타나는 문제를 시각적으로 보여주고 카메라 캡처 실패의 구체적인 원인을 이해하도록 돕습니다.](../../en/images/d65-01.png)

손목 카메라 케이블이 느슨해졌는지 확인하세요. 특히 카메라에 가까운 쪽 끝이 그렇습니다. 그 커넥터는 접촉 불량이 매우 잘 생깁니다

## 카메라 연결 끊김

![이 이미지는 /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py 코드의 실행 인터페이스를 보여줍니다. 상단에는 시간, 프로세스 ID 등의 정보가 표시되어 있고, 아래에는 /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py 같은 코드 경로와 "INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected." 같은 오류 메시지가 있습니다. 핵심 부분은 "raise TimeoutError"와 "TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True."로, 카메라 캡처가 실패했음을 나타냅니다. 이 이미지는 "카메라 캡처 실패" 문제와 관련되어 오류를 시각적으로 보여줍니다.](../../en/images/d65-02.png)

명령줄을 다시 시작하세요

## 서보 통신 문제 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![이 이미지는 다음을 보여줍니다.](../../en/images/d65-03.png)

해결 방법: `lerobot/src/lerobot/motors/motors_bus.py`의 코드에서 모든 `num_retry`를 99로 변경합니다. 특히 오류가 발생한 줄에 있는 값을 그렇게 바꾸세요

![이 이미지는 LeRobot 프로젝트의 `motors_bus.py` 코드 파일 내용을 보여줍니다. `MotorsBusABC` 클래스의 `write` 메서드가 강조되어 있고, `num_retry` 변수가 `99`로 변경되어 있습니다. 이 이미지는 "서보 통신 문제 1" 절과 관련되어, `lerobot/src/lerobot/motors/motors_bus.py`의 코드에서 모든 `num_retry`를 99로, 특히 오류가 발생한 줄에 있는 값을 그렇게 바꾸는 해결 방법에 대응합니다.](../../en/images/d65-04.png)

## 서보 통신 문제 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![이 이미지는 macOS의 zsh 터미널에서의 명령줄 세션을 보여줍니다. 터미널에는 `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py` 같은 여러 파일 경로와 코드 줄 번호가 표시됩니다. `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` 파일의 587번째 줄에서 `ConnectionError`가 발생하며, id=1에 대한 `Torque_Enable` 쓰기가 상태 패킷 없이 실패했다고 보고합니다. 이 이미지는 "서보 통신 문제 2" 내용과 관련되어, 오류 발생 순간의 코드 실행을 시각적으로 보여줍니다.](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![이 이미지는 macOS의 zsh 터미널에서의 명령줄 세션을 보여줍니다. 터미널에는 `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py` 같은 여러 파일 경로와 코드 줄 번호가 표시됩니다. 여기서 `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

해결 방법: 로봇 팔을 다시 캘리브레이션합니다
