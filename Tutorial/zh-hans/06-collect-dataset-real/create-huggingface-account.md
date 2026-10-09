[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | 简体中文 | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# 注册Hugging Face账号（可选）

## 设置HuggingFace国内镜像

- Ubuntu

```Shell
sudo nano ~/.bashrc

# 在文件末尾加入
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# 输出
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# 在文件末尾加入
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# 输出
# https://hf-mirror.com
```



## 创建Token

https://huggingface.co/settings/tokens

![图片展示了Hugging Face平台的界面，左侧为用户头像及个人信息区域，右侧是模型和数据集的相关内容。画面右侧有红色箭头指向“Access Tokens”选项，该选项位于“Settings”下。上下文提到在创建Token后，需用上下键控制，选择粘贴密钥，此图直观呈现了“Access Tokens”在平台中的位置，与上下文关于创建Token后记录Token的操作步骤相关，是创建Token后设置相关权限的界面展示。](../../en/images/d34-01.png)

![图片展示的是Hugging Face平台的Access Tokens页面。左侧导航栏中“Access Tokens”选项被选中。右侧页面显示User Access Tokens相关信息，包括名称、值、上次刷新日期、上次使用日期及权限等。页面右上角有“Create new token”按钮，用红色箭头突出显示。该图片与文档中“创建Token”部分内容相关，直观呈现了创建新Token的操作位置，帮助用户了解在Hugging Face平台创建Token的具体页面环境。](../../en/images/d34-02.png)

![这张图片展示的是Hugging Face平台创建新访问令牌的操作界面，页面标题为“Create new Access Token”。界面中需要重点设置三项内容，分别是选择名为“Write”的Token类型，设置名称为“so-arm101”，随后点击“Create token”按钮，这些操作都有红色方框和序号1、2、3做标识，用于引导完成带写权限的令牌创建，该操作对应文档中创建Token的步骤相关内容，是获取绑定Hugging Face所需密钥的关键环节。](../../en/images/d34-03.png)

![这张图片是Hugging Face账号的Access Token保存页面，核心内容为提示需将Token值妥善保存，关闭该弹窗后将无法再次查看，若丢失则需重新创建。页面内显示生成的访问密钥为hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx，对应名称为so-arm101，权限为可写。页面带有红色箭头指向的“Copy”按钮，按钮被红框突出标注，用于复制该Token，右下角有“Done”按钮可完成当前操作，该图对应文档中记录或绑定Hugging Face账号Token的相关步骤。](../../en/images/d34-04.png)

## 记录Token

例如，我的是：

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## 绑定Token

```Shell
hf auth login

hf auth whoami
```

![图片展示了在命令行中使用Hugging Face Token登录的界面。在输入“hf auth login”命令后，出现提示“? How would you like to log in?”，并显示“Paste an access token”选项。这与文档中“绑定Token”步骤相关，说明在用上下键控制选择粘贴密钥后，登录界面会提示如何登录，此时可选择粘贴访问令牌进行登录，以完成Hugging Face Token的绑定操作。](../../en/images/d34-05.png)

> 用上下键控制，选择粘贴密钥

![这张图片展示了在命令行中操作Hugging Face账号的过程，红色方框重点标注了当前激活的Token为“so-arm101-upload”，该Token已被保存至指定路径。画面中的命令行依次执行了退出登录、重新登录的操作，系统提示登录Hugging Face需使用令牌，粘贴令牌成功后显示令牌权限为写入，后续完成保存操作，最终显示当前活跃的令牌信息，该内容对应文档中“绑定Token”步骤的操作界面。](../../en/images/d34-06.png)

> 成功界面

## 创建Dataset Repo

<grid>
<column width-ratio="0.434605">
![这张图片展示的是Hugging Face界面的下拉菜单，顶部显示登录用户为“juxi-admin”，菜单中列有多个功能选项，包括新建模型、新建空间、新建存储桶等。其中被红色框标注突出显示的是“New Dataset”选项，对应文档中创建Dataset Repo的操作环节，该选项是创建数据集仓库的入口，用户可通过选择该选项完成数据集仓库的创建操作。](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![图片展示的是在Hugging Face创建Dataset Repo的界面。界面中“Dataset name”处输入了“so-arm101”，“License”选择为“apache-2.0”，“Public”选项被选中，表明任何人都可查看此Dataset，只有你可提交。该图片与文档中“创建Dataset Repo”步骤相关，是创建Dataset Repo操作中的一个设置界面展示，帮助用户了解创建时需填写的关键信息。](../../en/images/d34-08.png)
</column>
</grid>

![图片展示的是Hugging Face平台中“so - arm101”数据集的页面。页面上方有搜索栏及导航栏，可访问Models、Datasets等板块。页面中部显示数据集信息，包括License为apache - 2.0，文件大小为2.53 kB等。下方有“Getting started with your dataset”板块，提示添加元数据并完成数据集卡片以提高可发现性，还提供了编辑数据集卡片的选项。右侧有“Copy to bucket”和“Edit dataset card”按钮，以及下载数据集文件的记录。该图与文档中创建Dataset Repo的内容相关，展示了数据集管理界面。](../../en/images/d34-09.png)