[English](../../en/08-train-model/cloud-gpu-setup.md) | 简体中文 | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# 云GPU训练环境配置

## 关闭自己电脑的网络代理

不然可能打不开Jupyter的命令行

## 登录云GPU平台Featurize

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## 开启一个云GPU实例

<grid>
<column width-ratio="0.597692">
![这张图片是Featurize平台的云GPU实例选择界面，核心展示了不同配置的云GPU实例选项，其中被红色框标注出的是RTX 5090云GPU实例，该实例标注为2.0可用，按量使用费用为3元/小时，显卡显存达32.0GB，搭载38核AMD EPYC 9354处理器及128G内存，其下方有“开始使用”和“预定”两个按钮，并有红色箭头指向“开始使用”按钮，对应文档中“开启一个云GPU实例”的操作指引内容。](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![图片展示的是Featurize平台中选择镜像的界面。界面中显示有“选择镜像”选项卡，下方有“官方镜像”“我的镜像”“热门镜像”三个标签。其中“官方镜像”标签下，PyTorch 2镜像被红色框和箭头突出显示，其大小为14.5 GB，已使用19001次，标注为“官方”。该图片与上下文关系紧密，上下文提到开启云GPU实例后，点击“JupyterLab”并上传代码和数据集，此图即为选择镜像操作中展示的官方镜像选项，用于后续安装配置环境等操作。](../../en/images/d45-02.png)
</column>
</grid>

![这张图片是云GPU实例的操作界面，对应文档中“开启一个云GPU实例”的步骤内容，用于展示实例开启后的操作选项。界面中显示了型号为RTX 5090的实例的相关配置信息，包括GPU、CPU、内存、硬盘的参数，以及实例的租用时间、方式、费用等内容。图中用红色箭头和红色框突出标注了“打开工作区”按钮，提示用户需点击该按钮，以进入后续进行JupyterLab操作、上传代码和数据集的环节。](../../en/images/d45-03.png)

![图片展示了JupyterLab界面，左侧为文件管理区域，有“实例”“文件”“终端”等选项卡，当前选中“文件”选项卡。右侧是Launcher区域，显示了Notebook、Console、Python 3（ipykernel）等选项。图片中红色箭头指向左侧文件管理区域的“文件”选项卡，突出显示该操作位置，与上下文“点击下方的‘JupyterLab’，左上角有个上传按钮，可以在这里上传代码和数据集”相呼应，指导用户在JupyterLab中进行文件相关操作。](../../en/images/d45-04.png)

> 点击下方的“JupyterLab”，左上角有个上传按钮，可以在这里上传代码和数据集

## 安装配置环境

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

# 不上传到Huggingface和不需要wandb则不用安装
```

> 如果在模型安装的时候缺少了training，需要额外安装一下
> 
> `pip install -e ".[training]"`

## 登录wandb

```Shell
wandb login
复制粘贴API Key，回车
```

![这张图片展示的是Lerobot项目的wandb登录操作界面，记录了登录过程的相关信息。内容从启动wandb登录开始，提示用户需要访问指定地址查找API密钥，并将密钥粘贴后按回车提交。界面还显示系统未找到netrc文件，正在添加API密钥到对应的netrc文件路径中，最终完成登录，显示当前登录用户为tommyzihao，同时提供了强制重新登录的命令指引。该图片对应文档中“登录wandb”的步骤，呈现了登录操作的过程和结果。](../../en/images/d45-05.png)

## 挂载数据集

```Shell
复制实例下载命令，类似：
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

数据集出现在`~`目录下

## 修改权重保存频率（选做）

打开`lerobot/src/lerobot/configs/train.py`

将save_freq，从20_000修改为5_000

这样能在训练更早期获得模型权重文件