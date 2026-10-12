[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | 日本語 | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# よくある不具合と対処法

## カメラのキャプチャーに失敗する

![この画像は、LeRobot のロボットコードを実行したときのターミナル出力を示しています。`INFO` ログでは OpenCV カメラが開き、Follower が切断されたことが示され、`ERROR` ログでは `camera_opencv.py` ファイル内の `read` 関数が `OpenCVCamera(0) read failed` のために `RuntimeError` を発生させたことが指摘されています。この画像は「カメラのキャプチャーに失敗する」問題に関連し、コード実行時に現れる問題を視覚的に示し、カメラキャプチャー失敗の具体的な原因を説明するのに役立っています。](../../en/images/d65-01.png)

手首カメラのケーブルが緩んでいないか確認してください。特にカメラ側の端は接触不良を起こしやすい箇所です

## カメラが切断される

![この画像は、/opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py コードの実行インターフェースを示しています。上部には時刻やプロセス ID などの情報が表示され、その下には /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py などのコードパスとエラーメッセージ、および「INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.」が表示されています。重要な部分は「raise TimeoutError」と「TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.」で、カメラのキャプチャーが失敗したことを示しています。この画像は「カメラのキャプチャーに失敗する」問題に関連し、エラーを視覚的に示しています。](../../en/images/d65-02.png)

コマンドラインを再起動します

## サーボ通信の問題 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![この画像は以下を示しています。](../../en/images/d65-03.png)

対処法：`lerobot/src/lerobot/motors/motors_bus.py` のコード内にあるすべての `num_retry` を 99 に変更します。特にエラーが出ている行のものを変更してください

![この画像は、LeRobot プロジェクト内の `motors_bus.py` コードファイルの内容を示しています。`MotorsBusABC` クラスの `write` メソッドが強調され、`num_retry` 変数が `99` に変更されています。この画像は「サーボ通信の問題 1」セクションに関連し、`lerobot/src/lerobot/motors/motors_bus.py` のコード内にあるすべての `num_retry` を 99 に変更する、特にエラーが出ている行のものを変更するという対処法に対応しています。](../../en/images/d65-04.png)

## サーボ通信の問題 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![この画像は、macOS の zsh ターミナルでのコマンドラインセッションを示しています。ターミナルには `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py` など、いくつかのファイルパスとコード行番号が表示されています。ファイル `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` の 587 行目で `ConnectionError` が発生し、id=1 に対する `Torque_Enable` の書き込みが失敗し、ステータスパケットがないことが報告されています。この画像は「サーボ通信の問題 2」の内容に関連し、エラー発生時のコードの実行状況を視覚的に示しています。](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![この画像は、macOS の zsh ターミナルでのコマンドラインセッションを示しています。ターミナルには `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py` など、いくつかのファイルパスとコード行番号が表示されています。ここでは、`/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

解決策：ロボットアームを再キャリブレーションします
