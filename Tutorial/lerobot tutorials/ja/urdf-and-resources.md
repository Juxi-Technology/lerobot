[English](../en/urdf-and-resources.md) | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | [Español](../es/urdf-and-resources.md) | [Français](../fr/urdf-and-resources.md) | [Italiano](../it/urdf-and-resources.md) | 日本語 | [한국어](../ko/urdf-and-resources.md) | [Português (BR)](../pt-br/urdf-and-resources.md) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>URDF ファイルと参考リソース</title>

# Lerbot 公式 [URDF ファイル](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf)



## URDF Studio

https://urdf.d-robotics.cc/



## ROS2 シミュレーション制御（ご自身で実装）

https://github.com/holmsslk/so-arm-moveit-hardware



## LeRobot 公式グラフィカルインターフェース

https://github.com/huggingface/leLab

LeLab は、LeRobot のワークフロー全体 — キャリブレーション、テレオペレーション、記録、学習、再生 — を単一のブラウザインターフェースにまとめた Web アプリです。ロボットアームを接続してアプリを開くだけで、すぐに作業を始められます。面倒なコマンドライン作業もキーボード入力も不要です。

🤗 LeRobot のネイティブな Web エントリーポイントで、新規ユーザーが「箱から出してすぐ」の状態から「最初のポリシーを学習する」までを数分で行えるように設計されています。

🤗 コマンド1つですべてのインストールと実行が完了します。



# スマートフォンから Follower アームを制御する

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## クラウドロボティクス開発：AWS 上の ROS 2 デバイスと Isaac Sim LeRobot シミュレーションおよびデータストリーミング

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## Web UI でサーボ ID と中心キャリブレーションを設定する

https://bambot.org/feetech.js?lang=zh

1. サーボのモデルに応じて 0 または 1 を入力し、「Connect」をクリックします

![この画像は、Web UI でサーボ ID と中心キャリブレーションを設定するための接続インターフェースを示しています。インターフェースには「Connect」セクションがあり、ボーレートのドロップダウンが現在「1,000,000 bps (Index 0)」に設定され、プロトコルエンドのドロップダウンが現在「0=STS/SMS」に設定され、「Connect」ボタンがあります。インターフェースの下部には「Status: Disconnected」と表示されています。この画像は文脈と密接に関連しています。サーボのモデルに応じて 0 または 1 を入力して「Connect」をクリックした後、ID 1\~6 のサーボがスキャンされ、対応する ID のサーボを確認します。これはそのフローにおける重要なインターフェースです。](../en/images/d68-01.png)

2. ID 1\~6 のサーボをスキャンし、スキャン結果の FOUND で対応する ID のサーボを確認します。たとえば画像ではサーボ ID 1 が見つかっています

![この画像は、Lerbot 公式 URDF Studio のサーボスキャンインターフェースを示しています。インターフェースには開始 ID が 1、終了 ID が 6 と表示され、その下に「Start scan」ボタンがあります。スキャン結果では、ID1 をスキャンすると ID1239 が見つかり、ID2 から ID6 をスキャンするとそれぞれ「ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0」と報告されています。この画像は、文脈で説明されている Lerbot 公式 URDF Studio のサーボスキャン操作に関連し、スキャンのプロセスとその結果を視覚的に示しています。](../en/images/fix-01.png)

3. ID 設定と中心キャリブレーション

① 現在のサーボ ID の入力を、スキャンしたサーボの ID に設定します

② 「ID management」に数値を入力し、「Change ID」をクリックして ID を設定します

③ 中心キャリブレーション（STS3215 サーボの中心は 2047、SCS0009 サーボの中心は 511）

STS サーボ：「Position control」に 2047 を入力し、「Set」をクリックします

SCS サーボ：「Position control」に 511 を入力し、「Set」をクリックします

![この画像は Lerbot の単一サーボ制御インターフェースを示しています。「Current servo ID」は 1 と表示されています。その下の「ID management」には数値 1 と「Change ID」ボタンがあり、その下に「Success: ID changed to 1」というメッセージがあります。Position Control エリアには「Read position」ボタンがあり、位置 2047 が表示され、その隣に「Set」ボタンがあります。この画像は、文書の「ID 設定と中心キャリブレーション」のセクションに関連し、サーボ ID の設定と中心のキャリブレーションを行うためのインターフェースを視覚的に示し、ユーザーが Lerbot でこれらの設定を実行する方法を理解できるよう支援しています。](../en/images/d68-02.png)
