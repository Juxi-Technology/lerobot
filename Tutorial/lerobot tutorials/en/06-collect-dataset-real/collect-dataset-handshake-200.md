English | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# Collecting a Dataset by Demonstration — Handshake 200

## Create a Dataset Repo on HuggingFace

https://huggingface.co/new-dataset

![The image shows the interface for creating a new dataset repository on HuggingFace. "Owner" is shown as TommyZihao, the dataset name is "lerobot_zihao_dataset_shake200", "License" is set to mit, and the dataset type is "Public", viewable by anyone while only the dataset owner or organization members can commit. Below, it notes that after creating the dataset you can upload files through the web interface or git, and there is a "Create dataset" button at the bottom. This image relates to the content on creating a Dataset Repo on HuggingFace, and shows the interface for the create-dataset operation.](../../en/images/d37-01.png)

## Delete Any Existing Dataset with the Same Name (If Any)

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Shake200 Dataset Collection

One camera, collecting a dataset - Mac computer

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

## During Collection

<grid>
<column width-ratio="0.508765">
![The image shows the terminal interface while collecting a dataset on a Mac. It displays the output of SvtInfo() and SvtInfo(), including version number, compiler and architecture. It also presents the SvtConfig() configuration parameters, such as width, height, frame rate and preset. Below there is output marked "INFO" and "INFO 0", such as "Starting second pass: moving the moving atom to the beginning of the file". This image relates to the "During Collection" content, visually presenting the configuration and information shown in the terminal during collection.](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![The image shows the terminal output while collecting a dataset with the Open_Duck_Mini_Runtime_2 script on a Mac. It shows SVT and other video-encoding configuration parameters, such as gop size and key - frame type, and presents the video encoder version and build date. Below there are MP4 file logs, such as "Starting second pass: moving the moov atom to the beginning of the file". This image relates to the dataset collection workflow, visually presenting the terminal feedback during collection.](../../en/images/d37-03.png)
</column>
</grid>

Keyboard arrow key controls:  
→ (Right arrow) Terminate the current episode early; move on to the next episode.  
← (Left arrow) Cancel the current episode; record it again.  
ESC, stop immediately, encode the video, and upload the dataset.

## Collection Finished — Dataset Save Directory

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```