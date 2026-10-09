[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | 简体中文 | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# 示教采集数据集-握手200

## 在HuggingFace上创建Dataset Repo

https://huggingface.co/new-dataset

![图片展示了在HuggingFace上创建新数据集仓库的界面。界面中“Owner”处显示为TommyZihao，数据集名称为“lerobot_zihao_dataset_shake200”，“License”选择为mit，数据集类型为“Public”，任何人都可查看，只有数据集所有者或组织成员可提交。下方提示创建数据集后可使用web界面或git上传文件，底部有“Create dataset”按钮。该图片与文档中在HuggingFace上创建Dataset Repo的内容相关，是创建数据集仓库操作的界面展示。](../../en/images/d37-01.png)

## 删除之前已经有的同名数据集（如果有）

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Shake200数据集采集

一个摄像头，采集数据集-Mac电脑

```Shell
lerobot-record \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true \
    --dataset.repo_id=Tommymy/lerobot_my_dataset_shake200 \
    --dataset.num_episodes=200 \
    --dataset.single_task="Shanke Hands" \
    --dataset.push_to_hub=false \
    --dataset.episode_time_s=12 \
    --dataset.reset_time_s=1
```

## 采集中

<grid>
<column width-ratio="0.508765">
![图片展示的是在Mac电脑上采集数据集时的终端界面。界面中显示了SvtInfo()和SvtInfo()的输出信息，包括版本号、编译器、架构等。还呈现了SvtConfig()的配置参数，如宽度、高度、帧率、预设等。下方有“INFO”和“INFO 0”标识的输出信息，如“Starting second pass: moving the moving atom to the beginning of the file”等。该图片与文档文档中“采集中”内容相关，直观呈现了采集过程中终端显示的配置与信息。](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![图片展示的是在Mac电脑上使用Open_Duck_Mini_Runtime_2脚本采集数据集时的终端输出信息。画面中显示了SVT等视频编码相关配置参数，如gop size、key - frame type等，还呈现了视频编码器版本、编译日期等信息。下方有MP4文件相关日志，如“Starting second pass: moving the moov atom to the beginning of the file”等。该图片与文档中采集数据集的操作流程相关，直观呈现了采集过程中终端的反馈信息。](../../en/images/d37-03.png)
</column>
</grid>

键盘方向键操作：  
→（右箭头）提前终止当前episode；进入下一个episode。  
←（左箭头）取消当前episode；重新录制。  
ESC，立即停止，编码视频，并上传数据集。

## 采集完毕，数据集保存目录

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```