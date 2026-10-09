[English](../../en/basics/lerobot-datasets-on-huggingface.md) | [简体中文](../../zh-hans/basics/lerobot-datasets-on-huggingface.md) | [繁體中文](../../zh-hant/basics/lerobot-datasets-on-huggingface.md) | [Deutsch](../../de/basics/lerobot-datasets-on-huggingface.md) | [Español](../../es/basics/lerobot-datasets-on-huggingface.md) | [Français](../../fr/basics/lerobot-datasets-on-huggingface.md) | [Italiano](../../it/basics/lerobot-datasets-on-huggingface.md) | [日本語](../../ja/basics/lerobot-datasets-on-huggingface.md) | 한국어 | [Português (BR)](../../pt-br/basics/lerobot-datasets-on-huggingface.md) | [Português (PT)](../../pt-pt/basics/lerobot-datasets-on-huggingface.md)

# HuggingFace의 LeRobot 데이터셋

## LeRobot 형식의 오픈소스 데이터셋

https://huggingface.co/blog/lerobot-datasets#what-makes-a-good-dataset

![이 이미지는 "Cumulative number of LeRobot datasets uploaded last year"라는 제목의 꺾은선 그래프로, 가로축은 2023년 12월 1일부터 2024년 5월 1일까지의 날짜를, 세로축은 0에서 3500까지의 데이터셋 수를 나타냅니다. 파란색 선이 상승 추세를 보이며, 지난 한 해 동안 업로드된 LeRobot 데이터셋 수가 지속적으로 증가했음을 나타냅니다. 이 그래프는 HuggingFace의 LeRobot 데이터셋 소개와 관련이 있으며, 업로드된 데이터셋 수가 어떻게 변화했는지 시각적으로 제시합니다.](../../en/images/d05-01.png)

![이 이미지는 "Number of Datasets for the 10 most frequent robots"라는 제목의 막대 그래프입니다. 가로축은 로봇 유형을 나타내며 왼쪽에서 오른쪽으로 so100, loch, ar25_manual, moos, unknown, aloha, alohastationary, transen_al_solo, orix, alohastationary 순입니다. 세로축은 데이터셋 수를 나타냅니다. so100이 1750개가 넘어 압도적으로 가장 많고, 다른 로봇 유형은 상대적으로 적어 예를 들어 aloha와 alohastationary는 각각 100개 미만입니다. 이 그래프는 LeRobot 형식의 오픈소스 데이터셋 소개와 관련이 있으며, 가장 많이 등장하는 10개 로봇 유형의 데이터셋 수를 보여줍니다.](../../en/images/d05-02.png)

![이 이미지는 LeRobot 데이터셋의 소스 계층 구조를 보여줍니다. 맨 위에는 실제 환경의 로봇 이미지를 담은 주황색 삼각형으로 표시된 "Real-World Data"가 있습니다. 중간 계층은 가상 환경의 로봇 이미지를 담은 녹색 삼각형으로 표시된 "Synthetic Data"입니다. 맨 아래에는 Common Crawl, Reddit, Wikipedia, Epic Kitchen 등의 소스 레이블을 담은 파란색 사다리꼴로 표시된 "Web Data & Human Videos"가 있습니다. 이 이미지는 LeRobot 데이터셋의 소스 소개와 관련이 있으며, 데이터셋이 어떻게 구성되는지 시각적으로 제시합니다.](../../en/images/d05-03.png)

## 흥미로운 LeRobot 데이터셋 몇 가지



색상별 젤리빈 분류

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FMarkusWuenstel%2Fso101-sort-color-joint-angles-preprocessed%2Fepisode_0



레고 브릭을 상자에 넣기

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flerobot%2Fsvla_so101_pickplace%2Fepisode_0



테이블 정리

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fyouliangtan%2Fso101-table-cleanup%2Fepisode_0



블록 밀기

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FIPEC-COMMUNITY%2Flanguage_table_lerobot%2Fepisode_17



T자 부품을 올바른 위치에 배치하기 (시뮬레이션 데이터)

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flerobot%2Fpusht%2Fepisode_15



서랍 닫기

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flirislab%2Fclose_top_drawer_teabox%2Fepisode_1

체스 대국 — 강조 표시된 칸에 기물 놓기

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FChojins%2Fchess_game_001_blue_stereo%2Fepisode_1

동물 블록 정렬

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fpierfabre%2Fchicken%2Fepisode_6



다양한 집안일

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fcadene%2Fdroid_1.0.1%2Fepisode_13
