[English](../en/ros2-simulation.md) | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | [Deutsch](../de/ros2-simulation.md) | [Español](../es/ros2-simulation.md) | [Français](../fr/ros2-simulation.md) | [Italiano](../it/ros2-simulation.md) | 日本語 | [한국어](../ko/ros2-simulation.md) | [Português (BR)](../pt-br/ros2-simulation.md) | [Português (PT)](../pt-pt/ros2-simulation.md)

# ROS2 シミュレーション制御

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

SO-ARM101 6自由度ロボットアーム用の完全な ROS 2 ワークスペースで、ロボット記述、内蔵のハードウェアドライバ、Gazebo シミュレーション、MoveIt 2 の動作計画をカバーしています。

SO-ARM101 は [TheRobotStudio](https://www.therobotstudio.com/) と [LeRobot](https://huggingface.co/lerobot) コミュニティが共同設計した第2世代のオープンソース Follower アームで、6基の STS3215 サーボ、サーボドライバボード、3D プリントの PLA+ 部品を使用しています。

<callout emoji="📌">
**注意：アームには中心キャリブレーションが必要です。すべての関節が可動範囲の中央にある状態で中心キャリブレーションを実行してください**
</callout>

## パッケージ構成

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

対象プラットフォーム：**ROS 2 Humble / Jazzy**。

---

## ROS 2 環境の準備

このプロジェクトをビルドする前に、システムに ROS 2 と関連コンポーネントがインストールされていることを確認してください。

### システム要件

- Ubuntu 22.04（推奨）または 24.04
- 少なくとも 4 GB の RAM
- 実機モードには USB シリアルポートが必要

### 0.1  ROS 2 Humble のインストール

```Bash
# ロケールを設定
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# ROS 2 ソフトウェアリポジトリを追加
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# ROS 2 Humble Desktop をインストール
sudo apt update
sudo apt install ros-humble-desktop
```

### 0.2  ビルドツールと依存関係のインストール

```Bash
# colcon ビルドツール
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  環境変数の設定

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  シリアルポートの権限を設定（実機に必要）

**恒久的な設定（推奨）**：

```Bash
sudo usermod -a -G dialout $USER
# ログアウトして再ログインすると有効になります
```

**一時的な設定（再起動のたびにやり直す必要があります）**：

```Bash
sudo chmod 666 /dev/ttyACM0
```

## ワークスペースのインストール

```Markdown
# ステップ1  ワークスペースを作成
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# ステップ2  ソースコードを配置
cp -r /path/to/SO-ARM101_ROS2 ./

# ステップ3  システム依存関係をインストール
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# ステップ4  すべてのパッケージをビルド
colcon build --symlink-install

# ステップ5  環境を読み込む  ← 新しいターミナルごとに実行してください
source install/setup.bash
```

<callout emoji="💡">
**実機に関する注意** — `so_arm_hardware` パッケージは内蔵されています。追加のドライバをインストールする必要はありません。  
SCS プロトコルを使ってシリアルポート経由で STS3215 サーボと直接通信します。
</callout>

## 視覚的な確認

ここから始めてください — 最も簡単な手順です。コントローラもハードウェアも不要です。

```Bash
#  ターミナル1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

RViz にロボットモデル全体が表示されます。スライダーをドラッグして、各関節が正しく動くことを確認してください。

---

## コントローラのテスト（仮想ハードウェア / Mock モード）

ここでも実機は不要です — すべてメモリ上で動作します。

```Bash
#  ターミナル1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

ログに以下が表示されたら準備完了です：

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**注意**：シミュレーションモードでは2つのコントローラ（`joint_state_broadcaster` と  
`joint_trajectory_controller`）のみが起動します。`gripper_controller` は削除されています。グリッパは  
`joint_trajectory_controller` によって6つの関節すべてと一緒に制御されます。
</callout>

### コントローラの役割

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## MoveIt 動作計画（Mock ハードウェア）

**ターミナルは1つだけ必要です** — MoveIt が内部でコントローラスタックを起動します。

```Bash
#  ターミナル1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

RViz ウィンドウが開いたら：

1. **MotionPlanning** パネルで、**Planning Group → manipulator** を設定します
2. **Start State → `<current>`**、**Goal State → extended** にします
3. **Plan** をクリックし、次に **Execute** をクリックします

利用可能なプリセット姿勢：`open`、`zero`、`extended`、`rest`。

### 4.1  MoveIt インターフェースの操作手順

RViz が起動すると、左側に **MotionPlanning** パネルが表示され、以下の主要なタブがあります：

#### Planning タブ

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Planning パラメータ

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **初回テストのヒント**：安全のため、Velocity と Acceleration を 0.3 に設定して動作を遅くしてください。

#### Scene Objects タブ

- 衝突チェック用の障害物（Box / Sphere / Cylinder）を追加します
- シーンのインポート / エクスポート
- MoveIt は障害物を自動的に回避して計画します

#### Stored States タブ

- よく使うアームの姿勢を保存します
- デフォルトの姿勢：`open`、`zero`、`extended`、`rest`

### 4.2  基本的なワークフロー

#### 方法A：インタラクティブなドラッグ（推奨）

1. 3D ビューで、アーム先端の**インタラクティブマーカー**（色付きの矢印とリング）を見つけます
2. 矢印をドラッグしてエンドエフェクタの位置を平行移動し、リングをドラッグして姿勢を回転させます
3. システムは IK を自動的に解き、関節角度をリアルタイムで更新します
4. **Plan** をクリックして計画された軌道（オレンジ色）を確認します
5. 問題なければ **Execute** をクリックして実行します

> ドラッグがカクつく場合は、`rest` プリセット姿勢から始めてからドラッグしてください。

#### 方法B：プリセット姿勢

1. **Query Goal State** ドロップダウン → `open` / `extended` / `rest` などを選択します
2. **Update** をクリックします
3. **Plan** をクリックします
4. **Execute** をクリックします

#### 方法C：関節角度を手動で設定する

1. **Query Goal State** → **Joints** タブ
2. 各関節のスライダーをドラッグして目標角度を設定します
3. 関節範囲の参考：

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. **Update** をクリックします
2. **Plan** をクリックします
3. **Execute** をクリックします

#### 方法D：ランダムな有効目標

**Random Valid** をクリックして到達可能なランダムな姿勢を生成し、Plan → Execute と進みます。

### 4.3  安全上の注意

1. **初回使用時は速度を落とす**：Velocity / Acceleration を 0.1〜0.3 に設定します
2. **緊急停止**：いつでも Ctrl+C を押してプログラムを終了するか、電源を切ります
3. **関節リミット**：MoveIt は `joint_limits.yaml` の範囲を超えて計画しませんが、それらが正しく設定されていることを確認してください
4. **実機**：実行前にアームの周囲に十分なスペースがあることを確認してください

### MoveIt 設定の概要

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Gazebo シミュレーション

Gazebo シミュレーションでは**4つのターミナルを同時に実行する必要があります**。順序を厳守してください。

### 5.1  Gazebo シミュレーションの起動  （ターミナル1）

```Bash
#  ターミナル1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Gazebo ウィンドウが表示されるまで待ちます。ロボットはしばらく空中に留まった後、着地します。

### 5.2  軌道コントローラのロード  （ターミナル2）

デフォルトでは Gazebo は `forward_position_controller` のみを有効化します。手動で  
`joint_trajectory_controller` に切り替える必要があります：

```Markdown
#  ターミナル2
source ~/so101_ws/install/setup.bash

# ステップA — forward_position_controller をオフにする
ros2 control set_controller_state forward_position_controller inactive

# ステップB — spawner で joint_trajectory_controller をロードして有効化する
ros2 run controller_manager spawner joint_trajectory_controller

# ステップC — 確認する
ros2 control list_controllers
```

期待される出力：

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ 最初に `ros2 control load_controller` を使わないでください！コントローラが  
`unconfigured` 状態になり、spawner がそれを有効化できなくなります。すでに実行してしまった場合は、  
先に `unload_controller` を実行してやり直してください。
</callout>

### 5.3  move_group の起動  （ターミナル3）

```Bash
#  ターミナル3
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py use_sim_time:=True
```

### 5.4  RViz の起動  （ターミナル4）

```Bash
#  ターミナル4
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

RViz の準備ができたら：

1. **Planning Group → manipulator**
2. **Goal State → open**（または `extended`、`rest`）
3. **Plan** をクリックし、次に **Execute** をクリックします

Gazebo のアームの関節がその動きに追従します。

<callout emoji="💡">
**注意**：Humble 版の `gz_ros2_control` における PID ゲインの制限のため、  
Gazebo でグリッパが物理的に開かないことがあります（実行ログには成功と表示されます）。  
Mock モードと実機にはこの問題はありません。
</callout>

### 5.5  ヘッドレスモード（GUI なし）

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  トラブルシューティング：ロード失敗の繰り返し

spawner が `Failed to activate controller` を繰り返し報告する場合は、以下を実行して完全にリセットします：

```Bash
# 1. スタックしたコントローラをアンロード
ros2 control unload_controller joint_trajectory_controller

# 2. forward_position_controller をオフにする
ros2 control set_controller_state forward_position_controller inactive

# 3. 再度 spawn する
ros2 run controller_manager spawner joint_trajectory_controller
```

## 実機

前提条件：SO-ARM101 アームが組み立てられ、サーボドライバボードが USB 経由で PC に接続されていること。

### 6.1  コントローラの起動（オプション）

```Bash
#  ターミナル1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

`so_arm_hardware` プラグインは自動的に：

1. シリアルポートを開きます
2. 6つのサーボ ID（1〜6）をスキャンします
3. すべてのサーボが応答することを確認します
4. トルクを有効化し、現在位置を読み取ります

コントローラの準備ができたら、さらに2つのターミナルを開いて MoveIt を起動します：

```Bash
#  ターミナル2 — move_group
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py
```

```Bash
#  ターミナル3 — RViz
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

### 6.2  MoveIt（コマンド1つでの起動）

> 以下のコマンドは 6.1 を**置き換えます**（両方を同時に実行しないでください。6.1 のコマンドを停止してください）— `demo.launch.py` は内部にコントローラスタックを既に含んでいます。

```Bash
#  ターミナル1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  シリアルポートのトラブルシューティング

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  RViz の表示が実際の姿勢と一致しない

RViz のアームの姿勢が実機と一致しない場合（たとえば関節のオフセットや誤った衝突報告）：

1. サーボが中心キャリブレーション済みであることを確認します
2. `so_arm101.ros2_control.xacro` 内の各関節の `position_offset` を調整します
3. 変換式：`new offset = current offset + (currently displayed rad / 0.00153398)`
4. 変更後に `so_arm101_description` パッケージを再ビルドします

---

## FAQ

### Q1：ビルド時に「package not found」

**A**：すべてのシステム依存関係が正しくインストールされ、ROS 2 環境が読み込まれていることを確認してください：

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### Q2：起動時にシリアルポートへのアクセスで「Permission denied」

**A**：シリアルポートの権限を確認してください：

```Bash
# 一時的な修正
sudo chmod 666 /dev/ttyACM0

# 恒久的な修正（ログアウト後に有効）
sudo usermod -a -G dialout $USER
```

### Q3：MoveIt の計画が「Motion planning start tree could not be initialized」で失敗する

**A**：通常、原因は2つあります：

1. **関節が範囲外** — ログの `FixStartStateBounds` の出力を確認してください。現在の許容値は  
0.3 rad で、超過がその範囲内であれば通ります。そうでない場合は `start_state_max_bounds_error`  
を調整するか、サーボのオフセットを確認してください。
2. **開始状態が衝突している** — ログの `FixStartStateCollision` の出力を確認してください。  
「Unable to find a valid state nearby」が表示される場合、現在の姿勢が自己衝突しています。  
アームが折りたたまれた姿勢（たとえばグリッパが肩に触れている）か、オフセットが正しくない可能性があります。  
`position_offset` を調整して再試行してください。

### Q4：Execute してもアームが動かない

**A**：コントローラの状態を確認してください：

```Bash
ros2 control list_controllers
```

`joint_trajectory_controller` が `active` であることを確認してください。そうでない場合は、再度 spawn します：

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### Q5：RViz の起動が遅い、またはハングする

**A**：これは正常です。起動時に MoveIt は URDF モデル、衝突チェックプラグイン、  
運動学ソルバなどをロードします。初回の起動には約 10 秒かかります。

### Q6：計画された経路が滑らかでない、またはぎくしゃくする

**A**：以下を試してください：

- 別のプランナに切り替える（RViz の Planner ドロップダウンから `RRTConnect` を選択）
- Planning Time を 10 秒に増やす
- 目標がワークスペース内にあることを確認する（`Random Valid` でテスト）

### Q7：Gazebo でグリッパが動かない

**A**：これは Humble 版の `gz_ros2_control` におけるハードコードされた PID ゲインの制限  
（0.1 に固定）で、URDF パラメータでは上書きできません。Execute はログで成功を報告しますが、  
Gazebo の物理シミュレーションではグリッパが開きません。Mock モードと実機にはこの問題はありません。

## 付録：launch パラメータ早見表

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## ディレクトリ構成

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # Python utility library
├── so_arm101_description/          # URDF · controllers · meshes · RViz · MuJoCo
├── so_arm101_moveit_config/        # MoveIt 2 SRDF · planners · launch files
├── so_arm_gz/                      # Gazebo simulation launch
├── so_arm_hardware/                # Built-in SCS serial driver (C++)
└── Simulation/                     # Original CAD URDF (kept for reference)
```
