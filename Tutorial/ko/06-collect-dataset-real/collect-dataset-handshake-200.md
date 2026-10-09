[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | 한국어 | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# 시연으로 데이터셋 수집하기 — Handshake 200

## HuggingFace에 데이터셋 저장소 생성

https://huggingface.co/new-dataset

![이 이미지는 HuggingFace에서 새 데이터셋 저장소를 만드는 인터페이스를 보여 줍니다. "Owner"는 TommyZihao로, 데이터셋 이름은 "lerobot_zihao_dataset_shake200", "License"는 mit로 설정되어 있고, 데이터셋 유형은 "Public"으로 누구나 볼 수 있으며 데이터셋 소유자나 조직 구성원만 커밋할 수 있습니다. 아래에는 데이터셋을 만든 뒤 웹 인터페이스나 git을 통해 파일을 업로드할 수 있다는 안내와 함께 하단에 "Create dataset" 버튼이 있습니다. 이 이미지는 HuggingFace에 데이터셋 저장소를 만드는 내용과 관련이 있으며, 데이터셋 생성 작업의 인터페이스를 보여 줍니다.](../../en/images/d37-01.png)

## 같은 이름의 기존 데이터셋 삭제(있을 경우)

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Shake200 데이터셋 수집

카메라 한 대, 데이터셋 수집 - Mac 컴퓨터

```Shell
lerobot-record \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true \
    --dataset.repo_id=Tommymy/lerobot_my_dataset_shake200 \
    --dataset.num_episodes=200 \
    --dataset.single_task="Shanke Hands" \
    --dataset.push_to_hub=false \
    --dataset.episode_time_s=12 \
    --dataset.reset_time_s=1
```

## 수집 중

<grid>
<column width-ratio="0.508765">
![이 이미지는 Mac에서 데이터셋을 수집하는 동안의 터미널 인터페이스를 보여 줍니다. 버전 번호, 컴파일러, 아키텍처를 포함한 SvtInfo() 및 SvtInfo()의 출력이 표시됩니다. 또한 width, height, frame rate, preset 같은 SvtConfig() 구성 매개변수를 보여 줍니다. 아래에는 "INFO" 및 "INFO 0"으로 표시된 출력이 있는데, 예를 들어 "Starting second pass: moving the moving atom to the beginning of the file"가 있습니다. 이 이미지는 "수집 중" 내용과 관련이 있으며, 수집 중 터미널에 표시되는 구성과 정보를 시각적으로 보여 줍니다.](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![이 이미지는 Mac에서 Open_Duck_Mini_Runtime_2 스크립트로 데이터셋을 수집하는 동안의 터미널 출력을 보여 줍니다. gop size, key - frame type 같은 SVT 및 기타 비디오 인코딩 구성 매개변수를 보여 주고, 비디오 인코더 버전과 빌드 날짜를 표시합니다. 아래에는 "Starting second pass: moving the moov atom to the beginning of the file" 같은 MP4 파일 로그가 있습니다. 이 이미지는 데이터셋 수집 워크플로와 관련이 있으며, 수집 중의 터미널 피드백을 시각적으로 보여 줍니다.](../../en/images/d37-03.png)
</column>
</grid>

키보드 화살표 키 조작:  
→ (오른쪽 화살표) 현재 에피소드를 조기에 종료하고 다음 에피소드로 넘어갑니다.  
← (왼쪽 화살표) 현재 에피소드를 취소하고 다시 기록합니다.  
ESC, 즉시 중지하고, 비디오를 인코딩한 뒤 데이터셋을 업로드합니다.

## 수집 완료 — 데이터셋 저장 디렉터리

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
