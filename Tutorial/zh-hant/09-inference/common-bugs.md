[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | 繁體中文 | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# 常見Bug及解決

## 攝影機取得失敗

![圖片展示的是Lerobot機器人相關程式碼執行時的終端機輸出資訊。其中，`INFO`日誌顯示了OpenCV攝影機開啟、Follower斷連等資訊；`ERROR`日誌則指出在`camera_opencv.py`檔案中，`read`函式因`OpenCVCamera(0) read failed`而引發`RuntimeError`。該圖片與文件中「攝影機取得失敗」問題相關，直觀呈現了程式碼執行時出現的問題，輔助理解攝影機取得失敗的具體原因。](../../en/images/d65-01.png)

檢查一下腕部攝影機的接線是否鬆動，特別是靠近攝影機那端的接線，非常容易接觸不良

## 攝影機斷連

![圖片展示的是L /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py 程式碼執行介面。介面上方顯示了時間、行程ID等資訊，下方是 /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py 等程式碼路徑及報錯資訊，如「INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.」等。關鍵部分是「raise TimeoutError」及「TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.」，表明攝影機取得失敗。該圖片與文件中「攝影機取得失敗」問題相關，直觀呈現了報錯情況。](../../en/images/d65-02.png)

重新啟動一下命令列

## 伺服馬達通訊問題1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![圖片展示的是](../../en/images/d65-03.png)

解決方案，把`lerobot/src/lerobot/motors/motors_bus.py`程式碼中所有`num_retry`都改成99，特別是報錯行對應的

![圖片展示的是LeroBot專案中`motors_bus.py`程式碼檔案內容。檔案中`MotorsBusABC`類的`write`方法被高亮顯示，其中`num_retry`變數被修改為`99`。該圖片與文件中「伺服馬達通訊問題1」部分相關，對應解決方案中提到的把`lerobot/src/lerobot/motors/motors_bus.py`程式碼中所有`num_retry`都改成99的操作，特別是報錯行對應的程式碼部分。](../../en/images/d65-04.png)

## 伺服馬達通訊問題2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![圖片展示的是在macOS系統下，使用zsh終端機執行命令列操作的介面。終端機中顯示了多個檔案路徑及程式碼行號，如`/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`等。其中，`/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py`檔案的第587行程式碼引發`ConnectionError`，提示在id=1上寫入`Torque_Enable`失敗，且無狀態包。該圖片與文件中「伺服馬達通訊問題2」內容相關，直觀呈現了報錯時的程式碼執行情況。](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![圖片展示的是在macOS系統下，使用zsh終端機執行命令列操作的介面。終端機顯示了多個檔案路徑及程式碼行號，如`/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`等。其中，`/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot 自動生成](../../en/images/d65-06.png)
</column>
</grid>

解決方法：重新標定機械臂
