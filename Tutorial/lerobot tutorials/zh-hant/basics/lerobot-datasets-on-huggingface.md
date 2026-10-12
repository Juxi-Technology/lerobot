[English](../../en/basics/lerobot-datasets-on-huggingface.md) | [简体中文](../../zh-hans/basics/lerobot-datasets-on-huggingface.md) | 繁體中文 | [Deutsch](../../de/basics/lerobot-datasets-on-huggingface.md) | [Español](../../es/basics/lerobot-datasets-on-huggingface.md) | [Français](../../fr/basics/lerobot-datasets-on-huggingface.md) | [Italiano](../../it/basics/lerobot-datasets-on-huggingface.md) | [日本語](../../ja/basics/lerobot-datasets-on-huggingface.md) | [한국어](../../ko/basics/lerobot-datasets-on-huggingface.md) | [Português (BR)](../../pt-br/basics/lerobot-datasets-on-huggingface.md) | [Português (PT)](../../pt-pt/basics/lerobot-datasets-on-huggingface.md)

# HuggingFace上的LeRobot資料集

## LeRobot格式的開源資料集

https://huggingface.co/blog/lerobot-datasets#what-makes-a-good-dataset

![圖片為「LeRobot資料集上傳去年累計數量」折線圖，橫軸為日期，從2023年12月1日到2024年5月1日，縱軸為資料集數量，從0到3500。圖中藍色線條呈上升趨勢，表明去年上傳的LeRobot資料集數量持續成長。該圖與文件中介紹HuggingFace上的LeRobot資料集的內容相關，直觀呈現了資料集上傳數量的變化情況。](../../en/images/d05-01.png)

![圖片為柱狀圖，標題為「Number of Datasets for the 10 most frequent robots」。橫軸為機器人類型，從左至右依次為so100、loch、ar25_manual、moos、unknown、aloha、、alohastationary、transen_al_solo、orix、alohastationary。縱軸為資料集數量。其中so100資料集數量最多，超過1750個，其他機器人類型資料集數量相對較少，如aloha、alohastationary等資料集數量均在100以下。該圖與文件中介紹LeRobot格式的開源資料集上下文相關，展示了10個最頻繁機器人類型的資料集數量情況。](../../en/images/d05-02.png)

![圖片展示了LeRobot資料集的來源層次結構。最上方是「Real-World Data」，以一個橙色三角形呈現，內有機器人在真實環境中的圖像。中間層次是「Synthetic Data」，以綠色三角形展示，包含機器人在虛擬環境中的圖像。最下方是「Web Data & Human Videos」，以藍色梯形呈現，包含Common Crawl、Reddit、Wikipedia、Epic Kitchen等來源標識。該圖與文件中介紹LeLeRobot資料集來源的內容相關，直觀呈現了資料集的構成。](../../en/images/d05-03.png)

## 幾個有意思的LeRobot資料集



篩選不同顏色的糖果豆

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FMarkusWuenstel%2Fso101-sort-color-joint-angles-preprocessed%2Fepisode_0



把樂高積木放到盒子裡

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flerobot%2Fsvla_so101_pickplace%2Fepisode_0



整理桌面

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fyouliangtan%2Fso101-table-cleanup%2Fepisode_0



推積木

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FIPEC-COMMUNITY%2Flanguage_table_lerobot%2Fepisode_17



把T形零件擺到正確位置（模擬資料）

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flerobot%2Fpusht%2Fepisode_15



關抽屜

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flirislab%2Fclose_top_drawer_teabox%2Fepisode_1

國際象棋比賽，把棋子放到高亮格子上

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FChojins%2Fchess_game_001_blue_stereo%2Fepisode_1

擺放動物積木

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fpierfabre%2Fchicken%2Fepisode_6



各種家務

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fcadene%2Fdroid_1.0.1%2Fepisode_13