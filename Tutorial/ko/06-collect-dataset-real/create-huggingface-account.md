[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | 한국어 | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# Hugging Face 계정 등록(선택 사항)

## 중국 내 HuggingFace 미러 설정

- Ubuntu

```Shell
sudo nano ~/.bashrc

# 파일 끝에 다음을 추가합니다
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# 출력
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# 파일 끝에 다음을 추가합니다
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# 출력
# https://hf-mirror.com
```



## 토큰 생성

https://huggingface.co/settings/tokens

![이 이미지는 Hugging Face 플랫폼 인터페이스를 보여 주며, 왼쪽에는 사용자의 아바타와 프로필 정보 영역, 오른쪽에는 모델과 데이터셋 내용이 있습니다. 오른쪽에는 "Settings" 아래에 있는 "Access Tokens" 옵션을 가리키는 빨간 화살표가 있습니다. 본문은 토큰을 만든 뒤 위/아래 키로 키를 선택하고 붙여넣어야 한다고 언급하며, 이 이미지는 플랫폼에서 "Access Tokens"가 어디에 있는지 시각적으로 보여 주고, 토큰을 만든 뒤 기록하는 단계와 관련이 있으며, 토큰 생성 후 관련 권한을 설정하는 인터페이스입니다.](../../en/images/d34-01.png)

![이 이미지는 Hugging Face 플랫폼의 Access Tokens 페이지를 보여 줍니다. 왼쪽 내비게이션 바에서 "Access Tokens" 옵션이 선택되어 있습니다. 오른쪽에는 이름, 값, 마지막 새로 고침 날짜, 마지막 사용 날짜, 권한을 포함한 User Access Tokens 정보가 표시됩니다. 오른쪽 상단에는 빨간 화살표로 강조된 "Create new token" 버튼이 있습니다. 이 이미지는 "토큰 생성" 절과 관련이 있으며, 새 토큰을 만들 위치를 시각적으로 보여 주어 사용자가 Hugging Face에서 토큰을 만드는 구체적인 페이지를 이해하는 데 도움을 줍니다.](../../en/images/d34-02.png)

![이 이미지는 Hugging Face 플랫폼에서 새 액세스 토큰을 만드는 인터페이스를 보여 주며, 페이지 제목은 "Create new Access Token"입니다. 세 항목을 설정해야 합니다. "Write"라는 이름의 토큰 유형을 선택하고, 이름을 "so-arm101"로 설정한 다음, "Create token" 버튼을 클릭합니다. 이러한 작업은 빨간 박스와 숫자 1, 2, 3으로 표시되어 사용자가 쓰기 권한이 있는 토큰을 만들도록 안내합니다. 이는 토큰을 만드는 단계에 해당하며, Hugging Face를 바인딩하는 데 필요한 키를 얻는 핵심 단계입니다.](../../en/images/d34-03.png)

![이 이미지는 Hugging Face 계정의 Access Token 저장 페이지입니다. 핵심 내용은 토큰 값을 잘 보관하라는 알림으로, 팝업을 닫으면 다시 볼 수 없고 분실하면 다시 만들어야 하기 때문입니다. 페이지에는 생성된 액세스 키 hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx가 이름 so-arm101 및 쓰기 권한과 함께 표시됩니다. 토큰을 복사하는 데 사용하는, 빨간 화살표가 가리키고 빨간 박스로 강조된 "Copy" 버튼과 현재 작업을 마치는 오른쪽 하단의 "Done" 버튼이 있습니다. 이 이미지는 Hugging Face 계정 토큰을 기록하거나 바인딩하는 단계에 해당합니다.](../../en/images/d34-04.png)

## 토큰 기록

예를 들어 제 것은 다음과 같습니다:

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## 토큰 바인딩

```Shell
hf auth login

hf auth whoami
```

![이 이미지는 명령 줄에서 Hugging Face 토큰으로 로그인하는 것을 보여 줍니다. "hf auth login" 명령을 입력한 뒤 "? How would you like to log in?" 프롬프트가 나타나고 "Paste an access token" 옵션이 표시됩니다. 이는 "토큰 바인딩" 단계와 관련이 있으며, 위/아래 키로 키를 선택하고 붙여넣으면 로그인 화면에서 어떻게 로그인할지 묻고, 이때 액세스 토큰을 붙여넣어 로그인하여 Hugging Face 토큰 바인딩을 완료할 수 있음을 나타냅니다.](../../en/images/d34-05.png)

> 위/아래 키로 키를 선택하고 붙여넣습니다

![이 이미지는 명령 줄에서 Hugging Face 계정을 조작하는 것을 보여 주며, 빨간 박스로 현재 활성 토큰이 "so-arm101-upload"이고 지정된 경로에 저장되었음이 강조되어 있습니다. 명령 줄에서 로그아웃한 뒤 다시 로그인했습니다. 시스템은 Hugging Face에 로그인하려면 토큰이 필요하다고 안내했고, 토큰을 붙여넣어 성공한 뒤 토큰 권한이 write로 표시되었으며, 그다음 저장을 마치고 마지막으로 현재 활성 토큰 정보를 표시했습니다. 이 내용은 "토큰 바인딩" 단계에 해당합니다.](../../en/images/d34-06.png)

> 성공 화면

## 데이터셋 저장소 생성

<grid>
<column width-ratio="0.434605">
![이 이미지는 Hugging Face 인터페이스의 드롭다운 메뉴를 보여 줍니다. 상단에는 로그인한 사용자가 "juxi-admin"으로 표시되고, 메뉴에는 새 모델, 새 스페이스, 새 버킷 등 여러 기능 옵션이 나열됩니다. 빨간 박스로 강조된 옵션은 "New Dataset"으로, "데이터셋 저장소 생성" 단계에 해당합니다. 이 옵션은 데이터셋 저장소를 만드는 진입점으로, 이를 통해 사용자는 데이터셋 저장소 생성을 완료할 수 있습니다.](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![이 이미지는 Hugging Face에서 데이터셋 저장소를 만드는 인터페이스를 보여 줍니다. "Dataset name"에 "so-arm101" 값이 입력되어 있고, "License"는 "apache-2.0"으로 설정되어 있으며, "Public" 옵션이 선택되어 있어 누구나 이 데이터셋을 볼 수 있고 커밋은 본인만 할 수 있습니다. 이 이미지는 "데이터셋 저장소 생성" 단계와 관련이 있으며, 설정 화면 중 하나를 보여 주어 사용자가 데이터셋을 만들 때 입력해야 할 핵심 정보를 이해하는 데 도움을 줍니다.](../../en/images/d34-08.png)
</column>
</grid>

![이 이미지는 Hugging Face 플랫폼의 "so - arm101" 데이터셋 페이지를 보여 줍니다. 상단에는 Models, Datasets 같은 섹션에 접근할 수 있는 검색 바와 내비게이션 바가 있습니다. 가운데에는 License apache - 2.0과 2.53 kB의 파일 크기를 포함한 데이터셋 정보가 표시됩니다. 아래에는 "Getting started with your dataset" 섹션이 있어 메타데이터를 추가하고 데이터셋 카드를 완성하여 검색 가능성을 높이라고 안내하며, 데이터셋 카드를 편집할 수 있는 옵션도 제공합니다. 오른쪽에는 "Copy to bucket" 및 "Edit dataset card" 버튼과 데이터셋 파일 다운로드 기록이 있습니다. 이 이미지는 데이터셋 저장소 생성과 관련이 있으며, 데이터셋 관리 인터페이스를 보여 줍니다.](../../en/images/d34-09.png)
