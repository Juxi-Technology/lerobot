[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | 한국어 | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>SO-ARM101 로봇 팔 키트 조립 튜토리얼</title>

<callout emoji="💡">
참고: 조립 완료된 팔이 있다면 이 튜토리얼은 건너뛰십시오
</callout>

## Follower 암의 3D 프린팅 부품

![이 이미지는 SO-ARM101 로봇 팔을 조립하는 데 필요한 Follower 암의 3D 프린팅 부품을 보여주며, 모두 흰색 PLA 플라스틱 부품이 밝은 나뭇결 표면 위에 놓여 있습니다. 부품에는 다양한 형상의 커넥터, 격자가 있는 포크형 구조, 구멍이 뚫린 베이스형 부품, 특수한 형상의 포크형 지지 암 등이 있으며, 튜토리얼에서 Follower 암의 끝단이 그리퍼라는 점과 일치합니다. 이 부품들은 팔의 Follower 암을 위한 기본 성형 부품이며, 서포트 제거 단계에서 다루는 대상으로서 튜토리얼에서 소개하는 Follower 암 3D 프린팅 부품에 직접 대응합니다.](../en/images/d09-01.jpg)

## Leader 암의 3D 프린팅 부품

![이 이미지는 SO-ARM101 로봇 팔의 3D 프린팅 부품을 보여줍니다. 프레임 안에 다양한 검은색 3D 프린팅 부품이 가지런히 배열되어 있으며, 일부 부품의 모서리에는 파란색 선이 있습니다. 이 부품에는 그리퍼, 핸들, 트리거, 커넥터 등 Leader 및 Follower 암의 구조 부품이 포함됩니다. 이 이미지는 문서의 "Leader 암의 3D 프린팅 부품" 섹션에 대응하며, 3D 프린팅 부품의 외형을 시각적으로 제시하여 이후 남은 서포트 제거와 서보 구분 단계의 참고 자료를 제공합니다.](../en/images/d09-02.jpg)

Leader 암과 Follower 암은 매우 유사하며 끝단만 다릅니다

Leader에는 핸들과 트리거가 있고, Follower에는 그리퍼가 있습니다

## 3D 프린팅 부품의 남은 서포트 제거

모든 구멍, 개구부, 슬롯, 격자를 점검하십시오. 특히 마작의 "오점" 패를 닮은 다섯 개의 구멍을 확인하십시오

이 단계는 매우 중요합니다. 그렇지 않으면 나중에 나사를 조일 수 없습니다

## 네 가지 서보 구분

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">대형</td><td vertical-align="middle">소형</td><td vertical-align="middle">전압 (V)</td><td vertical-align="middle">감속비</td><td vertical-align="middle">팔 관절</td><td vertical-align="middle">수량</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">모든 Follower 관절</td><td vertical-align="middle">6</td></tr></tbody></table>

> 감속비는 "모터 회전 속도 : 서보 출력축 회전 속도"의 비율입니다. 예를 들어 1:345는 출력축이 한 바퀴 회전할 때 모터가 345번 회전한다는 뜻입니다.
> 
> 감속비가 높으면 기어 트레인을 통해 토크가 증폭되므로 더 무거운 하중(예: Follower 암)을 구동할 수 있습니다
> 
> 동시에 출력축은 더 느리게 회전합니다 ("감속"되기 때문입니다)
> 
> 관절을 끄는 데도 더 많은 힘이 듭니다

아래는 이 프로젝트의 모든 서보 모델과 감속비이며, 밑줄이 그어진 부분이 그 번호입니다

![이 이미지는 팔에 사용된 서보 모델, 전압, 감속비를 보여줍니다. 왼쪽은 Leader 암으로 C046 (7.4V, 1:147)과 C044 (7.4V, 1:191) 두 모델이 있습니다. 오른쪽은 Follower 암으로 C001 (7.4V, 1:345)과 C047 (12V, 1:345) 두 모델이 있습니다. 이 이미지는 Leader 암과 Follower 암의 서보 모델, 전압, 감속비를 자세히 소개하는 문맥과 밀접하게 연결되어 있으며, 이러한 핵심 수치를 시각적으로 제시하여 독자가 서보 구성를 더 잘 이해하도록 돕습니다.](../en/images/d09-03.png)

![이 이미지는 "STS3215"라고 표기된 네 개의 서보 박스를 보여줍니다. 각 박스에는 "SPECIFICATION"이라는 단어가 인쇄되어 있고 토크, 속도, 치수 등의 파라미터가 포함되어 있으며, 예를 들어 토크 9.2kg·cm/127.98oz·in(6V)입니다. STS3215-C001은 토크 12.5kg·cm/173.88oz·in(6V), STS3215-C046은 토크 16kg·cm/220.58oz·in(7V)입니다. 이 서보들은 팔의 Follower 암 모든 관절에 사용되는 모델로, 문서에서 소개하는 Follower 암에 대응하며 이후 조립 단계의 서보 설치에 사용됩니다.](../en/images/d09-04.jpg)

## 두 가지 전원 어댑터 구분

5V 6A 30W 전원 어댑터: 7.4V 서보 (Leader 암)에 전원을 공급하며, 검은색입니다

12V 5A 60W 전원 어댑터: 12V 서보 (Follower 암)에 전원을 공급하며, 흰색입니다

## Feetech 서보 디버깅 도구 다운로드

### Windows PC

https://gitee.com/ftservo/fddebug

[`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z)를 다운로드하여 압축을 풀고, 그 안의 exe 프로그램을 실행하십시오

### Ubuntu 및 Mac (압축 파일에 튜토리얼이 포함되어 있습니다)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![이 이미지는 SO-ARM101 로봇 팔 키트 조립 튜토리얼의 보조 도해로, 전원 어댑터를 구분하는 섹션에 대응합니다. 두 가지 서보 모델 STS3215-C001과 STS3215-C018 및 그 장착 위치를 보여주며, 팔의 서로 다른 관절에 대응하는 STS3215-C004 등의 서보도 표시합니다. 이 그림에는 회전 속도, 스톨 토크, 서보 정밀도, 보호 기능, 파라미터 피드백을 포함한 두 서보의 파라미터도 나열되어 있어, 팔 조립 시 서보 선택과 설치를 위한 참고 자료를 제공합니다.](../en/images/d09-05.jpg)

**프로 버전: Leader 암은 5V6A 전원 어댑터를, Follower 암은 12V5A 전원 어댑터를 사용합니다**

서보 ID 설정, 서보 각도 캘리브레이션, 조립은 사전에 완료해야 합니다. [공식 조립 튜토리얼](https://huggingface.co/docs/lerobot/so101)을 참고하십시오

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# 1단계: 서보 ID 설정 및 서보 혼 설치 (서보 5 제외)

<grid>
<column width-ratio="0.500000">
![이 이미지는 Feetech 상위 디버깅 도구 인터페이스를 보여줍니다. 인터페이스에는 "Debug", "Program", "Upgrade" 세 개의 탭이 있고 현재 "Program"이 선택되어 있습니다. 핵심 정보: 1. 통신 설정에서 포트 번호는 COM6, 보드레이트는 1000000입니다. 2. 서보 작업에서 동기 쓰기, 비동기 쓰기, 토크 출력이 모두 체크되어 있습니다. 3. 서보 피드백에서 전압, 전류, 온도, 위치 등의 파라미터가 모두 0으로 표시됩니다. 4. 서보 검색에서 id 1이 선택되어 있고 모델은 ST53215입니다. 이 이미지는 위에서 설명한 서보 ID 설정과 서보 혼 설치 등의 디버깅 작업과 관련이 있으며, 디버깅 도구 인터페이스를 제시합니다.](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![이 이미지는 서보 ID 설정에 사용되는 Feetech 상위 디버깅 도구 인터페이스를 보여줍니다. 인터페이스에는 "Debug", "Program", "Upgrade" 세 개의 탭이 있고 현재 "Program"이 선택되어 있습니다. "Center calibration" 영역에서 ID 번호는 4이고 오른쪽에 "Save" 버튼이 있습니다. 인터페이스 왼쪽에는 서보 ID, 모델 등의 정보가 표시됩니다. 이 이미지는 문서의 "1단계: 서보 ID 설정 및 서보 혼 설치 (서보 5 제외)" 내용과 관련이 있으며, 서보 ID 설정 작업의 인터페이스를 제시하여 ID 번호를 어디에서 설정하는지 시각적으로 보여줍니다.](../en/images/d09-07.png)
</column>
</grid>

1. Feetech 상위 디버깅 도구를 열고 COM 포트를 선택한 뒤, 보드레이트를 백만으로 설정하고 "Open"을 클릭합니다
2. "Search"를 클릭합니다. "STS3215"가 나타나면 "Stop"을 클릭한 다음 "STS3215"를 클릭합니다
3. 상단에서 "Debug"를 선택합니다. 슬라이더를 끌어 서보를 회전시킬 수 있고, "Scan"을 클릭하면 앞뒤로 움직이게 할 수 있습니다. 서보가 정상적으로 동작하는지 확인합니다
4. 상단에서 "Program"을 선택합니다
5. "Center calibration"을 클릭해 서보의 현재 회전축 위치를 중심 (0-4095)으로 설정합니다
6. "ID"를 클릭하고 우측 하단에서 해당 서보의 ID 번호를 설정한 뒤 "Save"를 클릭합니다. 번호는 문자가 아닌 순수 아라비아 숫자입니다
7. 서보와 제어 보드를 연결하는 케이블을 분리합니다
8. 서보 케이블을 서보에 꽂습니다

서보 1에는 두 개의 케이블이 연결됩니다. 나머지 서보에는 지금은 케이블 하나만 연결합니다

![이 이미지는 SO-ARM101 암 키트 조립 중의 서보 설치를 보여줍니다. 프레임에는 Follower 암과 Leader 암이 있으며, Follower 암은 123456, Leader 암은 123456으로 번호가 매겨져 있습니다. 서보에는 감속비 1:345, 1:191, 1:147이 표시되어 있습니다. 아래에는 제어 보드가 있고 흰색과 검은색 케이블 두 개가 연결되어 있습니다. 이 이미지는 위의 조립 단계와 관련이 있으며, 서보의 장착 위치와 번호를 시각적으로 제시하여 조립자가 서보와 제어 보드를 정확하게 맞추도록 돕습니다.](../en/images/d09-08.png)

<callout emoji="💡">
다시 강조합니다: 각 서보의 관절 ID와 감속비가 **SO-ARM101**과 정확히 일치하는지 확인하십시오.
</callout>

버스 위의 모든 모터는 고유한 ID를 가집니다. 새 모터는 보통 기본 ID `1`로 출고됩니다. 모터와 컨트롤러 간의 통신이 작동하도록 하려면 먼저 각 모터에 고유한 ID를 설정해야 합니다. 또한 버스의 데이터 전송 속도는 보드레이트로 결정됩니다. 서로 통신하려면 컨트롤러와 모든 모터가 동일한 보드레이트로 설정되어야 합니다. 이 팔의 서보는 보드레이트 100000을 사용합니다.

이를 위해 먼저 컨트롤러를 각 모터에 차례로 연결하여 설정할 수 있어야 합니다. 이 파라미터들은 모터 내부 메모리 (EEPROM)의 비휘발성 영역에 기록되므로 한 번만 하면 됩니다.

다른 로봇에서 사용하던 모터를 재사용하는 경우에도 이 단계가 필요할 수 있습니다. ID와 보드레이트가 맞지 않을 수 있기 때문입니다.

아래 동영상은 모터 ID 설정 단계의 순서를 보여줍니다.

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Feetech 서보 상위 도구로 서보 ID를 설정하고 중심을 캘리브레이션하십시오. ID는 1부터 6까지 순서로 설정합니다!

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu 및 Mac

<callout emoji="💡">
Feetech 서보 상위 도구가 필요하면 위의 [Feetech 서보 디버깅 도구](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb)를 참고하십시오
</callout>

먼저 [공식 LeRobot 설치](https://huggingface.co/docs/lerobot/installation) 페이지에 따라 환경 설정을 완료하십시오

<callout emoji="💡">
가상 환경을 활성화하고 해당 src/lerobot 디렉터리로 이동하는 것을 잊지 마십시오
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. 팔의 USB 포트를 찾습니다. 각 팔에 맞는 올바른 포트를 찾으려면 유틸리티 스크립트를 두 번 실행하십시오::

```Plain Text
lerobot-find-port
```

Leader 암 포트를 식별할 때의 출력 예시 (예를 들어 Mac에서는 `/dev/tty.usbmodem575E0031751`, Linux에서는 `/dev/ttyACM0`일 수 있습니다):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

Follower 암 포트를 식별할 때의 출력 예시 (예를 들어 `/dev/tty.usbmodem575E0032081`, Linux에서는 `/dev/ttyACM1`일 수 있습니다):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
USB 커넥터를 뽑는 것을 잊지 마십시오. 그렇지 않으면 포트를 감지할 수 없습니다.
</callout>

2. USB 케이블로 PC를 Follower 암의 서보 드라이버 보드에 연결하고 전원을 켭니다. 그런 다음 다음 명령을 실행합니다. 명령의 --robot.port=/dev/ttyACM0을 찾은 포트로 변경하십시오. 예를 들어 찾은 포트가 /dev/ttyACM1이면 --robot.port=/dev/ttyACM1로 변경하십시오

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

다음과 같은 출력이 표시됩니다.

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

안내에 따라 그리퍼 서보를 연결합니다. 서보 드라이버 보드에 연결된 서보가 이것 하나뿐이고, 이 서보가 아직 다른 서보에 연결되지 않았는지 확인하십시오. **[Enter]** 를 누르면 스크립트가 해당 서보의 ID와 보드레이트를 자동으로 설정합니다. ID는 6부터 1까지 순서로 설정됩니다!

그러면 다음과 같은 출력이 표시됩니다:

```Python
'gripper' motor id set to 6
```

다음 출력은 다음과 같습니다:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**참고** 각 서보에 대해 위 과정을 안내에 따라 반복하십시오.
이전 서보들과 마찬가지로, 드라이버 보드에 연결된 서보가 이것 하나뿐이고 서보 자체가 다른 서보에 연결되지 않았는지 확인하십시오.
</callout>

매번 **Enter** 를 누르기 전에 케이블 연결을 반드시 확인하십시오. 예를 들어 회로 기판을 다루는 동안 전원 케이블이 느슨해질 수 있습니다.

모든 단계를 완료하면 스크립트가 자동으로 종료되고 서보를 사용할 준비가 됩니다. 이제 각 서보의 3핀 커넥터를 차례로 연결하고, 첫 번째 서보 (ID 1의 "shoulder pan" 서보)의 케이블을 드라이버 보드에 연결할 수 있습니다. 이제 드라이버 보드를 팔의 베이스에 장착할 수 있습니다.

Leader 암에 대해서도 동일한 단계를 반복하십시오.

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# 2단계: 조립

<callout emoji="💡">
- Follower 암의 조립 단계는 Leader 암과 본질적으로 동일합니다. 유일한 차이는 12단계 이후 엔드이펙터 (그리퍼와 핸들)를 다르게 설치한다는 점입니다.
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
서보 드라이버 보드 설치: 먼저 4개의 황동 스탠드오프를 장착한 뒤, 4개의 M2.5\*8 나사로 드라이버 보드를 고정하십시오
</callout>

<grid>
<column width-ratio="0.525947">
![네 개의 황동 스탠드오프를 설치합니다](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![M2.5*8 나사로 서보 드라이버 보드를 고정합니다](../en/images/d09-10.webp)
</column>
</grid>

![팔에 장착하고 배선합니다](../en/images/d09-11.png)

**프로 버전: 검은색 Leader 암은 5V6A 전원 어댑터를, 흰색 Follower 암은 12V5A 전원 어댑터를 사용합니다**








# 웹 UI에서 서보 ID 설정 및 중심 캘리브레이션

https://bambot.org/feetech.js?lang=zh

1. 서보 모델에 따라 0 또는 1을 입력한 뒤 "Connect"를 클릭합니다

![이 이미지는 팔 키트 조립 튜토리얼의 "Connect" 인터페이스를 보여줍니다. 인터페이스 왼쪽에는 "Connect"라는 단어가 있고, 오른쪽에는 1,000,000 bps (Index 0)로 설정된 "Baud rate" 드롭다운과 0으로 설정된 "Protocol end (0=STS/SMS, 1=SCS)" 입력란이 있으며, 입력란 옆의 숫자 "1" 주위에 빨간 상자가 그려져 있습니다. 아래에는 초록색 "Connect" 버튼이 있고 그 옆의 숫자 "2" 주위에도 빨간 상자가 있습니다. 하단에는 "Status: Disconnected"가 표시됩니다. 이 이미지는 위의 "서보 모델에 따라 0 또는 1을 입력한 뒤 'Connect'를 클릭합니다" 내용에 대응하며, 연결 작업의 설정을 시각적으로 제시합니다.](../en/images/d09-12.png)

2. ID 1\~6의 서보를 스캔합니다. 스캔 결과에서 FOUND를 사용해 해당 ID 서보를 확인합니다. 예를 들어 이미지에서는 서보 ID 1이 발견되었습니다

![이 이미지는 SO-ARM101 암 키트 조립 튜토리얼의 "Scan servos" 단계 인터페이스를 보여줍니다. 인터페이스 상단에는 "Start ID"와 "End ID" 입력란이 있고 현재 시작 ID 1, 종료 ID 6으로 설정되어 있습니다. 아래에는 "Start scan" 버튼이 있습니다. 스캔 결과에서는 ID 1-6을 스캔해도 서보가 발견되지 않아 "Exception: No status packet! Error code: 0"이라고 보고됩니다. 이 이미지는 문맥과 밀접하게 연결되어 있으며, 서보 스캔 시의 인터페이스와 결과를 시각적으로 제시하여 사용자가 서보 스캔 상태를 이해하도록 돕습니다.](../en/images/d09-13.png)

3. ID 설정 및 중심 캘리브레이션

① 현재 서보 ID 입력란을 스캔한 서보의 ID로 설정합니다

② "ID management"에 숫자를 입력하고 "Change ID"를 클릭해 ID를 설정합니다

③ 중심 캘리브레이션 (STS3215 서보의 중심은 2047, SCS0009 서보의 중심은 511입니다)

STS 서보: "Position control"에 2047을 입력하고 "Set"을 클릭합니다

SCS 서보: "Position control"에 511을 입력하고 "Set"을 클릭합니다

![이 이미지는 단일 서보 제어 인터페이스를 보여줍니다. 현재 서보 ID는 1이며, ID management에 숫자 1을 입력하고 "Change ID"를 클릭하면 "Success: ID changed to 1"이라는 메시지가 나타납니다. Position Control에서 값은 2047이고 "Set" 버튼을 클릭하면 적용됩니다. 이 이미지는 "ID 설정 및 중심 캘리브레이션" 문맥과 관련이 있으며, ID 설정 작업의 인터페이스를 시각적으로 제시하여 사용자가 "ID management"에 숫자를 입력해 ID를 설정하고 "Position control"에 중심값을 입력한 뒤 "Set"을 클릭해 완료하는 방법을 이해하도록 돕습니다.](../en/images/d09-14.png)
