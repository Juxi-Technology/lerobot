[English](../../en/basics/lerobot-datasets-on-huggingface.md) | [简体中文](../../zh-hans/basics/lerobot-datasets-on-huggingface.md) | [繁體中文](../../zh-hant/basics/lerobot-datasets-on-huggingface.md) | [Deutsch](../../de/basics/lerobot-datasets-on-huggingface.md) | [Español](../../es/basics/lerobot-datasets-on-huggingface.md) | [Français](../../fr/basics/lerobot-datasets-on-huggingface.md) | [Italiano](../../it/basics/lerobot-datasets-on-huggingface.md) | 日本語 | [한국어](../../ko/basics/lerobot-datasets-on-huggingface.md) | [Português (BR)](../../pt-br/basics/lerobot-datasets-on-huggingface.md) | [Português (PT)](../../pt-pt/basics/lerobot-datasets-on-huggingface.md)

# HuggingFace 上の LeRobot データセット

## LeRobot 形式のオープンソースデータセット

https://huggingface.co/blog/lerobot-datasets#what-makes-a-good-dataset

![この画像は「昨年アップロードされた LeRobot データセットの累積数」というタイトルの折れ線グラフです。横軸は 2023年12月1日から 2024年5月1日までの日付を、縦軸は 0 から 3500 までのデータセット数を示しています。青い線は上昇傾向にあり、昨年アップロードされた LeRobot データセットの数が継続的に増加したことを示しています。このグラフは、HuggingFace 上の LeRobot データセットの紹介に関連し、アップロードされたデータセット数の推移を視覚的に示しています。](../../en/images/d05-01.png)

![この画像は「最も頻度の高い10種類のロボットのデータセット数」というタイトルの棒グラフです。横軸はロボットの種類を左から右へ so100、loch、ar25_manual、moos、unknown、aloha、alohastationary、transen_al_solo、orix、alohastationary と示しています。縦軸はデータセット数を示しています。so100 が圧倒的に多く、1750 を超えており、他のロボットの種類は比較的少なく、たとえば aloha と alohastationary はそれぞれ 100 未満です。このグラフは、LeRobot 形式のオープンソースデータセットの紹介に関連し、最も頻度の高い10種類のロボットのデータセット数を示しています。](../../en/images/d05-02.png)

![この画像は LeRobot データセットのソース階層を示しています。最上部は「Real-World Data（実世界データ）」で、実環境のロボットの画像を含むオレンジ色の三角形として示されています。中間層は「Synthetic Data（合成データ）」で、仮想環境のロボットの画像を含む緑色の三角形として示されています。最下部は「Web Data & Human Videos（Web データと人間の動画）」で、Common Crawl、Reddit、Wikipedia、Epic Kitchen といったソースラベルを含む青い台形として示されています。この画像は、LeRobot データセットのソースの紹介に関連し、データセットがどのように構成されるかを視覚的に示しています。](../../en/images/d05-03.png)

## いくつか興味深い LeRobot データセット



色ごとにゼリービーンズを仕分ける

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FMarkusWuenstel%2Fso101-sort-color-joint-angles-preprocessed%2Fepisode_0



レゴブロックを箱に入れる

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flerobot%2Fsvla_so101_pickplace%2Fepisode_0



テーブルを片付ける

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fyouliangtan%2Fso101-table-cleanup%2Fepisode_0



ブロックを押す

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FIPEC-COMMUNITY%2Flanguage_table_lerobot%2Fepisode_17



T字型の部品を正しい位置に置く（シミュレーションデータ）

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flerobot%2Fpusht%2Fepisode_15



引き出しを閉じる

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Flirislab%2Fclose_top_drawer_teabox%2Fepisode_1

チェスの対局 — ハイライトされたマスに駒を置く

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2FChojins%2Fchess_game_001_blue_stereo%2Fepisode_1

動物のブロックを並べる

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fpierfabre%2Fchicken%2Fepisode_6



さまざまな家事

https://huggingface.co/spaces/lerobot/visualize_dataset?path=%2Fcadene%2Fdroid_1.0.1%2Fepisode_13
