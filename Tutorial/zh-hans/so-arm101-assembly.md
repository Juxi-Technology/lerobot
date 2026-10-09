[English](../en/so-arm101-assembly.md) | 简体中文 | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>SO-ARM101机械臂散件组装教程</title>

<callout emoji="💡">
注意：成品机械臂请跳过本教程
</callout>

## 从动臂的3D打印件

![这张图片展示了SO-ARM101机械臂组装所需的从动臂3D打印件，均为白色PLA材质的塑料零件，摆放在浅色木质纹理的台面上。这些零件包含不同形状的连接件、带网格的分叉结构、带孔的基座类零件、特殊形状的分叉支臂等，符合教程中提到的从动臂末端为夹爪的结构特点。这些零件是机械臂从动臂部分的基础成型件，是拆除支撑步骤的处理对象，与教程中介绍的从动臂3D打印件内容直接对应。](../en/images/d09-01.jpg)

## 主动臂的3D打印件

![图片展示了SO - ARM101机械臂的3D打印件。画面中整齐排列着多种黑色3D打印件，部分件边缘有蓝色线条。这些部件包括主动臂和从动臂的结构件，如夹爪、把手、扳机等，还有连接件等。图片与文档中“主动臂的3D打印件”部分对应，直观呈现了3D打印件的外观，为后续拆除残留支撑、区分舵机等操作提供参考。](../en/images/d09-02.jpg)

主动臂和从动臂非常类似，只有末端不一样

主动臂是把手和扳机，从动臂是夹爪

## 拆除3D打印件上残留的支撑

检查每一个孔、洞、槽、网格，特别是类似麻将“五筒”的五个孔

这一步非常重要，不然后面拧螺丝拧不进去

## 四种舵机区分

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">大型号</td><td vertical-align="middle">小型号</td><td vertical-align="middle">电压（V）</td><td vertical-align="middle">减速比</td><td vertical-align="middle">机械臂关节</td><td vertical-align="middle">数量</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">主动臂2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">主动臂1、3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">主动臂4、5、6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">从动臂所有关节</td><td vertical-align="middle">6</td></tr></tbody></table>

> 减速比是 “电机转速：舵机输出轴转速” 的比值，比如 1:345 代表电机转 345 圈，舵机输出轴才转 1 圈。
> 
> 大减速比会通过齿轮组放大扭矩，所以能带动更重的负载（比如从动臂）
> 
> 但同时，输出轴的转动速度会更慢（因为被“减速”了）
> 
> 如果拖拽关节，会更费力

下面是本项目所有舵机的型号、减速比，下划线是它们的编号

![图片展示了机械臂中使用的舵机型号、电压及减速比。左侧为主动臂，有C046（7.4V, 1:147）、C044（7.4V, 1:191）两种型号；右侧为从动臂，有C001（7.4V, 1:345）、C047（12V, 1:345）两种型号。图片与上下文紧密相关，上下文详细介绍了主动臂和从动臂的舵机型号、电压、减速比等信息，此图直观呈现了这些关键数据，帮助读者更好地理解舵机配置。](../en/images/d09-03.png)

![图片展示了四盒标有“STS3215”的舵机。每盒上印有“SPECIFICATION”字样，包含扭矩、速度、尺寸等参数，如扭矩为9.2kg·cm/127.98oz·in(6V)等。其中，STS3215 - C001的扭矩为12.5kg·cm/173.88oz·in(6V)，STS3215 - C046的扭矩为16kg·cm/220.58oz·in(7V)。这些舵机是机械臂中从动臂所有关节的型号，与文档中介绍的从动臂相关，用于后续组装步骤中舵机的安装。](../en/images/d09-04.jpg)

## 区分两种电压的电源适配器

5V 6A 30W的电源适配器：给7.4V舵机供电（主动臂）黑色

12V 5A 60W的电源适配器，给12V舵机供电（从动臂）白色

## 下载飞特舵机调试工具

### Windows电脑

https://gitee.com/ftservo/fddebug

