[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | 繁體中文 | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# 雲GPU訓練環境設定

## 關閉自己電腦的網路代理

不然可能打不開Jupyter的命令列

## 登入雲GPU平台Featurize

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## 開啟一個雲GPU實例

<grid>
<column width-ratio="0.597692">
![這張圖片是Featurize平台的雲GPU實例選擇介面，核心展示了不同配置的雲GPU實例選項，其中被紅色框標註出的是RTX 5090雲GPU實例，該實例標註為2.0可用，按量使用費用為3元/小時，顯示卡顯示記憶體達32.0GB，搭載38核AMD EPYC 9354處理器及128G記憶體，其下方有「開始使用」和「預定」兩個按鈕，並有紅色箭頭指向「開始使用」按鈕，對應文件中「開啟一個雲GPU實例」的操作指引內容。](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![圖片展示的是Featurize平台中選擇鏡像的介面。介面中顯示有「選擇鏡像」選項卡，下方有「官方鏡像」「我的鏡像」「熱門鏡像」三個標籤。其中「官方鏡像」標籤下，PyTorch 2鏡像被紅色框和箭頭突出顯示，其大小為14.5 GB，已使用19001次，標註為「官方」。該圖片與上下文關係緊密，上下文提到開啟雲GPU實例後，點擊「JupyterLab」並上傳程式碼和資料集，此圖即為選擇鏡像操作中展示的官方鏡像選項，用於後續安裝設定環境等操作。](../../en/images/d45-02.png)
</column>
</grid>

![這張圖片是雲GPU實例的操作介面，對應文件中「開啟一個雲GPU實例」的步驟內容，用於展示實例開啟後的操作選項。介面中顯示了型號為RTX 5090的實例的相關設定資訊，包括GPU、CPU、記憶體、硬碟的參數，以及實例的租用時間、方式、費用等內容。圖中用紅色箭頭和紅色框突出標註了「開啟工作區」按鈕，提示使用者需點擊該按鈕，以進入後續進行JupyterLab操作、上傳程式碼和資料集的環節。](../../en/images/d45-03.png)

![圖片展示了JupyterLab介面，左側為檔案管理區域，有「實例」「檔案」「終端機」等選項卡，目前選中「檔案」選項卡。右側是Launcher區域，顯示了Notebook、Console、Python 3（ipykernel）等選項。圖片中紅色箭頭指向左側檔案管理區域的「檔案」選項卡，突出顯示該操作位置，與上下文「點擊下方的『JupyterLab』，左上角有個上傳按鈕，可以在這裡上傳程式碼和資料集」相呼應，指導使用者在JupyterLab中進行檔案相關操作。](../../en/images/d45-04.png)

> 點擊下方的「JupyterLab」，左上角有個上傳按鈕，可以在這裡上傳程式碼和資料集

## 安裝設定環境

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

# 不上传到Huggingface和不需要wandb则不用安装
```

> 如果在模型安裝的時候缺少了training，需要額外安裝一下
> 
> `pip install -e ".[training]"`

## 登入wandb

```Shell
wandb login
复制粘贴API Key，回车
```

![這張圖片展示的是Lerobot專案的wandb登入操作介面，記錄了登入過程的相關資訊。內容從啟動wandb登入開始，提示使用者需要存取指定位址查找API金鑰，並將金鑰貼上後按Enter鍵提交。介面還顯示系統未找到netrc檔案，正在添加API金鑰到對應的netrc檔案路徑中，最終完成登入，顯示目前登入使用者為tommyzihao，同時提供了強制重新登入的命令指引。該圖片對應文件中「登入wandb」的步驟，呈現了登入操作的過程和結果。](../../en/images/d45-05.png)

## 掛載資料集

```Shell
复制实例下载命令，类似：
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

資料集出現在`~`目錄下

## 修改權重儲存頻率（選做）

開啟`lerobot/src/lerobot/configs/train.py`

將save_freq，從20_000修改為5_000

這樣能在訓練更早期取得模型權重檔案
