[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | 한국어 | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# 클라우드 GPU 학습 환경 구성

## 사용하는 컴퓨터의 네트워크 프록시 끄기

그렇지 않으면 Jupyter 명령줄을 열 수 없습니다

## 클라우드 GPU 플랫폼 Featurize 로그인

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## 클라우드 GPU 인스턴스 시작

<grid>
<column width-ratio="0.597692">
![이 이미지는 Featurize 플랫폼의 클라우드 GPU 인스턴스 선택 화면으로, 서로 다른 사양의 클라우드 GPU 인스턴스 옵션이 주로 표시되어 있습니다. 빨간 상자로 표시된 옵션은 RTX 5090 클라우드 GPU 인스턴스로, 사용 가능 수량 2.0, 종량제 요금 3 CNY/시간, GPU 메모리 32.0 GB, 38코어 AMD EPYC 9354 프로세서와 128 GB RAM으로 기재되어 있습니다. 그 아래에는 "Start Using"과 "Reserve" 버튼이 있고, 빨간 화살표가 "Start Using"을 가리키며, 이는 문서의 "클라우드 GPU 인스턴스 시작" 안내와 일치합니다.](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![이 이미지는 Featurize 플랫폼의 이미지 선택 화면을 보여줍니다. "Select Image" 탭이 있고 그 아래에 "Official Images", "My Images", "Popular Images" 세 개의 하위 탭이 있습니다. "Official Images" 탭에서 PyTorch 2 이미지가 빨간 상자와 화살표로 강조되어 있으며, 크기 14.5 GB, 사용 횟수 19,001회, "Official" 라벨이 붙어 있습니다. 이 이미지는 클라우드 GPU 인스턴스를 시작한 뒤 "JupyterLab"을 클릭해 코드와 데이터셋을 업로드하는 과정을 설명하는 문맥과 밀접하게 관련되어 있으며, 이미지 선택 단계에서 공식 이미지 옵션을 보여주어 이후의 환경 설정과 구성에 사용됩니다.](../../en/images/d45-02.png)
</column>
</grid>

![이 이미지는 클라우드 GPU 인스턴스의 콘솔을 보여주며, 문서의 "클라우드 GPU 인스턴스 시작" 단계에 대응해 인스턴스를 시작한 뒤 사용할 수 있는 작업들을 나타냅니다. RTX 5090 인스턴스의 사양(GPU, CPU, 메모리, 디스크 파라미터 등)과 인스턴스의 임대 시간, 과금 방식, 비용이 표시되어 있습니다. 빨간 화살표와 빨간 상자가 "Open Workspace" 버튼을 강조하여, 사용자가 이것을 클릭해 JupyterLab 작업으로 넘어가 코드와 데이터셋을 업로드하도록 안내합니다.](../../en/images/d45-03.png)

![이 이미지는 JupyterLab 인터페이스를 보여줍니다. 왼쪽은 파일 관리 영역으로 "Instances", "Files", "Terminal" 탭이 있고 현재 "Files" 탭이 선택되어 있습니다. 오른쪽은 Launcher 영역으로 Notebook, Console, Python 3 (ipykernel) 등의 옵션이 표시되어 있습니다. 이미지의 빨간 화살표는 왼쪽 파일 관리 영역의 "Files" 탭을 가리키며, "아래의 JupyterLab을 클릭하세요. 왼쪽 상단에 업로드 버튼이 있어 코드와 데이터셋을 업로드할 수 있습니다"라는 문맥과 호응하여 JupyterLab에서의 파일 관련 작업을 안내합니다.](../../en/images/d45-04.png)

> 아래의 "JupyterLab"을 클릭하세요. 왼쪽 상단에 업로드 버튼이 있어 코드와 데이터셋을 업로드할 수 있습니다

## 환경 설치 및 구성

```Shell
conda create -y -n lerobot python=3.12
conda activate lerobot
conda install ffmpeg=7.1.1 -c conda-forge -y
# git clone https://github.com/Seeed-Projects/lerobot.git ~/work/Lerobot
git clone https://github.com/huggingface/lerobot.git
cd lerobot
pip install -e ".[pi]"
pip install wandb --upgrade
# export HF_ENDPOINT=https://hf-mirror.com
hf auth login

# HuggingFace에 업로드하지 않고 wandb도 필요 없다면 설치하지 않아도 됩니다
```

> 모델을 설치할 때 `training`이 빠져 있었다면 추가로 설치해야 합니다
> 
> `pip install -e ".[training]"`

## wandb 로그인

```Shell
wandb login
API Key를 복사해 붙여 넣고 Enter를 누르세요
```

![이 이미지는 LeRobot 프로젝트의 wandb 로그인 화면으로, 로그인 과정의 정보를 기록하고 있습니다. wandb 로그인을 시작하며 사용자에게 지정된 주소에서 API 키를 찾아 키를 붙여 넣고 Enter를 눌러 제출하라고 안내합니다. 또한 netrc 파일을 찾지 못했고 해당 netrc 파일 경로에 API 키를 추가하고 있다는 내용을 보여주며, 이후 로그인이 완료되어 현재 로그인 사용자가 tommyzihao로 표시되고 강제 재로그인 명령도 함께 제공됩니다. 이 이미지는 문서의 "wandb 로그인" 단계에 대응해 로그인 과정과 결과를 보여줍니다.](../../en/images/d45-05.png)

## 데이터셋 마운트

```Shell
인스턴스 다운로드 명령을 복사합니다. 예를 들면:
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

데이터셋은 `~` 디렉터리 아래에 나타납니다

## 가중치 저장 주기 조정(선택)

`lerobot/src/lerobot/configs/train.py`를 엽니다

save_freq를 20_000에서 5_000으로 변경합니다

이렇게 하면 학습 중에 모델 가중치 파일을 더 일찍 얻을 수 있습니다
