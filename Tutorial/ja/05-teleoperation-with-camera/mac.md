[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | 日本語 | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Mac コンピューター

## カメラをコンピューターに接続する

```Shell
lerobot-find-cameras opencv
```

![この画像は、Mac にカメラを接続した後の検出結果を示しています。自動生成された 2 つのカメラ、すなわち外部カメラと Mac 内蔵のフロントカメラが一覧表示されています。外部カメラの Fps は 60.00024、内蔵カメラの Fps は 30.0 です。この画像は Mac へのカメラ接続の内容に関連し、接続後の検出結果を視覚的に示し、各カメラの種類、ID、バックエンド API、フレームレートの理解を助けます。](../../en/images/d31-01.png)

## カメラ 1 台で、カメラ映像を表示しながらのテレオペレーション

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

実行すると、テレオペレーションが開始されます

rerun.io のウィンドウが開き、各サーボ関節の軌道がリアルタイムで表示され、カメラのライブ映像も表示されます

さらに画像は `~/username/outputs/captured_images` ディレクトリに保存されます

![この画像は、実行後にテレオペレーションが開始されたときに開く rerun.io のウィンドウを示しています。左側にはいくつかのサーボ関節の軌道のグラフがあり、異なる関節の動きを示す曲線として表示されています。右側には屋内のシーンのカメラ映像がリアルタイムで表示され、テーブル、椅子、いくつかの物体が見えます。下部には棒状の情報もいくつかあります。この画像は文脈と密接に関連し、テレオペレーション中のサーボ関節の軌道とライブカメラ映像を視覚的に示すとともに、画像が指定されたディレクトリに保存されることも示しています。](../../en/images/d31-02.png)

## カメラ複数台で、カメラ映像を表示しながらのテレオペレーション

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

![この画像は、複数のカメラ映像を使ったテレオペレーションで使用される rerun.io のウィンドウを示しています。左側にはライブカメラ映像があり、机の上の物体が映っています。右側にはデータグラフがあり、observation_wip など異なる関節の軌道が表示されています。下部には、いくつかの関節のデータを一覧表示する Streams エリアがあります。右上には Application ID や Source IP などのデータ情報があります。この画像は「カメラ複数台で、カメラ映像を表示しながらのテレオペレーション」の内容に対応し、テレオペレーション中の映像とデータを視覚的に示しています。](../../en/images/d31-03.png)
