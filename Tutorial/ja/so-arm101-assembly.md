[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | 日本語 | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>SO-ARM101 ロボットアームキット 組立チュートリアル</title>

<callout emoji="💡">
注：組み立て済みのアームをお持ちの場合は、このチュートリアルをスキップしてください
</callout>

## Follower アームの 3D プリント部品

![この画像は、SO-ARM101 ロボットアームを組み立てるために必要な Follower アームの 3D プリント部品を示しており、明るい木目の表面に白い PLA 樹脂部品がすべて並べられています。部品には、さまざまな形状のコネクタ、格子状のフォーク構造、穴の開いたベース型の部品、特殊な形状のフォーク状サポートアームなどが含まれ、チュートリアルの「Follower アームの先端はグリッパである」という点と一致しています。これらの部品は、アームの Follower アームの基本成形部品であり、サポート除去のステップで扱う対象物で、チュートリアルで紹介されている Follower アームの 3D プリント部品に直接対応しています。](../en/images/d09-01.jpg)

## Leader アームの 3D プリント部品

![この画像は、SO-ARM101 ロボットアームの 3D プリント部品を示しています。フレーム内には、さまざまな黒い 3D プリント部品が整然と並べられ、一部の部品の縁には青い線があります。これらの部品には、Leader アームと Follower アームの構造部品（グリッパ、ハンドル、トリガーなど）やコネクタが含まれます。この画像は、文書の「Leader アームの 3D プリント部品」のセクションに対応し、3D プリント部品の外観を視覚的に示し、後の残ったサポートの除去やサーボの見分けのステップの参考を提供しています。](../en/images/d09-02.jpg)

Leader アームと Follower アームは非常に似ており、先端だけが異なります

Leader にはハンドルとトリガーがあり、Follower にはグリッパがあります

## 3D プリント部品の残ったサポートを除去する

すべての穴、開口部、スロット、格子を確認してください。特に麻雀の「五筒」に似た5つの穴に注意してください

このステップは非常に重要です。そうしないと、後でネジを締め込めなくなります

## 4種類のサーボを見分ける

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">大型</td><td vertical-align="middle">小型</td><td vertical-align="middle">電圧 (V)</td><td vertical-align="middle">ギア比</td><td vertical-align="middle">アーム関節</td><td vertical-align="middle">数量</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Follower の全関節</td><td vertical-align="middle">6</td></tr></tbody></table>

> ギア比とは「モータ回転数 : サーボ出力軸回転数」の比です。たとえば 1:345 は、出力軸が1回転するのにモータが345回転することを意味します。
> 
> ギア比が高いと、ギアトレインを通じてトルクが倍増するため、より重い負荷（たとえば Follower アーム）を駆動できます
> 
> ただし同時に、出力軸はよりゆっくり回転します（「減速」されているため）
> 
> 関節を手で動かすのにもより力が必要になります

以下は本プロジェクトのすべてのサーボのモデルとギア比です。下線部がその番号です

![この画像は、アームで使用するサーボのモデル、電圧、ギア比を示しています。左が Leader アームで、C046（7.4V、1:147）と C044（7.4V、1:191）の2つのモデルがあります。右が Follower アームで、C001（7.4V、1:345）と C047（12V、1:345）の2つのモデルがあります。この画像は文脈と密接に関連しており、文脈では Leader アームと Follower アームのサーボのモデル、電圧、ギア比を詳しく紹介しています。この画像はこれらの重要な数値を視覚的に示し、読者がサーボ構成をよりよく理解できるよう支援しています。](../en/images/d09-03.png)

![この画像は「STS3215」と表示された4箱のサーボを示しています。各箱には「SPECIFICATION」という語が印刷され、トルク、速度、寸法などのパラメータが含まれています。たとえばトルクは 9.2kg·cm/127.98oz·in(6V) です。STS3215-C001 のトルクは 12.5kg·cm/173.88oz·in(6V)、STS3215-C046 のトルクは 16kg·cm/220.58oz·in(7V) です。これらのサーボは、アームの Follower アームのすべての関節に使用されるモデルで、文書で紹介されている Follower アームに対応し、後の組み立てステップでサーボの取り付けに使用されます。](../en/images/d09-04.jpg)

## 2種類の電源アダプタを見分ける

5V 6A 30W 電源アダプタ：7.4V サーボ（Leader アーム）に給電、黒色

12V 5A 60W 電源アダプタ：12V サーボ（Follower アーム）に給電、白色

## Feetech サーボデバッグツールのダウンロード

### Windows PC

https://gitee.com/ftservo/fddebug

[`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z) をダウンロードして解凍し、中の exe プログラムを実行します

### Ubuntu と Mac（アーカイブにチュートリアルが含まれています）

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![この画像は、SO-ARM101 ロボットアームキットの組立チュートリアルの補助的な説明図で、電源アダプタの見分けのセクションに対応しています。STS3215-C001 と STS3215-C018 という2つのサーボモデルとその取り付け位置を示し、STS3215-C004 などのサーボにもラベルを付けており、アームの異なる関節に対応しています。図にはこれら2つのサーボのパラメータ（回転速度、ストールトルク、サーボ精度、保護機能、パラメータフィードバックを含む）も記載されており、アームの組み立て時のサーボの選択と取り付けの参考を提供しています。](../en/images/d09-05.jpg)

**Pro 版：Leader アームは 5V6A 電源アダプタを、Follower アームは 12V5A 電源アダプタを使用します**

サーボ ID の設定、サーボ角度のキャリブレーション、組み立ては事前に行う必要があります。[公式組立チュートリアル](https://huggingface.co/docs/lerobot/so101)を参照してください

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# ステップ1：サーボ ID の設定とサーボホーンの取り付け（サーボ5を除く）

<grid>
<column width-ratio="0.500000">
![この画像は Feetech 上位デバッグツールのインターフェースを示しています。インターフェースには「Debug」「Program」「Upgrade」の3つのタブがあり、現在は「Program」が選択されています。主な情報：1. 通信設定では、ポート番号は COM6、ボーレートは 1000000 です。2. サーボ操作では、同期書き込み、非同期書き込み、トルク出力がすべてチェックされています。3. サーボフィードバックでは、電圧、電流、温度、位置などのパラメータがすべて 0 を示しています。4. サーボ検索では、id 1 が選択され、モデルは ST53215 です。この画像は、上記で説明したサーボ ID の設定やサーボホーンの取り付けなどのデバッグ操作に関連し、デバッグツールのインターフェースを示しています。](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![この画像は、サーボ ID を設定するために使用される Feetech 上位デバッグツールのインターフェースを示しています。インターフェースには「Debug」「Program」「Upgrade」の3つのタブがあり、現在は「Program」が選択されています。「Center calibration」エリアでは、ID 番号が 4 で、右側に「Save」ボタンがあります。インターフェースの左側にはサーボの ID、モデルなどの情報が表示されています。この画像は、文書の「ステップ1：サーボ ID の設定とサーボホーンの取り付け（サーボ5を除く）」の内容に関連し、サーボ ID 設定操作のインターフェースを示し、ID 番号をどこで設定するかを視覚的に示しています。](../en/images/d09-07.png)
</column>
</grid>

1. Feetech 上位デバッグツールを開き、COM ポートを選択し、ボーレートを100万に設定して「Open」をクリックします
2. 「Search」をクリックし、「STS3215」が表示されたら「Stop」をクリックしてから「STS3215」をクリックします
3. 上部で「Debug」を選択します。スライダーをドラッグしてサーボを回転させるか、「Scan」をクリックして前後に動かすことができます。サーボが正常に動作することを確認します
4. 上部で「Program」を選択します
5. 「Center calibration」をクリックして、サーボの現在の回転軸位置を中心（0-4095）に設定します
6. 「ID」をクリックし、右下隅で対応するサーボの ID 番号を設定し、「Save」をクリックします。番号は英字を含まない半角アラビア数字であることに注意してください。
7. サーボと制御ボードを接続しているケーブルを外します
8. サーボケーブルをサーボに差し込みます

サーボ1は2本のケーブルを接続します。他のサーボは今のところ1本のケーブルのみ接続します

![この画像は、SO-ARM101 アームキットの組み立てにおけるサーボの取り付けを示しています。フレーム内には Follower アームと Leader アームがあり、Follower アームには 123456、Leader アームには 123456 の番号が付けられています。サーボには 1:345、1:191、1:147 のギア比がラベル付けされています。下には制御ボードがあり、白と黒の2本のケーブルが接続されています。この画像は上記の組み立て手順に関連し、サーボの取り付け位置と番号を視覚的に示し、組み立て者がサーボと制御ボードを正確に対応させるのを支援しています。](../en/images/d09-08.png)

<callout emoji="💡">
繰り返します：各サーボの関節 ID とギア比が **SO-ARM101** と正確に一致していることを確認してください。
</callout>

バス上の各モータは一意の ID を持ちます。新しいモータは通常、デフォルト ID の `1` で出荷されます。モータとコントローラ間の通信を確実に機能させるには、まず各モータに一意の ID を設定する必要があります。さらに、バス上のデータ伝送速度はボーレートによって決まります。互いに通信するには、コントローラとすべてのモータに同じボーレートを設定する必要があります。このアームのサーボはボーレート 100000 を使用します。

これを行うには、まずコントローラを各モータに順番に接続して設定できるようにする必要があります。これらのパラメータはモータ内部メモリ（EEPROM）の不揮発領域に書き込まれるため、この作業は一度だけ行えば済みます。

別のロボットからモータを流用する場合も、ID とボーレートが一致しない可能性があるため、このステップが必要になることがあります。

以下の動画は、モータ ID を設定する手順の流れを示しています。

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Feetech サーボ上位ツールを使ってサーボ ID を設定し、中心をキャリブレーションします。ID は 1 から 6 まで設定します！

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu と Mac

<callout emoji="💡">
Feetech サーボ上位ツールが必要な場合は、上記の[Feetech サーボデバッグツール](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb)を参照してください
</callout>

まず [LeRobot 公式インストール](https://huggingface.co/docs/lerobot/installation)ページに従って環境構築を完了してください

<callout emoji="💡">
仮想環境を有効化し、対応する src/lerobot ディレクトリに移動するのを忘れないでください
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. アームの USB ポートを見つけます。各アームの正しいポートを見つけるには、ユーティリティスクリプトを2回実行します：

```Plain Text
lerobot-find-port
```

Leader アームのポートを特定する際の出力例（たとえば Mac では `/dev/tty.usbmodem575E0031751`、Linux では `/dev/ttyACM0` などの可能性があります）：

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

Follower アームのポートを特定する際の出力例（たとえば `/dev/tty.usbmodem575E0032081`、Linux では `/dev/ttyACM1` などの可能性があります）：

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
USB コネクタを必ず外してください。そうしないとポートが検出できません。
</callout>

2. USB ケーブルで PC を Follower アームのサーボドライバボードに接続し、電源を入れます。次に以下のコマンドを実行します。コマンド内の --robot.port=/dev/ttyACM0 を、見つけたポートに変更してください。たとえば、見つけたポートが /dev/ttyACM1 の場合、--robot.port=/dev/ttyACM1 に変更します

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

以下の出力が表示されます。

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

指示に従って、グリッパのサーボを接続します。サーボドライバボードに接続されているサーボがそれだけであり、そのサーボがまだ他のサーボに接続されていないことを確認してください。**[Enter]** を押すと、スクリプトがそのサーボの ID とボーレートを自動的に設定します。ID は 6 から 1 へ設定されます！

その後、以下が表示されます：

```Python
'gripper' motor id set to 6
```

次に表示される出力は：

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**注** 指示に従い、各サーボについて上記を繰り返してください。
前のサーボと同様に、ドライバボードに接続されているサーボがそれだけであり、そのサーボ自体が他のサーボに接続されていないことを確認してください。
</callout>

毎回 **Enter** を押す前に、必ずケーブルの接続を確認してください。たとえば、回路基板を扱っているうちに電源ケーブルが緩むことがあります。

すべてのステップを完了すると、スクリプトは自動的に終了し、サーボが使用可能になります。次に、各サーボの3ピンコネクタを順番に接続し、最初のサーボ（ID 1 の「shoulder pan」サーボ）のケーブルをドライバボードに接続します。ドライバボードをアームのベースに取り付けることができます。

Leader アームについても同じステップを繰り返します。

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# ステップ2：組み立て

<callout emoji="💡">
- Follower アームの組み立て手順は Leader アームとほぼ同じです。唯一の違いは、ステップ12の後にエンドエフェクタ（グリッパとハンドル）を別の方法で取り付ける点です。
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
サーボドライバボードの取り付け：まず4本の真鍮スタンドオフを取り付け、次にドライバボードを4本の M2.5\*8 ネジで固定します
</callout>

<grid>
<column width-ratio="0.525947">
![4本の真鍮スタンドオフを取り付ける](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![M2.5*8 ネジでサーボドライバボードを固定する](../en/images/d09-10.webp)
</column>
</grid>

![アームに取り付けて配線する](../en/images/d09-11.png)

**Pro 版：黒い Leader アームは 5V6A 電源アダプタを、白い Follower アームは 12V5A 電源アダプタを使用します**







# Web UI でサーボ ID と中心キャリブレーションを設定する

https://bambot.org/feetech.js?lang=zh

1. サーボのモデルに応じて 0 または 1 を入力し、「Connect」をクリックします

![この画像は、アームキットの組立チュートリアルにおける「Connect」インターフェースを示しています。インターフェースの左側には「Connect」という語があり、右側には「1,000,000 bps (Index 0)」に設定された「Baud rate」ドロップダウンと、「0」に設定された「Protocol end (0=STS/SMS, 1=SCS)」の入力ボックスがあり、入力ボックスの横の数字「1」が赤い枠で囲まれています。下には緑色の「Connect」ボタンがあり、その横の数字「2」が赤い枠で囲まれています。一番下には「Status: Disconnected」と表示されています。この画像は、上記の「サーボのモデルに応じて 0 または 1 を入力し、『Connect』をクリックします」という内容に対応し、接続操作の設定を視覚的に示しています。](../en/images/d09-12.png)

2. ID 1\~6 のサーボをスキャンし、スキャン結果の FOUND で対応する ID のサーボを確認します。たとえば画像ではサーボ ID 1 が見つかっています

![この画像は、SO-ARM101 アームキットの組立チュートリアルにおける「Scan servos」ステップのインターフェースを示しています。インターフェースの上部には「Start ID」と「End ID」の入力ボックスがあり、現在は開始 ID が 1、終了 ID が 6 です。下には「Start scan」ボタンがあります。スキャン結果では、ID 1〜6 をスキャンしてもサーボが見つからず、「Exception: No status packet! Error code: 0」と報告されています。この画像は文脈と密接に関連し、サーボをスキャンする際のインターフェースと結果を視覚的に示し、ユーザーがサーボのスキャン状態を理解できるよう支援しています。](../en/images/d09-13.png)

3. ID 設定と中心キャリブレーション

① 現在のサーボ ID の入力を、スキャンしたサーボの ID に設定します

② 「ID management」に数値を入力し、「Change ID」をクリックして ID を設定します

③ 中心キャリブレーション（STS3215 サーボの中心は 2047、SCS0009 サーボの中心は 511）

STS サーボ：「Position control」に 2047 を入力し、「Set」をクリックします

SCS サーボ：「Position control」に 511 を入力し、「Set」をクリックします

![この画像は単一サーボの制御インターフェースを示しています。現在のサーボ ID は 1 です。ID management に数値 1 を入力して「Change ID」をクリックすると、「Success: ID changed to 1」というメッセージが表示されます。Position Control の値は 2047 で、「Set」ボタンをクリックすると適用されます。この画像は「ID 設定と中心キャリブレーション」という文脈に関連し、ID 設定操作のインターフェースを視覚的に示し、ユーザーが「ID management」に数値を入力して ID を設定する方法や、「Position control」に中心値を入力して「Set」をクリックして完了する方法を理解できるよう支援しています。](../en/images/d09-14.png)
