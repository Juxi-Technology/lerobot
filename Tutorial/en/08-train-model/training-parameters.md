English | [简体中文](../../zh-hans/08-train-model/training-parameters.md) | [繁體中文](../../zh-hant/08-train-model/training-parameters.md) | [Deutsch](../../de/08-train-model/training-parameters.md) | [Español](../../es/08-train-model/training-parameters.md) | [Français](../../fr/08-train-model/training-parameters.md) | [Italiano](../../it/08-train-model/training-parameters.md) | [日本語](../../ja/08-train-model/training-parameters.md) | [한국어](../../ko/08-train-model/training-parameters.md) | [Português (BR)](../../pt-br/08-train-model/training-parameters.md) | [Português (PT)](../../pt-pt/08-train-model/training-parameters.md)

# Training Parameter Recommendations



https://github.com/huggingface/lerobot/blob/main/src/lerobot/configs/train.py

You can lower the `save_freq` parameter a little so that the model appears earlier after training



For simple tasks (picking, handshaking, placing), 20K steps of training is entirely sufficient
