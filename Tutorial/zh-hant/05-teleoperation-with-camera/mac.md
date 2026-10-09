[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | 繁體中文 | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Mac電腦

## 連接攝影機和電腦

```Shell
lerobot-find-cameras opencv
```

![圖片展示了Mac電腦連接攝影機後的偵測結果。畫面中列出兩個 自動產生的兩個攝影機資訊，分別是外接的攝影機和Mac內建的前置攝影機。外接攝影機的Fps為60.00024，內建攝影機的Fps為30.0。該圖片與文件中介紹Mac電腦連接攝影機和電腦的內容相關，直觀呈現了連接後攝影機的偵測情況，協助使用者瞭解攝影機的類型、ID、後端API等資訊，以及各攝影機的影格率。](../../en/images/d31-01.png)

## 一個攝影機，遠端操作並顯示攝影機畫面

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

執行後啟動遠端操作

會開啟rerun.io畫面，即時顯示各個伺服馬達關節的軌跡，以及攝影機即時畫面

並將影像儲存至`~/用户名/outputs/captured_images`目錄

![圖片展示了執行後啟動遠端操作時開啟的rerun.io畫面。畫面左側是多個伺服馬達關節軌跡的圖表，以曲線形式呈現不同關節的運動情況。畫面右側即時顯示了攝影機捕捉的室內場景，能看到桌子、椅子和一些物品。畫面下方還有一些條狀資訊。這張圖片與上下文緊密相關，直觀呈現了執行遠端操作後伺服馬達關節軌跡及攝影機即時畫面的情況，同時也體現了影像會儲存至指定目錄這一功能。](../../en/images/d31-02.png)

## 多個攝影機，遠端操作並顯示攝影機畫面

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 1920, height: 1080, fps: 30, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

![圖片展示了rerun.io畫面，用於遠端操作並顯示多個攝影機畫面。畫面中左側為攝影機即時畫面，顯示了桌面上的物品；右側是資料圖表，展示了不同關節的軌跡，如observation_wip等。畫面底部有Streams區域，列出多個關節資料。右上角有資料資訊，如Application ID、Source IP等。該圖與文件中「多個攝影機，遠端操作並顯示攝影機畫面」內容對應，直觀呈現了遠端操作時畫面和資料展示情況。](../../en/images/d31-03.png)
