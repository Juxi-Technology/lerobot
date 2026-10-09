[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | 繁體中文 | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# 示教採集資料集-握手200

## 在HuggingFace上建立Dataset Repo

https://huggingface.co/new-dataset

![圖片展示了在HuggingFace上建立新資料集儲存庫的介面。介面中「Owner」處顯示為TommyZihao，資料集名稱為「lerobot_zihao_dataset_shake200」，「License」選擇為mit，資料集類型為「Public」，任何人都可檢視，只有資料集擁有者或組織成員可提交。下方提示建立資料集後可使用web介面或git上傳檔案，底部有「Create dataset」按鈕。該圖片與文件中在HuggingFace上建立Dataset Repo的內容相關，是建立資料集儲存庫操作的介面展示。](../../en/images/d37-01.png)

## 刪除之前已經有的同名資料集（如果有）

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Shake200資料集採集

一個攝影機，採集資料集-Mac電腦

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

## 採集中

<grid>
<column width-ratio="0.508765">
![圖片展示的是在Mac電腦上採集資料集時的終端機介面。介面中顯示了SvtInfo()和SvtInfo()的輸出資訊，包括版本號、編譯器、架構等。還呈現了SvtConfig()的設定參數，如寬度、高度、影格率、預設等。下方有「INFO」和「INFO 0」標識的輸出資訊，如「Starting second pass: moving the moving atom to the beginning of the file」等。該圖片與文件中「採集中」內容相關，直觀呈現了採集過程中終端機顯示的設定與資訊。](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![圖片展示的是在Mac電腦上使用Open_Duck_Mini_Runtime_2指令碼採集資料集時的終端機輸出資訊。畫面中顯示了SVT等影片編碼相關設定參數，如gop size、key - frame type等，還呈現了影片編碼器版本、編譯日期等資訊。下方有MP4檔案相關日誌，如「Starting second pass: moving the moov atom to the beginning of the file」等。該圖片與文件中採集資料集的操作流程相關，直觀呈現了採集過程中終端機的回饋資訊。](../../en/images/d37-03.png)
</column>
</grid>

鍵盤方向鍵操作：  
→（右箭頭）提前終止目前episode；進入下一個episode。  
←（左箭頭）取消目前episode；重新錄製。  
ESC，立即停止，編碼影片，並上傳資料集。

## 採集完畢，資料集儲存目錄

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
