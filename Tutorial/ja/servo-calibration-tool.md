[English](../en/servo-calibration-tool.md) | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | [Deutsch](../de/servo-calibration-tool.md) | [Español](../es/servo-calibration-tool.md) | [Français](../fr/servo-calibration-tool.md) | [Italiano](../it/servo-calibration-tool.md) | 日本語 | [한국어](../ko/servo-calibration-tool.md) | [Português (BR)](../pt-br/servo-calibration-tool.md) | [Português (PT)](../pt-pt/servo-calibration-tool.md)

# So-ARM シリーズ向け STS3215 サーボキャリブレーションツール（オプション）

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**So-ARM 10X シリーズのアーム向けに設計された FTServo サーボの工場出荷キャリブレーションおよび LeRobot キャリブレーション用ツールキット**

> ⚠️ **互換性に関する注意：本システムは現在、Feetech（STS3215 シリーズ）サーボのみに対応しています**。レジスタテーブル、xdat パラメータ形式、ボーレートテーブルはすべて Feetech STS3215 シリーズ向けに設計されています。

> 📜 **由来とクレジット：本ツールは** [**Seeed Studio の Seeed_RoboController**](https://github.com/Seeed-Studio) **プロジェクト**を改変・アップグレードしたもので、もともとは MIT ライセンスの下で公開されていました。元のコア機能を維持しつつ、本プロジェクトでは GUI をリファクタリングし、FT デバッガ、xdat パラメータのバックアップ / 復元、クロスプラットフォーム対応、中国語 / 英語の切り替え、その他の強化を追加しています。

---

## ✨ 機能

| 機能 | 説明 |
|-|-|
| ポートの自動検出 | USB シリアルポートをインテリジェントに検出し、仮想デバイスを除外します |
| クロスプラットフォーム対応 | Windows / Ubuntu / macOS 間で互換 |
| デュアルポート同期 | 左右のシリアルポートが独立して動作し、Leader/Follower のデュアルポート遠隔制御の同期に対応します |
| 中国語 / 英語の切り替え | UI でワンクリックで中国語 / 英語を切り替え、選択は自動的に記憶されます |
| 中心キャリブレーション | サーボの現在位置を 2048 の中心として焼き込みます（EEPROM に永続化） |
| 中心テスト | トルクを有効化してサーボを中心へ移動し、キャリブレーション結果を検証します |
| モータの無効化 | ワンクリックですべてのサーボのトルクを無効化し、手動調整を容易にします |
| 自動スキャン | ID 1〜20 の範囲内のすべてのオンラインサーボを自動検出します |
| 単一サーボ制御 | スライダーで1つのサーボの位置とトルクのオン / オフをリアルタイムに制御します |
| FT デバッガ | シリアル接続、スキャン、パラメータの読み書き、位置制御、ボーレート変更、工場出荷リセット、xdat パラメータのバックアップ |
| xdat パラメータ | 現在のサーボの EEPROM パラメータを保存 / バックアップを開いて復元します |
| LeRobot キャリブレーション | LeRobot 形式の JSON キャリブレーションファイルを生成します |
| キャリブレーションファイルから中心へ移動 | キャリブレーションファイルに基づいてアームを中心へ移動します |

---

## 📚 詳細チュートリアル

### 中国語

| OS | チュートリアル |
|-|-|
| Windows | \[Windows チュートリアル\](docs/zh/Windows教程.md) |
| Linux | \[Linux チュートリアル\](docs/zh/Linux教程.md) |
| macOS | \[macOS チュートリアル\](docs/zh/macOS教程.md) |

### 英語

| OS | ガイド |
|-|-|
| Windows | \[Windows ガイド\](docs/en/Windows.md) |
| Linux | \[Linux ガイド\](docs/en/Linux.md) |
| macOS | \[macOS ガイド\](docs/en/macOS.md) |

---

## 🖥️ インターフェース概要

メインプログラムには3つのタブがあります：

```Plain Text
┌─────────────────────────────────────────────────────────────┐
│  SoARM Series Calibration Tool  [Port1▾] [Port2▾] [🔄]  [🎮Remote][EN]│  ← Top bar
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────┬──────────────────────────────┐ │
│  │ Port1 - Servo Calib.    │ Port2 - Servo Calib.         │ │
│  │  [🔴Disconnected] Cur:… │  [🔴Disconnected] Cur:…      │ │
│  │  Servo1~6 status table  │  Servo1~6 status table       │ │
│  │  [CenterCal][CenterTest]│  [CenterCal][CenterTest]…    │ │
│  └─────────────────────────┴──────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

- **トップバー**：アプリのタイトル、ポート選択ドロップダウン、更新ボタン、遠隔制御ボタン、言語切り替えボタン。
- **🦾 Tab1 Servo Calibration**：左右のパネルのクイック操作（中心キャリブレーション、中心テスト、モータの無効化）とライブステータス。
- **🎚️ Tab2 Single-Servo Control**：スライダーで各オンラインサーボの位置を微調整し、トルクを切り替えます。
- **🔬 Tab3 FT Debugger**：シリアル接続、スキャン、パラメータの読み書き、位置制御、ボーレート / 工場出荷リセット、xdat パラメータのバックアップと復元。

---

## 🚀 クイックスタート

> システムごとの詳細なチュートリアルは \[📚 詳細チュートリアル\](#-详细教程) を参照してください。以下は各システムのポイントです。

### Windows

1. [Python 3.10+](https://www.python.org/downloads/) をインストールします（**Add to PATH** にチェック）
2. 仮想環境を作成し、依存関係をインストールします：

```Bash
cd Juxi_ServoController
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

1. 環境を確認して起動します：

```Bash
python setup.py
python -m src.gui.factory_calibration_tool
```

1. デバイスマネージャーでポート番号（例：`COM3`）を確認し、トップバーで選択します。ポートを手動で指定するには：

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux（Ubuntu / Debian）

1. CJK フォントと依存関係をインストールします：

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ シリアルポートの権限（dialout グループ）を追加します** [必須]：

```Bash
sudo usermod -a -G dialout $USER
# ログアウトして再ログインすると有効になります
```

1. 仮想環境を作成し、依存関係をインストールして起動します：

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. シリアルデバイスは `/dev/ttyUSB0` / `/dev/ttyACM0` です。手動で指定するには：

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/ttyUSB0 --port2 /dev/ttyUSB1
```

### macOS

1. `Homebrew ` で `Python` をインストールします：

```Bash
brew install python
```

1. 仮想環境を作成し、依存関係をインストールして起動します：

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. **⚠️ シリアルポートの命名**：macOS では `/dev/tty.*` ではなく `/dev/cu.usbserial-*`（**推奨、ノンブロッキング**）を使用してください。一覧表示するには：

```Bash
ls /dev/cu.*
```

手動で指定するには：

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### 一般的なコマンドラインツール（GUI 不要）

```Bash
# サーボをスキャン
python -m src.tools.scan_id

# サーボの中心キャリブレーションをすばやく実行
python -m src.tools.servo_quick_calibration

# サーボの中心テスト
python -m src.tools.servo_center_test

# すべてのサーボを無効化
python -m src.tools.servo_disable

# LeRobot 形式のキャリブレーション
python -m src.tools.lerobot_calibrate

# デュアルポート同期の遠隔制御
python -m src.tools.servo_remote_control
```

---

## 📖 使用手順

### 1. サーボの接続と検出

1. USB-シリアルアダプタを通じてアームの制御ボードを接続し、サーボに電源を供給します。
2. GUI を開き、トップバーのドロップダウンでポートを選択します（または `🔄` をクリックして更新）。
3. パネルの上部に `🟢 Connected` が表示され、ID 1〜20 の範囲内のオンラインサーボ（通常は 1〜6）を自動的にスキャンします。

> ポートが使用中と報告された場合は、他のプログラム（シリアルモニタ、終了しなかった以前に開いたツールなど）が使用していないことを確認してください。

### 2. 中心キャリブレーション（現在位置を 2048 に設定）

> キャリブレーションの前に、各関節が目的の「ゼロ / 中心」位置になるように、アームを物理的にポーズさせてください。

1. パネルの **PortX Center Calibration** ボタンをクリックします。
2. プログラムはまずサーボを無効化し、目的の中心へ手動で移動するよう促します。
3. 確認後、プログラムは各サーボについて、EEPROM のロック解除 → キャリブレーションコマンドの書き込み（アドレス 40 に値 128）→ EEPROM の再ロックを実行します。
4. キャリブレーション後、「Center test」で検証します。サーボがその場に留まれば（ほとんど動かなければ）、キャリブレーションは成功です。

### 3. 中心テスト

1. **PortX Center Test** をクリックします。
2. プログラムはトルクを有効化し、すべてのサーボを 2048 へ移動します。
3. サーボが現在位置からほとんど動かなければ、キャリブレーションは正しいです。大きく動く場合は、キャリブレーション値が信頼できないため、やり直す必要があります。

### 4. モータの無効化（手動調整）

- **PortX Disable Motors** をクリックすると、そのポートのすべてのサーボのトルクがオフになり、手で自由に回転できます。
- 単一のサーボについては、**Single-Servo Control** ページでスライダーの下のトルクスイッチを使って、個別にトルクを切り替えます。

### 5. サーボ ID の変更

1. **🔬 FT Debugger** ページに移動し、シリアルポートを接続してサーボをスキャンします。
2. 対象のサーボを選択し、パラメータテーブルの「Servo ID」の値（アドレス 0x05）を変更し、書き込みをクリックします。
3. プログラムはロック解除 → アドレス 5 への書き込み → 新しい ID の検証 → 再ロックを実行します。

> ⚠️ ID を変更する前に、これがバス上の唯一のサーボであることを確認し、ID の競合を避けてください。

### 6. ボーレートの変更 / 工場出荷リセット

- **ボーレートの変更**：FT Debugger ページの「Baud rate / factory reset」エリアで、新しいボーレート（38400〜1000000 bps）を選択して適用します。書き込み後、シリアルのボーレートが自動的に切り替わり、ping で検証されます。失敗した場合は自動的にロールバックします。
- **工場出荷リセット**：サーボが工場出荷時のデフォルト（ID=1、ボーレート=1000000）に戻ります。後で再スキャンしてください。

### 7. xdat パラメータのバックアップと復元

FT Debugger ページの「xdat parameters (EEPROM only)」エリアで：

1. **💾 Save current servo**：現在選択されているサーボの EEPROM パラメータを xdat ファイルに保存します（バックアップ）。
2. サーボのパラメータを自由に変更した後、復元したい場合：
3. **📂 Open xdat**：バックアップファイルを読み込みます。
4. **📤 Restore parameters to servo**：バックアップを現在のサーボの EEPROM に書き戻します。

### 8. デュアルポート同期の遠隔制御

> ⚠️ **方向：ポート1がポート2を制御します**。ポート1（Leader）はサーボ角度を読み取るだけで、ポート2（Follower）が同期して制御されます。

1. トップバーの **🎮 Remote** をクリックします（ポート1が角度を読み取り → ポート2が同じ ID のサーボを同期して制御）。
2. 両方のポートが一致するサーボ ID を持っている必要があり、共通部分にあるサーボのみが同期されます。
3. 同じボタンをもう一度クリックすると停止します。その後、左右のパネルのスキャンスレッドが自動的に再開します。

### 9. LeRobot キャリブレーション（コマンドライン）

```Bash
# Follower アームをキャリブレーション（~/.cache/huggingface/lerobot/calibration/robots/so_follower/ に保存されます）
python -m src.tools.lerobot_calibrate --arm-type follower

# Leader アームをキャリブレーション
python -m src.tools.lerobot_calibrate --arm-type leader
```

流れ：サーボを無効化 → 各関節を中心へ移動して `homing_offset` を記録 → 全行程をゆっくり掃引して `range_min/max` を記録（`wrist_roll` は連続回転関節で、範囲は `[0,4095]` に固定）→ JSON を保存。

キャリブレーションファイルを使って中心へ移動：

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ 注意事項



1. **安全第一**：中心キャリブレーションは EEPROM に永続化されます。キャリブレーションの前に、電源が安定しており、アームが人や物に衝突しないことを確認してください。
2. **電源**：標準の SoARM 101 では DC 5V 5A を推奨します。Pro 版では DC 12V 5A です。電力が不足すると、サーボのステップ抜けや通信障害が発生します。
3. **シリアルポートの排他性**：Windows ではポートが排他的にロックされるため、同じポートを GUI のスキャンスレッドとキャリブレーションのサブプロセスが同時に使用することはできません。ツールは操作前にスキャンスレッドを自動的に停止し、古いプロセスを終了します。手動で繰り返しクリックしないでください。
4. **Linux のシリアル権限**：`/dev/ttyUSB*` / `/dev/ttyACM*` にアクセスするには、ユーザーを `dialout` グループに追加する必要があります（\[Linux チュートリアル\](docs/zh/Linux教程.md)を参照）。
5. **macOS のシリアル命名**：`/dev/tty.*`（ブロッキング、ハングする可能性があります）ではなく `/dev/cu.*`（ノンブロッキング）を使用してください。\[macOS チュートリアル\](docs/zh/macOS教程.md)を参照してください。
6. **ホットプラグ**：USB を抜いた後、プログラムは自動的に再接続を試みます。再度差し込んだ後、`🔄` をクリックしてポート一覧を更新してください。
7. **過熱 / 過電圧保護**：プログラムは電圧と温度を監視します（60°C を超えるとアラーム）。サーボが熱いままの場合は、停止して冷ましてください。
8. **中心キャリブレーションは不可逆**：書き込み後、元のオフセットは上書きされ、元に戻せません。キャリブレーションの前に、まず元の位置を記録してください。
9. **ID 変更のリスク**：書き込みや検証が失敗した場合、プログラムはエラーを報告してスキャンを再開しますが、極端な場合にはサーボが「見失われる」ことがあります。その場合は「Factory reset」を試してください（リセット後、ID は 1 に戻ります）。
10. **エンコーディングの問題**：Windows のコンソールで絵文字が文字化けする場合は、コマンドラインツールを実行する前に `PYTHONIOENCODING=utf-8` を設定してください。ネイティブ UTF-8 の Linux/macOS では通常この問題はありません。

---

## 🛠️ トラブルシューティング

| 症状 | 考えられる原因 | 解決策 |
|-|-|-|
| シリアルポートを開けない / ポートが使用中 | 別のプログラムが使用している | シリアルモニタなどのプログラムを閉じるか、ポートを切り替えてツールを再起動します |
| スキャンでサーボが見つからない | 電力不足 / 配線ミス / ボーレートの不一致 | 電源と配線を確認し、サーボが 1M ボーレートであることを確認します |
| 中心キャリブレーション後にサーボが暴走する | キャリブレーション前に姿勢が正しく設定されていない | 「無効化 → 手動でポーズ → 中心キャリブレーション」をやり直します |
| 温度が上昇しすぎる | 過負荷またはストール | 機構の引っかかりを確認し、速度 / 加速度を下げます |
| ID 変更後にサーボが見つからない | ID の競合または書き込み失敗 | 工場出荷リセットして再スキャンします |
| 遠隔制御が同期しない | 2つのポートの ID が一致していない | Leader ポートと Follower ポートの両方で、同じ ID のサーボがオンラインであることを確認します |

---

## 📁 ディレクトリ構成

```Plain Text
Juxi_ServoController/
├── docs/                    # Per-system tutorials (Chinese/English)
│   ├── zh/                  # Chinese tutorials
│   │   ├── Windows教程.md
│   │   ├── Linux教程.md
│   │   └── macOS教程.md
│   └── en/                  # English tutorials
│       ├── Windows.md
│       ├── Linux.md
│       └── macOS.md
├── src/
│   ├── gui/                  # PySide6 GUI
│   │   ├── factory_calibration_tool.py   # Main tool (dual-port calibration + remote control + language switching)
│   │   ├── ft_debugger.py                # FT debugger (parameter read/write / xdat backup)
│   │   ├── calibration_wizard.py         # LeRobot calibration wizard
│   │   ├── theme_utils.py                # Light theme
│   │   └── language_dialog.py            # Language-selection dialog
│   ├── tools/                # Command-line tools
│   ├── xdat_utils.py         # xdat parameter file read/write
│   ├── i18n*.py / i18n_translations/     # Chinese/English internationalization
│   ├── port_utils.py         # Serial port detection
│   └── calibration_manager.py# LeRobot calibration file management
├── scservo_sdk/              # FTServo servo communication SDK
├── requirements.txt
└── setup.py                  # Environment check script
```
