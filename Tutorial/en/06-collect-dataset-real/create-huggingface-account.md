English | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# Register a Hugging Face Account (Optional)

## Set Up a China-Based HuggingFace Mirror

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Add this at the end of the file
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# Output
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# Add this at the end of the file
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Output
# https://hf-mirror.com
```



## Create a Token

https://huggingface.co/settings/tokens

![The image shows the Hugging Face platform interface, with the user's avatar and profile information area on the left and model and dataset content on the right. On the right, a red arrow points to the "Access Tokens" option, located under "Settings". The context mentions that after creating a token you need to use the up/down keys to select and paste the key; this image visually presents where "Access Tokens" is on the platform, relates to the step of recording the token after creating it, and is the interface for setting the relevant permissions after creating a token.](../../en/images/d34-01.png)

![The image shows the Access Tokens page of the Hugging Face platform. In the left navigation bar, the "Access Tokens" option is selected. The right side shows User Access Tokens information, including name, value, last refresh date, last used date and permissions. In the top right there is a "Create new token" button highlighted with a red arrow. This image relates to the "Create a Token" section, visually presenting where to create a new token and helping users understand the specific page for creating a token on Hugging Face.](../../en/images/d34-02.png)

![This image shows the interface for creating a new access token on the Hugging Face platform, with the page title "Create new Access Token". Three items need to be set: select the token type named "Write", set the name to "so-arm101", and then click the "Create token" button. These operations are marked with red boxes and the numbers 1, 2 and 3 to guide users through creating a token with write permission. This corresponds to the steps for creating a token, a key step in obtaining the key needed to bind Hugging Face.](../../en/images/d34-03.png)

![This image is the Access Token save page of a Hugging Face account; its core content is a reminder to save the token value properly, because after closing the popup it can no longer be viewed, and if lost it must be recreated. The page shows the generated access key hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx, with the name so-arm101 and write permission. There is a "Copy" button pointed to by a red arrow and highlighted with a red box, used to copy the token, and a "Done" button at the bottom right to finish the current operation. This image corresponds to the step of recording or binding the Hugging Face account token.](../../en/images/d34-04.png)

## Record the Token

For example, mine is:

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## Bind the Token

```Shell
hf auth login

hf auth whoami
```

![The image shows logging in with a Hugging Face token on the command line. After entering the "hf auth login" command, the prompt "? How would you like to log in?" appears and the "Paste an access token" option is shown. This relates to the "Bind the Token" step, indicating that after selecting and pasting the key with the up/down keys, the login screen asks how you would like to log in, at which point you can choose to paste an access token to log in and complete the Hugging Face token binding.](../../en/images/d34-05.png)

> Use the up/down keys to select and paste the key

![This image shows operating a Hugging Face account on the command line, with a red box highlighting that the currently active token is "so-arm101-upload", which has been saved to the specified path. The command line logged out and then logged back in; the system prompted that logging in to Hugging Face requires a token, and after pasting the token successfully it showed the token permission as write, then completed the save, and finally displayed the current active token information. This content corresponds to the "Bind the Token" step.](../../en/images/d34-06.png)

> Success screen

## Create a Dataset Repo

<grid>
<column width-ratio="0.434605">
![This image shows a dropdown menu in the Hugging Face interface; at the top the logged-in user is shown as "juxi-admin", and the menu lists several function options, including new model, new space and new bucket. The option highlighted with a red box is "New Dataset", corresponding to the "Create a Dataset Repo" step. This option is the entry point for creating a dataset repository, through which users can complete the creation of a dataset repository.](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![The image shows the interface for creating a Dataset Repo on Hugging Face. Under "Dataset name" the value "so-arm101" is entered, "License" is set to "apache-2.0", and the "Public" option is selected, meaning anyone can view this Dataset and only you can commit. This image relates to the "Create a Dataset Repo" step, showing one of the setup screens and helping users understand the key information to fill in when creating one.](../../en/images/d34-08.png)
</column>
</grid>

![The image shows the page of the "so - arm101" dataset on the Hugging Face platform. At the top there is a search bar and navigation bar providing access to sections such as Models and Datasets. In the middle it shows dataset information, including License apache - 2.0 and a file size of 2.53 kB. Below there is a "Getting started with your dataset" section, prompting you to add metadata and complete the dataset card to improve discoverability, and offering the option to edit the dataset card. On the right there are "Copy to bucket" and "Edit dataset card" buttons, and a record of downloading dataset files. This image relates to creating a Dataset Repo, showing the dataset management interface.](../../en/images/d34-09.png)