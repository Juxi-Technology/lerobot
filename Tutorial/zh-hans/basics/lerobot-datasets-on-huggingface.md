[English](../../en/basics/lerobot-datasets-on-huggingface.md) | 简体中文 | [繁體中文](../../zh-hant/basics/lerobot-datasets-on-huggingface.md) | [Deutsch](../../de/basics/lerobot-datasets-on-huggingface.md) | [Español](../../es/basics/lerobot-datasets-on-huggingface.md) | [Français](../../fr/basics/lerobot-datasets-on-huggingface.md) | [Italiano](../../it/basics/lerobot-datasets-on-huggingface.md) | [日本語](../../ja/basics/lerobot-datasets-on-huggingface.md) | [한국어](../../ko/basics/lerobot-datasets-on-huggingface.md) | [Português (BR)](../../pt-br/basics/lerobot-datasets-on-huggingface.md) | [Português (PT)](../../pt-pt/basics/lerobot-datasets-on-huggingface.md)

# HuggingFace上的LeRobot数据集

## LeRobot格式的开源数据集

https://huggingface.co/blog/lerobot-datasets#what-makes-a-good-dataset

![图片为“LeRobot数据集上传去年累计数量”折线图，横轴为日期，从2023年12月1日到2024年5月1日，纵轴为数据集数量，从0到3500。图中蓝色线条呈上升趋势，表明去年上传的LeRobot数据集数量持续增长。该图与文档中介绍HuggingFace上的LeRobot数据集的内容相关，直观呈现了数据集上传数量的变化情况。](../../en/images/d05-01.png)

![图片为柱状图，标题为“Number of Datasets for the 10 most frequent robots”。横轴为机器人类型，从左至右依次为so100、loch、ar25_manual、moos、unknown、aloha、、alohastationary、transen_al_solo、orix、alohastationary。纵轴为数据集数量。其中so100数据集数量最多，超过1750个，其他机器人类型数据集数量相对较少，如aloha、alohastationary等数据集数量均在100以下。该图与文档中介绍LeRobot格式的开源数据集上下文相关，展示了10个最频繁机器人类型的数据集数量情况。](../../en/images/d05-02.png)

![图片展示了LeRobot数据集的来源层次结构。最上方是“Real-World Data”，以一个橙色三角形呈现，内有机器人在真实环境中的图像。中间层次是“Synthetic Data”，以绿色三角形展示，包含机器人在虚拟环境中的图像。最下方是“Web Data & Human Videos”，以蓝色梯形呈现，包含Common Crawl、Reddit、Wikipedia、Epic Kitchen等来源标识。该图与文档中介绍LeLeRobot数据集来源的内容相关，直观呈现了数据集的构成。](../../en/images/d05-03.png)

## 几个有意思的LeRobot数据集



筛选不同颜色的糖果豆

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FMarkusWuenstel%2Fso101-sort-color-joint-angles-preprocessed%2Fepisode_0



把乐高积木放到盒子里

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flerobot%2Fsvla_so101_pickplace%2Fepisode_0



整理桌面

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fyouliangtan%2Fso101-table-cleanup%2Fepisode_0



推积木

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FIPEC-COMMUNITY%2Flanguage_table_lerobot%2Fepisode_17



把T形零件摆到正确位置（仿真数据）

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flerobot%2Fpusht%2Fepisode_15



关抽屉

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flirislab%2Fclose_top_drawer_teabox%2Fepisode_1

国际象棋比赛，把棋子放到高亮格子上

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FChojins%2Fchess_game_001_blue_stereo%2Fepisode_1

摆放动物积木

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fpierfabre%2Fchicken%2Fepisode_6



各种家务

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fcadene%2Fdroid_1.0.1%2Fepisode_13