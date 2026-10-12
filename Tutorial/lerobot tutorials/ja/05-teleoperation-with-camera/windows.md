[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | 日本語 | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Windows コンピューター

## カメラをコンピューターに接続する

```Shell
lerobot-find-cameras opencv
```

![この画像は Windows のコマンドラインウィンドウで、カメラ接続のエラーとデバイス検出の結果を示しています。上部にエラー「ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range」があります。その下には検出されたカメラの一覧があり、Camera #0 と Camera #1 を含み、それぞれの名前、種類、バックエンド API、デフォルトのストリーム設定、形式、ソース、幅、高さ、フレームレートが示されています。下部には「lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0」などのエラーがあります。これは、文書で言及されている「カメラが接続できず、それでも Tencent Meeting でカメラを切り替えると正常に開く」というエラーシナリオに対応し、OpenCV バックエンドのコードを修正する前の実際の実行時エラーのフィードバックです。](../../en/images/d32-01.png)

## カメラ映像を表示しながらのテレオペレーション

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

rerun.io のウィンドウが開き、各サーボ関節の軌道がリアルタイムで表示され、カメラのライブ映像も表示されます

さらに画像は `C:\Users\username\outputs\captured_images` ディレクトリに保存されます

![この画像は rerun.io のウィンドウを示しており、サーボ関節の軌道とライブカメラ映像がリアルタイムで表示されています。左側はブループリントのインターフェースで、「teleoperation」などのオプションがあります。中央は軌道のグラフで、「observation_wrist_rot.pos」などの関節位置データが表示されています。右側はカメラ映像で、ロボット視点のシーンが映っています。右上には「Waiting for data on rerun: http://127.0.0.1:9876/remote...」と表示され、その下にデータソース情報があります。この画像は、rerun.io のウィンドウがカメラ映像をリアルタイムで表示する内容の説明に関連し、その様子を視覚的に示しています。](../../en/images/d32-02.png)

## 以下のエラーが発生した場合

カメラが接続できず、それでも Tencent Meeting でカメラを切り替えると正常に開きます

![この画像は Windows のコマンドラインインターフェースで、カメラ検出の結果を示しています。上部に「Detected Cameras」と、名前、種類、ID、バックエンド API などのカメラ関連情報が表示されています。その下には、lerobot_find_cameras_openpyc の実行時に OpenCV カメラの接続または設定に失敗したというエラーがあり、使用可能なカメラを見つけるために lerobot_find_cameras_opencv を実行するよう促し、カメラを接続できないため画像の保存を中止することを示しています。この画像はカメラ接続問題の文脈に対応し、エラーを視覚的に示しています。](../../en/images/d32-03.png)

`lerobot\src\lerobot\cameras\utils.py` ファイルを修正し、OpenCV バックエンドを `cv2.CAP_SHOW` に変更します

![この画像は、`lerobot\\src\\lerobot\\cameras\\utils.py` ファイル内の `get_cv2_backend()` 関数のコードを示しています。システムが Windows の場合、関数は `int(cv2.CAP_DSHOW)` を返し、Windows で AVFOUNDATION の代わりに MSMF を使用するために使われます。コードには `cv2.CAP_MSMF` に関するコメントや、Darwin（macOS）や Linux など他のシステムの扱い方も含まれています。この画像は、`lerobot\\src\\lerobot\\cameras\\utils.py` ファイルを修正して OpenCV バックエンドを `cv2.CAP_SHOW` に変更する操作に関連し、コード修正の例です。](../../en/images/d32-04.png)

> これは Doubao でも解決できないバグです。ひとえに lerobot ライブラリのラップが深すぎるためで、初心者にとってデバッグは非常に困難です

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## カメラ複数台を接続して、カメラ映像を表示しながらのテレオペレーション

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![この画像は、カメラ映像を使ったテレオペレーションで使用される rerun.io のウィンドウを示しています。左側は軌道のグラフで、observation_wrist_l_pos や observation_wrist_r_pos など複数の関節の軌道データが表示されています。右側は上部がカメラのライブ映像で、下部が Tencent Meeting のウィンドウです。右上には「Waiting for data on rerun: http://127.0.0.1:9678/remote...」と表示されています。この画像は、カメラを複数接続してテレオペレーション中にカメラ映像を表示する内容に関連し、その様子を視覚的に示しています。](../../en/images/d32-05.png)
