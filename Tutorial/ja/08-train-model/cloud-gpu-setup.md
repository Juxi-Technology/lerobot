[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | 日本語 | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# クラウド GPU 学習環境の構成

## お使いのコンピューターのネットワークプロキシを無効にする

そうしないと、Jupyter のコマンドラインを開けない場合があります

## クラウド GPU プラットフォーム Featurize にログインする

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## クラウド GPU インスタンスを起動する

<grid>
<column width-ratio="0.597692">
![この画像は、Featurize プラットフォームのクラウド GPU インスタンス選択画面で、主に構成の異なるクラウド GPU インスタンスの選択肢を示しています。赤い枠で示された選択肢は RTX 5090 のクラウド GPU インスタンスで、2.0 が利用可能、従量課金 3 元/時間、GPU メモリ 32.0 GB、38 コアの AMD EPYC 9354 プロセッサー、メモリ 128 GB と表示されています。その下には「Start Using」と「Reserve」のボタンがあり、赤い矢印が「Start Using」を指しており、文書内の「クラウド GPU インスタンスを起動する」という案内に対応しています。](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![この画像は、Featurize プラットフォームのイメージ選択画面を示しています。「Select Image」タブがあり、その下に「Official Images」「My Images」「Popular Images」の 3 つのサブタブがあります。「Official Images」タブの下では PyTorch 2 のイメージが赤い枠と矢印で強調されており、サイズは 14.5 GB、これまでに 19,001 回使用され、「Official」と表示されています。この画像は文脈と密接に関連しており、クラウド GPU インスタンスを起動した後に「JupyterLab」をクリックしてコードとデータセットをアップロードするという説明に対応しています。このスクリーンショットは、以降の環境構築と構成に用いるイメージ選択ステップでの公式イメージの選択肢を示しています。](../../en/images/d45-02.png)
</column>
</grid>

![この画像は、クラウド GPU インスタンスのコンソールを示しており、文書内の「クラウド GPU インスタンスを起動する」ステップに対応し、インスタンス起動後に利用できる操作を示しています。RTX 5090 インスタンスの構成として、GPU、CPU、メモリ、ディスクの各パラメーターや、インスタンスのレンタル時間、課金方法、費用が表示されています。赤い矢印と赤い枠が「Open Workspace」ボタンを強調しており、JupyterLab の操作へ進み、コードとデータセットをアップロードするためにクリックするようユーザーに促しています。](../../en/images/d45-03.png)

![この画像は、JupyterLab のインターフェースを示しています。左側はファイル管理エリアで、「Instances」「Files」「Terminal」のタブがあり、現在は「Files」タブが選択されています。右側は Launcher エリアで、Notebook、Console、Python 3 (ipykernel) などの選択肢が表示されています。画像内の赤い矢印は左側のファイル管理エリアの「Files」タブを指しており、その場所を強調して文脈（「下の JupyterLab をクリックしてください。左上隅にアップロードボタンがあり、コードとデータセットをアップロードできます」）と呼応しながら、JupyterLab でのファイル関連の操作へとユーザーを導いています。](../../en/images/d45-04.png)

> 下の「JupyterLab」をクリックしてください。左上隅にアップロードボタンがあり、コードとデータセットをアップロードできます

## 環境のインストールと構成

```Shell
conda create -y -n lerobot python=3.12
conda activate lerobot
conda install ffmpeg=7.1.1 -c conda-forge -y
# git clone https://github.com/Seeed-Projects/lerobot.git ~/work/Lerobot
git clone https://github.com/huggingface/lerobot.git
cd lerobot
pip install -e ".[pi]"
pip install wandb --upgrade
# export HF_ENDPOINT=https://hf-mirror.com
hf auth login

# HuggingFace にアップロードせず wandb も不要な場合は、このインストールを省略してください
```

> モデルのインストール時に `training` が不足していた場合は、追加でインストールする必要があります
> 
> `pip install -e ".[training]"`

## wandb にログインする

```Shell
wandb login
Copy and paste the API Key, then press Enter
```

![この画像は、LeRobot プロジェクトの wandb ログイン画面で、ログイン処理の詳細を記録しています。まず wandb ログインを開始し、指定された URL にアクセスして API キーを探し、そのキーを貼り付けて Enter キーを押して送信するようユーザーに促しています。また、netrc ファイルが見つからなかったこと、対応する netrc ファイルのパスに API キーを追加していることが表示され、その後ログインが完了してログイン中のユーザーが tommyzihao として示され、再ログインを強制するコマンドも表示されています。この画像は「wandb にログインする」ステップに対応し、ログインの手順と結果を示しています。](../../en/images/d45-05.png)

## データセットをマウントする

```Shell
Copy the instance download command, something like:
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

データセットは `~` ディレクトリの下に現れます

## 重みの保存頻度を調整する（任意）

`lerobot/src/lerobot/configs/train.py` を開きます

save_freq を 20_000 から 5_000 に変更します

こうすると、学習のより早い段階でモデルの重みファイルが得られます
