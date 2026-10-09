[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | 日本語 | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# Hugging Face アカウントの登録（任意）

## 中国国内向けの HuggingFace ミラーを設定する

- Ubuntu

```Shell
sudo nano ~/.bashrc

# ファイルの末尾にこれを追加する
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# 出力
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# ファイルの末尾にこれを追加する
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# 出力
# https://hf-mirror.com
```



## トークンの作成

https://huggingface.co/settings/tokens

![この画像は Hugging Face プラットフォームのインターフェースで、左側にユーザーのアバターとプロフィール情報エリア、右側にモデルとデータセットの内容があります。右側では赤い矢印が「Settings」の下にある「Access Tokens」オプションを指しています。文脈では、トークンを作成した後に上下キーで選択してキーを貼り付ける必要があると述べられており、この画像はプラットフォーム上で「Access Tokens」がどこにあるかを視覚的に示し、トークン作成後に記録するステップに関連し、トークン作成後に関連する権限を設定するためのインターフェースです。](../../en/images/d34-01.png)

![この画像は Hugging Face プラットフォームの Access Tokens ページを示しています。左のナビゲーションバーでは「Access Tokens」オプションが選択されています。右側には User Access Tokens の情報として、名前、値、最終更新日、最終使用日、権限が表示されています。右上には赤い矢印で強調された「Create new token」ボタンがあります。この画像は「トークンの作成」セクションに関連し、新しいトークンを作成する場所を視覚的に示し、Hugging Face でトークンを作成する具体的なページの理解を助けます。](../../en/images/d34-02.png)

![この画像は Hugging Face プラットフォームで新しいアクセストークンを作成するインターフェースを示しており、ページタイトルは「Create new Access Token」です。3 つの項目を設定する必要があります。すなわち「Write」という名前のトークンタイプを選び、名前を「so-arm101」に設定し、そして「Create token」ボタンをクリックします。これらの操作は赤枠と番号 1、2、3 で示され、書き込み権限を持つトークンを作成するようユーザーを導きます。これはトークンを作成する手順に対応し、Hugging Face を連携させるために必要なキーを取得する重要なステップです。](../../en/images/d34-03.png)

![この画像は Hugging Face アカウントのアクセストークン保存ページです。その中心的な内容は、ポップアップを閉じると二度と表示できなくなり、紛失した場合は再作成する必要があるため、トークンの値を適切に保存するよう促す注意です。ページには生成されたアクセスキー hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx が表示され、名前は so-arm101、権限は write です。赤い矢印で指され赤枠で強調された「Copy」ボタンがあり、トークンをコピーするために使われ、右下には現在の操作を終える「Done」ボタンがあります。この画像は Hugging Face アカウントのトークンを記録または連携するステップに対応します。](../../en/images/d34-04.png)

## トークンの記録

たとえば、私のものは次のとおりです：

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## トークンの連携

```Shell
hf auth login

hf auth whoami
```

![この画像は、コマンドラインで Hugging Face のトークンを使ってログインする様子を示しています。「hf auth login」コマンドを入力すると、プロンプト「? How would you like to log in?」が表示され、「Paste an access token」オプションが示されています。これは「トークンの連携」ステップに関連し、上下キーでキーを選択して貼り付けた後、ログイン画面でログイン方法を尋ねられ、そこでアクセストークンを貼り付けてログインし、Hugging Face のトークン連携を完了できることを示しています。](../../en/images/d34-05.png)

> 上下キーでキーを選択して貼り付けます

![この画像は、コマンドラインで Hugging Face アカウントを操作する様子を示しており、現在有効なトークンが「so-arm101-upload」で、指定されたパスに保存されていることが赤枠で強調されています。コマンドラインではログアウトしてから再びログインしており、システムは Hugging Face へのログインにトークンが必要だと促し、トークンを貼り付けて成功するとトークンの権限が write であることを示し、その後保存を完了し、最後に現在有効なトークン情報を表示しています。この内容は「トークンの連携」ステップに対応します。](../../en/images/d34-06.png)

> 成功画面

## データセットリポジトリの作成

<grid>
<column width-ratio="0.434605">
![この画像は Hugging Face インターフェースのドロップダウンメニューを示しており、上部にはログイン中のユーザーが「juxi-admin」と表示され、メニューには新しいモデル、新しいスペース、新しいバケットなど、いくつかの機能オプションが一覧表示されています。赤枠で強調されたオプションは「New Dataset」で、「データセットリポジトリの作成」ステップに対応します。このオプションはデータセットリポジトリを作成するための入り口であり、これを通じてデータセットリポジトリの作成を完了できます。](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![この画像は Hugging Face でデータセットリポジトリを作成するインターフェースを示しています。「Dataset name」には「so-arm101」が入力され、「License」は「apache-2.0」に設定され、「Public」オプションが選択されており、誰でもこのデータセットを閲覧でき、コミットできるのは自分だけであることを意味します。この画像は「データセットリポジトリの作成」ステップに関連し、設定画面の 1 つを示し、作成時に記入すべき重要事項の理解を助けます。](../../en/images/d34-08.png)
</column>
</grid>

![この画像は Hugging Face プラットフォームの「so - arm101」データセットのページを示しています。上部には検索バーとナビゲーションバーがあり、Models や Datasets などのセクションにアクセスできます。中央にはデータセット情報として、ライセンス apache - 2.0 とファイルサイズ 2.53 kB が表示されています。以下には「Getting started with your dataset」セクションがあり、メタデータを追加してデータセットカードを完成させ、見つけやすさを高めるよう促し、データセットカードを編集するオプションも提供しています。右側には「Copy to bucket」と「Edit dataset card」ボタンがあり、データセットファイルのダウンロードの記録もあります。この画像はデータセットリポジトリの作成に関連し、データセットの管理インターフェースを示しています。](../../en/images/d34-09.png)
