[English](../../en/08-train-model/get-model-weights.md) | [简体中文](../../zh-hans/08-train-model/get-model-weights.md) | [繁體中文](../../zh-hant/08-train-model/get-model-weights.md) | [Deutsch](../../de/08-train-model/get-model-weights.md) | [Español](../../es/08-train-model/get-model-weights.md) | [Français](../../fr/08-train-model/get-model-weights.md) | [Italiano](../../it/08-train-model/get-model-weights.md) | 日本語 | [한국어](../../ko/08-train-model/get-model-weights.md) | [Português (BR)](../../pt-br/08-train-model/get-model-weights.md) | [Português (PT)](../../pt-pt/08-train-model/get-model-weights.md)

# モデルの重みファイルを取得する



```Shell
cd ~/output_lerobot_train/a/checkpoints/last
zip -r ~/ckpt.zip pretrained_model
```

モデルの重みは 20K ステップごとに 1 回保存されます。



`ckpt.zip` アーカイブを右クリックしてダウンロードし、ローカルのコンピューターに解凍します














## 握手

```Shell
# 指定した学習ステップで保存されたモデル
# cd ~/output_lerobot_train/shake/diffusion/checkpoints/005000

# 最新のモデル
cd ~/output_lerobot_train/shake/wallx/checkpoints/last
zip -r ~/ckpt.zip pretrained_model
```