下载[`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z)，解压，运行里面的exe程序

### Ubuntu电脑和Mac电脑（压缩包含教程）

<figure view-type="Card">[附件 / Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![这张图片是SO-ARM101机械臂散件组装教程的辅助说明图，对应区分电源适配器的内容模块，展示了两种型号的舵机及安装位置，分别为STS3215-C001、STS3215-C018，还标注了STS3215-C004等舵机的编号，对应机械臂的不同关节部位。图中同时列出了这两款舵机的参数信息，包括转动速度、堵转扭矩、舵机精度、保护功能和参数反馈内容，为机械臂组装中舵机的选型和安装提供参考。](../en/images/d09-05.jpg)

**Pro版 主动臂使用5V6A电源适配器，从动臂使用12V5A电源适配器**

舵机ID设置和舵机角度校准及组装要提前做好，可参考[官方组装教程](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# 第一步：设置舵机ID，安装舵盘（除5号舵机）

<grid>
<column width-ratio="0.500000">
![图片展示的是飞特上位机调试工具界面。界面中有“调试”“编程”“升级”三个选项卡，当前选中“编程”选项卡。关键信息有：1. 通信设置中，端口号为COM6，波特率为1000000；2. 舵机操作中，同步写、异步写、扭矩输出均被选中；3. 舵机反馈中，电压、电流、温度、位置等参数显示为0；4. 舵机搜索中，选中id为1，型号为ST53215。该图片与上文设置舵机ID、安装舵盘等调试操作相关，是调试工具界面的呈现。](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![图片展示的是飞特上位机调试工具界面，用于设置舵机ID。界面中有“调试”“编程”“升级”三个选项卡，当前选中“编程”选项卡。在“中位校准”区域，可看到ID编号为4，右侧有“保存”按钮。界面左侧显示舵机ID、型号等信息。该图片与文档中“第一步：设置舵机ID，安装舵盘（除5号舵机）”的内容相关，是设置舵机ID操作的界面呈现，直观展示了设置ID编号的操作位置。](../en/images/d09-07.png)
</column>
</grid>

1. 打开飞特上位机调试工具，选择COM端口号，波特率为一百万，点“打开”
2. 点“搜索”，出现“STS3215”后，点“停止”，点“STS3215”
3. 选择上方“调试”，可以拖拽滑条让舵机旋转，也可以点“扫描”让舵机往复运动。确认舵机运行正常
4. 选择上方“编程”
5. 点“中位校准”，设置此时舵机旋转轴位置为中位（0-4095）
6. 点“ID”，在右下角设置对应舵机的ID编号，点“保存”。注意编号是纯阿拉伯数字，不加字母。
7. 拔掉舵机连接控制板的线
8. 在舵机上插上舵机线

1号舵机插两根线，其它舵机先只插一根线

![图片展示了SO-ARM101机械臂散件组装中舵机的安装情况。画面中有从动臂和主动臂，从动臂编号为123456，主动臂编号为123456。舵机上标注了1:345和1:191、1:147的齿轮比。下方是控制板，连接着两根线，一根白色，一根黑色。该图片与上文组装步骤相关，直观呈现了舵机的安装位置及编号，帮助组装者准确对应舵机与控制板的连接。](../en/images/d09-08.png)

<callout emoji="💡">
再次提醒，请确保舵机关节 ID 和齿轮比与 **SO-ARM101** 的严格对应。
</callout>

总线上每个电机都有一个唯一的ID。新电机通常带有一个默认ID `1`。为了确保电机和控制器之间的通信正常，我们首先需要为每个电机设置一个唯一的ID。此外，总线上的数据传输速度由波特率决定。为了能够相互通信，控制器和所有电机都需要配置相同的波特率，本机械臂舵机的波特率为100000。

为此，我们首先需要将控制器分别连接到每个电机，以便进行设置。由于我们会将这些参数写入电机内部存储器（EEPROM）的非易失性区域，因此只需操作一次即可。

如果您要重新利用其他机器人的电机，您可能还需要执行此步骤，因为 ID 和波特率可能不匹配。

下面的视频展示了设置电机 ID 的步骤顺序。

## Windows系统

<figure view-type="Card">[附件 / Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

使用飞特舵机上位机设置舵机ID并校准中位，ID设置是从1到6的！

<figure view-type="Preview">[附件 / Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/ubuntu系统和Mac电脑

<callout emoji="💡">
如需飞特舵机上位机可参考上面的 [飞特舵机调试工具](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb)
</callout>

请先按照 [官方Lerobot环境安装](https://huggingface.co/docs/lerobot/installation) 这一页完成环境部署

<callout emoji="💡">
注意激活虚拟环境并进入到对应的src/lerobot目录下
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1、查找机械臂对应的 USB 端口 为了找到每个机械臂正确的端口，请运行实用脚本两次：：

```Plain Text
lerobot-find-port
```

识别Leader机械臂端口时的示例输出（例如，Mac 上为 `/dev/tty.usbmodem575E0031751`，或 Linux 上可能为 `/dev/ttyACM0`）：

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

识别Follower机械臂端口时的示例输出（例如，`/dev/tty.usbmodem575E0032081`，或在 Linux 上可能为 `/dev/ttyACM1`）：

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
请记住要拔出 USB 接头，否则将无法检测到接口。
</callout>

2、使用 USB 数据线从电脑连接到从动臂的舵机驱动板，并接通电源。然后，运行以下命令。请将命令中的--robot.port=/dev/ttyACM0 修改为找到的端口号。如查找的端口为/dev/ttyACM1，则修改为--robot.port=/dev/ttyACM1

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

您会看到以下输出。

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

依照指示，连接夹爪的舵机。请确保它是唯一连接到舵机驱动板的舵机，并且该舵机尚未与其他任何舵机进行连接。当您按下 **[Enter]** 键后，脚本将自动设置该舵机的 ID 和波特率，ID设置是从6到1的！

之后，您应该会看到以下信息：

```Python
'gripper' motor id set to 6
```

接着是下一条输出是:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**注意** 根据指示，对每个舵机重复上述操作。
与之前的舵机一样，请确保它是唯一连接到驱动板的舵机，并且舵机本身没有连接到任何其他舵机。
</callout>

在每次按 **Enter** 键之前，请务必检查您的线缆连接。例如，在操作电路板时，电源线可能会断开。

当您完成所有步骤后，脚本将自动结束，此时舵机即可投入使用。现在，您可以将每根舵机的 3 针接口依次连接，并将第一个舵机（ID 为 1 的“shoulder pan”舵机）的线缆连接到驱动板。现在可以将驱动板安装到机械臂的底座上。

对主动臂重复相同的步骤。

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[附件 / Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# 第二步：组装

<callout emoji="💡">
- 从动臂的组装步骤与主动臂基本相同。唯一的区别在于第12步之后，末端执行器（夹爪和手柄）的安装方式有所不同。
</callout>

<figure view-type="Preview">[附件 / Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
舵机驱动板的安装：先安装4个铜柱，然后用四个M2.5\*8的螺丝固定驱动板
</callout>

<grid>
<column width-ratio="0.525947">
![安装四个铜柱](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![用M2.5*8螺丝将舵机驱动板固定](../en/images/d09-10.webp)
</column>
</grid>

![安装到机械臂上并接线](../en/images/d09-11.png)

**Pro版 黑色主动臂使用5V6A电源适配器，白色从动臂使用12V5A电源适配器**







# 网页端设置舵机ID和中位校准

https://bambot.org/feetech.js?lang=zh

1、根据舵机型号输入0或1，点击“连接”

![图片展示的是机械臂散件组装教程中“连接”界面。界面左侧显示“连接”字样，右侧有“波特率”设置为1,000,000 bps（Index 0）的下拉框，以及“协议端（0=STS/SMS, 1=SCS）”设置为0的输入框，输入框旁有红色边框标识的数字“1”。下方有绿色的“连接”按钮，按钮旁有红色边框标识的数字“2”。底部显示“状态：已断开”。该图片与上文“根据舵机型号输入0或1，点击‘连接’”的内容对应，直观呈现了连接操作的界面设置。](../en/images/d09-12.png)

2、扫描ID 1\~6 的舵机，可以根据扫描结果里的FOUND确认对应ID舵机。例如图片里舵机 ID 1 被扫描到了

![图片展示的是SO-ARM101机械臂散件组装教程中“扫描舵机”步骤的界面。界面上方有“起始ID”和“结束ID”输入框，当前起始ID为1，结束ID为6。下方有“开始扫描”按钮。扫描结果部分显示扫描ID1 - 6，扫描ID1 - 6均未找到舵机，提示“Exception: No status packet! Error code: 0”。该图片与上下文紧密相关，直观呈现了扫描舵机时的界面及结果，帮助用户了解舵机扫描情况。](../en/images/d09-13.png)

3、ID设置和中位校准

①当前舵机ID输入为被扫描到的舵机ID

②在“ID管理”中输入数字，点击“更改ID”即可设置ID

③中位校准（STS3215舵机中位是2047，SCS0009舵机中位是511）

STS舵机：在“位置控制”输入2047，并点击“Set”

SCS舵机：在“位置控制”输入511，并点击“Set”

![图片展示了单个舵机控制界面。当前舵机ID为1，ID管理中输入数字1，点击“更改ID”后显示“Success: ID changed to 1”。位置控制中显示2047，点击“Set”按钮。该图片与上下文“ID设置和中位校准”相关，直观呈现了ID设置操作的界面，帮助用户了解如何在“ID管理”中输入数字设置ID，以及在“位置控制”中输入中位值并点击“Set”完成设置。](../en/images/d09-14.png)