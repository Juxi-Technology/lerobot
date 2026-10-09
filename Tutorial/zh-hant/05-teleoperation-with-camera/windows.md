[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | 繁體中文 | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Windows電腦

## 連接攝影機和電腦

```Shell
lerobot-find-cameras opencv
```

![這張圖片是Windows系統的命令列視窗，顯示了攝影機連接相關的錯誤資訊與裝置偵測結果。視窗頂部有報錯提示「ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range」，下方列出了偵測到的攝影機資訊，包括Camera #0、Camera #1的名稱、類型、後端API、預設串流設定、格式、來源、寬高、影格率等內容，底部還有「lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0」等連接失敗的報錯。這段內容對應文件中提到的「攝影機連接不上，但在騰訊會議中切換攝影機，仍然能正常開啟」的報錯場景，是修改OpenCV後端程式碼前的實際執行錯誤回饋。](../../en/images/d32-01.png)

## 遠端操作並顯示攝影機畫面

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

會開啟rerun.io畫面，即時顯示各個伺服馬達關節的軌跡，以及攝影機即時畫面

並將影像儲存至`C:\Users\用户\outputs\captured_images`目錄

![圖片展示的是rerun.io畫面，即時顯示了各個伺服馬達關節的軌跡及攝影機即時畫面。畫面左側為藍圖介面，有「teleoperation」等選項。中間是軌跡圖，顯示了「observation_wrist_rot.pos」等關節位置資料。右側是攝影機畫面，呈現了機器人視角下的場景。畫面右上角顯示「Waiting for data on rerun: http://127.0.0.1:9876/remote...」，下方有資料來源資訊。該圖與文件中介紹rerun.io畫面即時顯示攝影機畫面的內容相關，直觀呈現了畫面效果。](../../en/images/d32-02.png)

## 如果遇到了下面這種報錯

攝影機連接不上，但在騰訊會議中切換攝影機，仍然能正常開啟

![圖片展示的是Windows電腦命令列介面，顯示了攝影機偵測結果。介面上方顯示「Detected Cameras」及攝影機相關資訊，如名稱、類型、ID、後端API等。下方有錯誤提示，指出在執行lerobot_find_cameras_openpyc時，OpenCV攝影機連接或設定失敗，提示執行lerobot_find_cameras_opencv以尋找可用攝影機，且無攝影機可連接，將中止影像儲存。該圖片與文件中遇到攝影機連接不上問題的上下文對應，直觀呈現了報錯情況。](../../en/images/d32-03.png)

修改`lerobot\src\lerobot\cameras\utils.py`檔案，將OpenCV後端改為`cv2.CAP_SHOW`

![圖片展示的是`lerobot\\src\\lerobot\\cameras\\utils.py`檔案中`get_cv2_backend()`函式程式碼。當系統為Windows時，函式返回`int(cv2.CAP_DSHOW)`，用於在Windows上使用MSMF代替AVFOUNDATION。程式碼中還有對`cv2.CAP_MSMF`的註解，以及對Darwin（macOS）和Linux等其他系統的處理方式。該圖片與文件中修改`lerobot\\src\\lerobot\\cameras\\utils.py`檔案，將OpenCV後端改為`cv2.CAP_SHOW`的操作相關，是修改程式碼範例。](../../en/images/d32-04.png)

> 這是一個豆包都無法解決的bug，都怪lerobot程式庫封裝的太深了，初學者小白很難dubug

<figure view-type="Preview">[附件 / Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## 連接多個攝影機，遠端操作並顯示攝影機畫面

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![圖片展示了rerun.io畫面，用於遠端操作並顯示攝影機畫面。畫面左側是軌跡圖，顯示了多個關節的軌跡資料，如observation_wrist_l_pos、observation_wrist_r_pos等。右側上方是攝影機即時畫面，下方是騰訊會議畫面。畫面右上角顯示「Waiting for data on rerun: http://127.0.0.1:9678/remote...」。該圖與文件中連接多個攝影機，遠端操作並顯示攝影機畫面的內容相關，直觀呈現了畫面效果。](../../en/images/d32-05.png)
