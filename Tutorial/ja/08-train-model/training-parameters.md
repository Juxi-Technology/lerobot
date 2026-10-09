[English](../../en/08-train-model/training-parameters.md) | [简体中文](../../zh-hans/08-train-model/training-parameters.md) | [繁體中文](../../zh-hant/08-train-model/training-parameters.md) | [Deutsch](../../de/08-train-model/training-parameters.md) | [Español](../../es/08-train-model/training-parameters.md) | [Français](../../fr/08-train-model/training-parameters.md) | [Italiano](../../it/08-train-model/training-parameters.md) | 日本語 | [한국어](../../ko/08-train-model/training-parameters.md) | [Português (BR)](../../pt-br/08-train-model/training-parameters.md) | [Português (PT)](../../pt-pt/08-train-model/training-parameters.md)

# 学習パラメーターの推奨



https://github.com/huggingface/lerobot/blob/main/src/lerobot/configs/train.py

`save_freq` パラメーターを少し小さくすると、学習後にモデルがより早く現れます



単純なタスク（把持・握手・配置）では、20K ステップの学習で十分すぎるほどです
