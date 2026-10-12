[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | 繁體中文 | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# 註冊Hugging Face帳號（選用）

## 設定HuggingFace國內鏡像

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



## 建立Token

https://huggingface.co/settings/tokens

![圖片展示了Hugging Face平台的介面，左側為使用者頭像及個人資訊區域，右側是模型和資料集的相關內容。畫面右側有紅色箭頭指向「Access Tokens」選項，該選項位於「Settings」下。上下文提到在建立Token後，需用上下鍵控制，選擇貼上金鑰，此圖直觀呈現了「Access Tokens」在平台中的位置，與上下文關於建立Token後記錄Token的操作步驟相關，是建立Token後設定相關權限的介面展示。](../../en/images/d34-01.png)

![圖片展示的是Hugging Face平台的Access Tokens頁面。左側導覽列中「Access Tokens」選項被選取。右側頁面顯示User Access Tokens相關資訊，包括名稱、值、上次重新整理日期、上次使用日期及權限等。頁面右上角有「Create new token」按鈕，用紅色箭頭醒目顯示。該圖片與文件中「建立Token」部分內容相關，直觀呈現了建立新Token的操作位置，協助使用者瞭解在Hugging Face平台建立Token的具體頁面環境。](../../en/images/d34-02.png)

![這張圖片展示的是Hugging Face平台建立新存取權杖的操作介面，頁面標題為「Create new Access Token」。介面中需要重點設定三項內容，分別是選擇名為「Write」的Token類型，設定名稱為「so-arm101」，隨後點選「Create token」按鈕，這些操作都有紅色方框和序號1、2、3做標識，用於引導完成帶寫入權限的權杖建立，該操作對應文件中建立Token的步驟相關內容，是取得綁定Hugging Face所需金鑰的關鍵環節。](../../en/images/d34-03.png)

![這張圖片是Hugging Face帳號的Access Token儲存頁面，核心內容為提示需將Token值妥善儲存，關閉該彈出視窗後將無法再次檢視，若遺失則需重新建立。頁面內顯示產生的存取金鑰為hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx，對應名稱為so-arm101，權限為可寫。頁面帶有紅色箭頭指向的「Copy」按鈕，按鈕被紅框醒目標註，用於複製該Token，右下角有「Done」按鈕可完成目前操作，該圖對應文件中記錄或綁定Hugging Face帳號Token的相關步驟。](../../en/images/d34-04.png)

## 記錄Token

例如，我的是：

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## 綁定Token

```Shell
hf auth login

hf auth whoami
```

![圖片展示了在命令列中使用Hugging Face Token登入的介面。在輸入「hf auth login」命令後，出現提示「? How would you like to log in?」，並顯示「Paste an access token」選項。這與文件中「綁定Token」步驟相關，說明在用上下鍵控制選擇貼上金鑰後，登入介面會提示如何登入，此時可選擇貼上存取權杖進行登入，以完成Hugging Face Token的綁定操作。](../../en/images/d34-05.png)

> 用上下鍵控制，選擇貼上金鑰

![這張圖片展示了在命令列中操作Hugging Face帳號的過程，紅色方框重點標註了目前作用中的Token為「so-arm101-upload」，該Token已被儲存至指定路徑。畫面中的命令列依序執行了登出、重新登入的操作，系統提示登入Hugging Face需使用權杖，貼上權杖成功後顯示權杖權限為寫入，後續完成儲存操作，最終顯示目前作用中的權杖資訊，該內容對應文件中「綁定Token」步驟的操作介面。](../../en/images/d34-06.png)

> 成功介面

## 建立Dataset Repo

<grid>
<column width-ratio="0.434605">
![這張圖片展示的是Hugging Face介面的下拉式選單，頂部顯示登入使用者為「juxi-admin」，選單中列有多個功能選項，包括新增模型、新增空間、新增儲存桶等。其中被紅色框標註醒目顯示的是「New Dataset」選項，對應文件中建立Dataset Repo的操作環節，該選項是建立資料集儲存庫的入口，使用者可透過選擇該選項完成資料集儲存庫的建立操作。](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![圖片展示的是在Hugging Face建立Dataset Repo的介面。介面中「Dataset name」處輸入了「so-arm101」，「License」選擇為「apache-2.0」，「Public」選項被選取，表示任何人都可檢視此Dataset，只有你可提交。該圖片與文件中「建立Dataset Repo」步驟相關，是建立Dataset Repo操作中的一個設定介面展示，協助使用者瞭解建立時需填寫的關鍵資訊。](../../en/images/d34-08.png)
</column>
</grid>

![圖片展示的是Hugging Face平台中「so - arm101」資料集的頁面。頁面上方有搜尋列及導覽列，可存取Models、Datasets等板塊。頁面中部顯示資料集資訊，包括License為apache - 2.0，檔案大小為2.53 kB等。下方有「Getting started with your dataset」板塊，提示新增中繼資料並完成資料集卡片以提高可發現性，還提供了編輯資料集卡片的選項。右側有「Copy to bucket」和「Edit dataset card」按鈕，以及下載資料集檔案的記錄。該圖與文件中建立Dataset Repo的內容相關，展示了資料集管理介面。](../../en/images/d34-09.png)
