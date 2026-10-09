English | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# Configuring a Cloud GPU Training Environment

## Disable Your Computer's Network Proxy

Otherwise you may not be able to open the Jupyter command line

## Log In to the Cloud GPU Platform Featurize

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## Start a Cloud GPU Instance

<grid>
<column width-ratio="0.597692">
![This image is the cloud GPU instance selection screen on the Featurize platform, primarily showing cloud GPU instance options with different configurations. The option marked with a red box is an RTX 5090 cloud GPU instance, listed as 2.0 available at a pay-as-you-go rate of 3 CNY/hour, with 32.0 GB of GPU memory, a 38-core AMD EPYC 9354 processor and 128 GB of RAM. Below it are "Start Using" and "Reserve" buttons, with a red arrow pointing to "Start Using", matching the "Start a Cloud GPU Instance" guidance in the document.](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![This image shows the image selection screen on the Featurize platform. It shows a "Select Image" tab, with three sub-tabs below it: "Official Images", "My Images" and "Popular Images". Under the "Official Images" tab, the PyTorch 2 image is highlighted with a red box and arrow; it is 14.5 GB in size, has been used 19,001 times and is labelled "Official". The image is closely related to the context, which describes clicking "JupyterLab" and uploading code and datasets after starting a cloud GPU instance; this screenshot shows the official image option in the image selection step, used for the subsequent environment setup and configuration.](../../en/images/d45-02.png)
</column>
</grid>

![This image shows the console of a cloud GPU instance, corresponding to the "Start a Cloud GPU Instance" step in the document and showing the operations available after the instance is started. It displays the configuration of an RTX 5090 instance, including the GPU, CPU, memory and disk parameters, as well as the instance's rental duration, billing method and cost. A red arrow and a red box highlight the "Open Workspace" button, prompting the user to click it in order to proceed to the JupyterLab operations and upload the code and dataset.](../../en/images/d45-03.png)

![This image shows the JupyterLab interface. On the left is the file management area, with tabs for "Instances", "Files" and "Terminal", and the "Files" tab currently selected. On the right is the Launcher area, showing options such as Notebook, Console and Python 3 (ipykernel). A red arrow in the image points to the "Files" tab in the left-hand file management area, highlighting that location and echoing the context — "click JupyterLab below; there is an upload button in the top-left corner where you can upload code and datasets" — guiding the user through file-related operations in JupyterLab.](../../en/images/d45-04.png)

> Click "JupyterLab" below; there is an upload button in the top-left corner where you can upload code and datasets

## Install and Configure the Environment

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

# Skip the install if you are not uploading to HuggingFace and do not need wandb
```

> If `training` was missing when you installed the model, you need to install it additionally
> 
> `pip install -e ".[training]"`

## Log In to wandb

```Shell
wandb login
Copy and paste the API Key, then press Enter
```

![This image shows the wandb login screen for the LeRobot project, recording the details of the login process. It begins by starting the wandb login, prompting the user to visit a given URL to find the API key and to paste the key and press Enter to submit it. It also shows that no netrc file was found and that the API key is being added to the corresponding netrc file path, after which the login completes and the logged-in user is shown as tommyzihao, along with a command for forcing a re-login. This image corresponds to the "Log In to wandb" step, presenting the process and result of the login.](../../en/images/d45-05.png)

## Mount the Dataset

```Shell
Copy the instance download command, something like:
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

The dataset appears under the `~` directory

## Adjust the Weight Save Frequency (Optional)

Open `lerobot/src/lerobot/configs/train.py`

Change save_freq from 20_000 to 5_000

This way you get model weight files earlier in training
