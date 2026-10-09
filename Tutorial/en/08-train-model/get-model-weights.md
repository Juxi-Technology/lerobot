English | [简体中文](../../zh-hans/08-train-model/get-model-weights.md) | [繁體中文](../../zh-hant/08-train-model/get-model-weights.md) | [Deutsch](../../de/08-train-model/get-model-weights.md) | [Español](../../es/08-train-model/get-model-weights.md) | [Français](../../fr/08-train-model/get-model-weights.md) | [Italiano](../../it/08-train-model/get-model-weights.md) | [日本語](../../ja/08-train-model/get-model-weights.md) | [한국어](../../ko/08-train-model/get-model-weights.md) | [Português (BR)](../../pt-br/08-train-model/get-model-weights.md) | [Português (PT)](../../pt-pt/08-train-model/get-model-weights.md)

# Obtaining Model Weight Files



```Shell
cd ~/output_lerobot_train/a/checkpoints/last
zip -r ~/ckpt.zip pretrained_model
```

The model weights are saved once every 20K steps.



Right-click to download the `ckpt.zip` archive and extract it to your local computer
















## Shake Hands

```Shell
# A model saved at a specific training step
# cd ~/output_lerobot_train/shake/diffusion/checkpoints/005000

# The latest model
cd ~/output_lerobot_train/shake/wallx/checkpoints/last
zip -r ~/ckpt.zip pretrained_model
```
