[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | 繁體中文 | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>SO-ARM101機械手臂散件組裝教學</title>

<callout emoji="💡">
注意：成品機械手臂請略過本教學
</callout>

## 從動臂的3D列印件

![這張圖片展示了SO-ARM101機械手臂組裝所需的從動臂3D列印件，均為白色PLA材質的塑膠零件，擺放在淺色木質紋理的檯面上。這些零件包含不同形狀的連接件、帶網格的分叉結構、帶孔的基座類零件、特殊形狀的分叉支臂等，符合教學中提到的從動臂末端為夾爪的結構特點。這些零件是機械手臂從動臂部分的基礎成型件，是拆除支撐步驟的處理對象，與教學中介紹的從動臂3D列印件內容直接對應。](../en/images/d09-01.jpg)

## 主動臂的3D列印件

![圖片展示了SO - ARM101機械手臂的3D列印件。畫面中整齊排列著多種黑色3D列印件，部分件邊緣有藍色線條。這些部件包括主動臂和從動臂的結構件，如夾爪、把手、扳機等，還有連接件等。圖片與文件中「主動臂的3D列印件」部分對應，直觀呈現了3D列印件的外觀，為後續拆除殘留支撐、區分伺服馬達等操作提供參考。](../en/images/d09-02.jpg)

主動臂和從動臂非常類似，只有末端不一樣

主動臂是把手和扳機，從動臂是夾爪

## 拆除3D列印件上殘留的支撐

檢查每一個孔、洞、槽、網格，特別是類似麻將「五筒」的五個孔

這一步非常重要，不然後面鎖螺絲鎖不進去

## 四種伺服馬達區分

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">大型號</td><td vertical-align="middle">小型號</td><td vertical-align="middle">電壓（V）</td><td vertical-align="middle">減速比</td><td vertical-align="middle">機械手臂關節</td><td vertical-align="middle">數量</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">主動臂2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">主動臂1、3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">主動臂4、5、6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">從動臂所有關節</td><td vertical-align="middle">6</td></tr></tbody></table>

> 減速比是 「馬達轉速：伺服馬達輸出軸轉速」 的比值，比如 1:345 代表馬達轉 345 圈，伺服馬達輸出軸才轉 1 圈。
> 
> 大減速比會透過齒輪組放大扭矩，所以能帶動更重的負載（比如從動臂）
> 
> 但同時，輸出軸的轉動速度會更慢（因為被「減速」了）
> 
> 如果拖曳關節，會更費力

下面是本專案所有伺服馬達的型號、減速比，底線是它們的編號

![圖片展示了機械手臂中使用的伺服馬達型號、電壓及減速比。左側為主動臂，有C046（7.4V, 1:147）、C044（7.4V, 1:191）兩種型號；右側為從動臂，有C001（7.4V, 1:345）、C047（12V, 1:345）兩種型號。圖片與上下文緊密相關，上下文詳細介紹了主動臂和從動臂的伺服馬達型號、電壓、減速比等資訊，此圖直觀呈現了這些關鍵資料，幫助讀者更好地理解伺服馬達配置。](../en/images/d09-03.png)

![圖片展示了四盒標有「STS3215」的伺服馬達。每盒上印有「SPECIFICATION」字樣，包含扭矩、速度、尺寸等參數，如扭矩為9.2kg·cm/127.98oz·in(6V)等。其中，STS3215 - C001的扭矩為12.5kg·cm/173.88oz·in(6V)，STS3215 - C046的扭矩為16kg·cm/220.58oz·in(7V)。這些伺服馬達是機械手臂中從動臂所有關節的型號，與文件中介紹的從動臂相關，用於後續組裝步驟中伺服馬達的安裝。](../en/images/d09-04.jpg)

## 區分兩種電壓的電源適配器

5V 6A 30W的電源適配器：給7.4V伺服馬達供電（主動臂）黑色

12V 5A 60W的電源適配器，給12V伺服馬達供電（從動臂）白色

## 下載飛特伺服馬達除錯工具

### Windows電腦

https://gitee.com/ftservo/fddebug

下載[`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z)，解壓縮，執行裡面的exe程式

### Ubuntu電腦和Mac電腦（壓縮檔含教學）

<figure view-type="Card">[附件 / Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![這張圖片是SO-ARM101機械手臂散件組裝教學的輔助說明圖，對應區分電源適配器的內容模組，展示了兩種型號的伺服馬達及安裝位置，分別為STS3215-C001、STS3215-C018，還標註了STS3215-C004等伺服馬達的編號，對應機械手臂的不同關節部位。圖中同時列出了這兩款伺服馬達的參數資訊，包括轉動速度、堵轉扭矩、伺服馬達精度、保護功能和參數回饋內容，為機械手臂組裝中伺服馬達的選型和安裝提供參考。](../en/images/d09-05.jpg)

**Pro版 主動臂使用5V6A電源適配器，從動臂使用12V5A電源適配器**

伺服馬達ID設定和伺服馬達角度校正及組裝要提前做好，可參考[官方組裝教學](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# 第一步：設定伺服馬達ID，安裝舵盤（除5號伺服馬達）

<grid>
<column width-ratio="0.500000">
![圖片展示的是飛特上位機除錯工具介面。介面中有「除錯」「編程」「升級」三個選項卡，目前選中「編程」選項卡。關鍵資訊有：1. 通訊設定中，埠號為COM6，鮑率為1000000；2. 伺服馬達操作中，同步寫、非同步寫、扭矩輸出均被選中；3. 伺服馬達回饋中，電壓、電流、溫度、位置等參數顯示為0；4. 伺服馬達搜尋中，選中id為1，型號為ST53215。該圖片與上文設定伺服馬達ID、安裝舵盤等除錯操作相關，是除錯工具介面的呈現。](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![圖片展示的是飛特上位機除錯工具介面，用於設定伺服馬達ID。介面中有「除錯」「編程」「升級」三個選項卡，目前選中「編程」選項卡。在「中位校正」區域，可看到ID編號為4，右側有「儲存」按鈕。介面左側顯示伺服馬達ID、型號等資訊。該圖片與文件中「第一步：設定伺服馬達ID，安裝舵盤（除5號伺服馬達）」的內容相關，是設定伺服馬達ID操作的介面呈現，直觀展示了設定ID編號的操作位置。](../en/images/d09-07.png)
</column>
</grid>

1. 開啟飛特上位機除錯工具，選擇COM連接埠號，鮑率為一百萬，點「開啟」
2. 點「搜尋」，出現「STS3215」後，點「停止」，點「STS3215」
3. 選擇上方「除錯」，可以拖曳滑條讓伺服馬達旋轉，也可以點「掃描」讓伺服馬達往復運動。確認伺服馬達運作正常
4. 選擇上方「編程」
5. 點「中位校正」，設定此時伺服馬達旋轉軸位置為中位（0-4095）
6. 點「ID」，在右下角設定對應伺服馬達的ID編號，點「儲存」。注意編號是純阿拉伯數字，不加字母。
7. 拔掉伺服馬達連接控制板的線
8. 在伺服馬達上插上伺服馬達線

1號伺服馬達插兩根線，其它伺服馬達先只插一根線

![圖片展示了SO-ARM101機械手臂散件組裝中伺服馬達的安裝情況。畫面中有從動臂和主動臂，從動臂編號為123456，主動臂編號為123456。伺服馬達上標註了1:345和1:191、1:147的齒輪比。下方是控制板，連接著兩根線，一根白色，一根黑色。該圖片與上文組裝步驟相關，直觀呈現了伺服馬達的安裝位置及編號，幫助組裝者準確對應伺服馬達與控制板的連接。](../en/images/d09-08.png)

<callout emoji="💡">
再次提醒，請確保伺服馬達關節 ID 和齒輪比與 **SO-ARM101** 的嚴格對應。
</callout>

總線上每個馬達都有一個唯一的ID。新馬達通常帶有一個預設ID `1`。為了確保馬達和控制器之間的通訊正常，我們首先需要為每個馬達設定一個唯一的ID。此外，總線上的資料傳輸速度由鮑率決定。為了能夠相互通訊，控制器和所有馬達都需要配置相同的鮑率，本機械手臂伺服馬達的鮑率為100000。

為此，我們首先需要將控制器分別連接到每個馬達，以便進行設定。由於我們會將這些參數寫入馬達內部記憶體（EEPROM）的非易失性區域，因此只需操作一次即可。

如果您要重新利用其他機器人的馬達，您可能還需要執行此步驟，因為 ID 和鮑率可能不匹配。

下面的影片展示了設定馬達 ID 的步驟順序。

## Windows系統

<figure view-type="Card">[附件 / Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

使用飛特伺服馬達上位機設定伺服馬達ID並校正中位，ID設定是從1到6的！

<figure view-type="Preview">[附件 / Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/ubuntu系統和Mac電腦

<callout emoji="💡">
如需飛特伺服馬達上位機可參考上面的 [飛特伺服馬達除錯工具](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb)
</callout>

請先按照 [官方Lerobot環境安裝](https://huggingface.co/docs/lerobot/installation) 這一頁完成環境部署

<callout emoji="💡">
注意啟用虛擬環境並進入到對應的src/lerobot目錄下
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1、查找機械手臂對應的 USB 連接埠 為了找到每個機械手臂正確的連接埠，請執行實用指令碼兩次：：

```Plain Text
lerobot-find-port
```

辨識Leader機械手臂連接埠時的範例輸出（例如，Mac 上為 `/dev/tty.usbmodem575E0031751`，或 Linux 上可能為 `/dev/ttyACM0`）：

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

辨識Follower機械手臂連接埠時的範例輸出（例如，`/dev/tty.usbmodem575E0032081`，或在 Linux 上可能為 `/dev/ttyACM1`）：

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
請記住要拔出 USB 接頭，否則將無法偵測到介面。
</callout>

2、使用 USB 資料線從電腦連接到從動臂的伺服馬達驅動板，並接通電源。然後，執行以下命令。請將命令中的--robot.port=/dev/ttyACM0 修改為找到的連接埠號。如查找的連接埠為/dev/ttyACM1，則修改為--robot.port=/dev/ttyACM1

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

您會看到以下輸出。

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

依照指示，連接夾爪的伺服馬達。請確保它是唯一連接到伺服馬達驅動板的伺服馬達，並且該伺服馬達尚未與其他任何伺服馬達進行連接。當您按下 **[Enter]** 鍵後，指令碼將自動設定該伺服馬達的 ID 和鮑率，ID設定是從6到1的！

之後，您應該會看到以下資訊：

```Python
'gripper' motor id set to 6
```

接著是下一條輸出是:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**注意** 根據指示，對每個伺服馬達重複上述操作。
與之前的伺服馬達一樣，請確保它是唯一連接到驅動板的伺服馬達，並且伺服馬達本身沒有連接到任何其他伺服馬達。
</callout>

在每次按 **Enter** 鍵之前，請務必檢查您的線纜連接。例如，在操作電路板時，電源線可能會斷開。

當您完成所有步驟後，指令碼將自動結束，此時伺服馬達即可投入使用。現在，您可以將每根伺服馬達的 3 針介面依次連接，並將第一個伺服馬達（ID 為 1 的「shoulder pan」伺服馬達）的線纜連接到驅動板。現在可以將驅動板安裝到機械手臂的底座上。

對主動臂重複相同的步驟。

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[附件 / Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# 第二步：組裝

<callout emoji="💡">
- 從動臂的組裝步驟與主動臂基本相同。唯一的區別在於第12步之後，末端執行器（夾爪和手柄）的安裝方式有所不同。
</callout>

<figure view-type="Preview">[附件 / Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
伺服馬達驅動板的安裝：先安裝4個銅柱，然後用四個M2.5\*8的螺絲固定驅動板
</callout>

<grid>
<column width-ratio="0.525947">
![安裝四個銅柱](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![用M2.5*8螺絲將伺服馬達驅動板固定](../en/images/d09-10.webp)
</column>
</grid>

![安裝到機械手臂上並接線](../en/images/d09-11.png)

**Pro版 黑色主動臂使用5V6A電源適配器，白色從動臂使用12V5A電源適配器**







# 網頁端設定伺服馬達ID和中位校正

https://bambot.org/feetech.js?lang=zh

1、根據伺服馬達型號輸入0或1，點擊「連接」

![圖片展示的是機械手臂散件組裝教學中「連接」介面。介面左側顯示「連接」字樣，右側有「鮑率」設定為1,000,000 bps（Index 0）的下拉式選單，以及「協議端（0=STS/SMS, 1=SCS）」設定為0的輸入框，輸入框旁有紅色邊框標識的數字「1」。下方有綠色的「連接」按鈕，按鈕旁有紅色邊框標識的數字「2」。底部顯示「狀態：已斷開」。該圖片與上文「根據伺服馬達型號輸入0或1，點擊『連接』」的內容對應，直觀呈現了連接操作的介面設定。](../en/images/d09-12.png)

2、掃描ID 1\~6 的伺服馬達，可以根據掃描結果裡的FOUND確認對應ID伺服馬達。例如圖片裡伺服馬達 ID 1 被掃描到了

![圖片展示的是SO-ARM101機械手臂散件組裝教學中「掃描伺服馬達」步驟的介面。介面上方有「起始ID」和「結束ID」輸入框，目前起始ID為1，結束ID為6。下方有「開始掃描」按鈕。掃描結果部分顯示掃描ID1 - 6，掃描ID1 - 6均未找到伺服馬達，提示「Exception: No status packet! Error code: 0」。該圖片與上下文緊密相關，直觀呈現了掃描伺服馬達時的介面及結果，幫助使用者了解伺服馬達掃描情況。](../en/images/d09-13.png)

3、ID設定和中位校正

①目前伺服馬達ID輸入為被掃描到的伺服馬達ID

②在「ID管理」中輸入數字，點擊「更改ID」即可設定ID

③中位校正（STS3215伺服馬達中位是2047，SCS0009伺服馬達中位是511）

STS伺服馬達：在「位置控制」輸入2047，並點擊「Set」

SCS伺服馬達：在「位置控制」輸入511，並點擊「Set」

![圖片展示了單個伺服馬達控制介面。目前伺服馬達ID為1，ID管理中輸入數字1，點擊「更改ID」後顯示「Success: ID changed to 1」。位置控制中顯示2047，點擊「Set」按鈕。該圖片與上下文「ID設定和中位校正」相關，直觀呈現了ID設定操作的介面，幫助使用者了解如何在「ID管理」中輸入數字設定ID，以及在「位置控制」中輸入中位值並點擊「Set」完成設定。](../en/images/d09-14.png)