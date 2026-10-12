[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | 日本語 | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# デモによるデータセットの収集 — Handshake 200

## HuggingFace にデータセットリポジトリを作成する

https://huggingface.co/new-dataset

![この画像は、HuggingFace で新しいデータセットリポジトリを作成するインターフェースを示しています。「Owner」は TommyZihao、データセット名は「lerobot_zihao_dataset_shake200」、ライセンスは mit に設定され、データセットタイプは「Public」で、誰でも閲覧できる一方、コミットできるのはデータセットの所有者または組織のメンバーだけです。以下には、データセットを作成した後にウェブインターフェースまたは git でファイルをアップロードできることと、下部に「Create dataset」ボタンがあることが記載されています。この画像は HuggingFace でデータセットリポジトリを作成する内容に関連し、データセット作成操作のインターフェースを示しています。](../../en/images/d37-01.png)

## 同名の既存データセットがある場合は削除する

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Shake200 データセットの収集

カメラ 1 台でデータセットを収集する - Mac コンピューター

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

## 収集中

<grid>
<column width-ratio="0.508765">
![この画像は、Mac でデータセットを収集しているときのターミナルインターフェースを示しています。SvtInfo() と SvtInfo() の出力として、バージョン番号、コンパイラ、アーキテクチャが表示されています。また、SvtConfig() の設定パラメーターとして、幅、高さ、フレームレート、プリセットが示されています。下部には「INFO」や「INFO 0」と印された出力があり、たとえば「Starting second pass: moving the moving atom to the beginning of the file」などがあります。この画像は「収集中」の内容に関連し、収集中にターミナルに表示される設定と情報を視覚的に示しています。](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![この画像は、Mac で Open_Duck_Mini_Runtime_2 スクリプトを使ってデータセットを収集しているときのターミナル出力を示しています。SVT などの動画エンコード設定パラメーターとして、gop サイズやキーフレームタイプなどが表示され、動画エンコーダーのバージョンとビルド日も示されています。下部には「Starting second pass: moving the moov atom to the beginning of the file」などの MP4 ファイルのログがあります。この画像はデータセット収集のワークフローに関連し、収集中のターミナルのフィードバックを視覚的に示しています。](../../en/images/d37-03.png)
</column>
</grid>

キーボードの矢印キー操作：  
→（右矢印）現在のエピソードを途中で終了し、次のエピソードへ進みます。  
←（左矢印）現在のエピソードをキャンセルし、録り直します。  
ESC、即座に停止し、動画をエンコードしてデータセットをアップロードします。

## 収集完了 — データセットの保存ディレクトリ

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
