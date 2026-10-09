[English](../en/servo-calibration-tool.md) | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | [Deutsch](../de/servo-calibration-tool.md) | [Español](../es/servo-calibration-tool.md) | [Français](../fr/servo-calibration-tool.md) | [Italiano](../it/servo-calibration-tool.md) | [日本語](../ja/servo-calibration-tool.md) | 한국어 | [Português (BR)](../pt-br/servo-calibration-tool.md) | [Português (PT)](../pt-pt/servo-calibration-tool.md)

# So-ARM 시리즈용 STS3215 서보 캘리브레이션 도구 (선택 사항)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**So-ARM 10X 시리즈 팔을 위해 설계된 FTServo 서보 공장 캘리브레이션 및 LeRobot 캘리브레이션 툴킷**

> ⚠️ **호환성 주의: 이 시스템은 현재 Feetech (STS3215 시리즈) 서보만 지원합니다**. 레지스터 테이블, xdat 파라미터 형식, 보드레이트 테이블은 모두 Feetech STS3215 시리즈를 위해 설계되었습니다.

> 📜 **출처 및 크레딧: 이 도구는** [**Seeed Studio의 Seeed_RoboController**](https://github.com/Seeed-Studio) **프로젝트를 각색하고 업그레이드한 것**으로, 원래 MIT 라이선스로 공개되었습니다. 원래의 핵심 기능을 유지하면서 GUI를 리팩터링하고 FT 디버거, xdat 파라미터 백업/복원, 크로스플랫폼 지원, 중국어/영어 전환 등의 개선 사항을 추가했습니다.

---

## ✨ 기능

| 기능 | 설명 |
|-|-|
| 자동 포트 감지 | USB 시리얼 포트를 지능적으로 감지하고 가상 디바이스를 걸러냅니다 |
| 크로스플랫폼 지원 | Windows / Ubuntu / macOS 전반에서 호환됩니다 |
| 듀얼 포트 동기화 | 좌우 시리얼 포트가 독립적으로 동작하며, Leader/Follower 듀얼 포트 동기 원격 제어를 지원합니다 |
| 중국어/영어 전환 | UI에서 원클릭으로 중국어/영어를 전환하며, 선택 사항이 자동으로 기억됩니다 |
| 중심 캘리브레이션 | 서보의 현재 위치를 2048 중심으로 기록합니다 (EEPROM에 영구 저장) |
| 중심 테스트 | 토크를 활성화하고 서보를 중심으로 이동시켜 캘리브레이션 결과를 검증합니다 |
| 모터 비활성화 | 원클릭으로 모든 서보의 토크를 해제해 수동 조정을 쉽게 합니다 |
| 자동 스캔 | ID 1–20 범위의 모든 온라인 서보를 자동으로 감지합니다 |
| 단일 서보 제어 | 슬라이더로 한 서보의 위치와 토크 온/오프를 실시간 제어합니다 |
| FT 디버거 | 시리얼 연결, 스캔, 파라미터 읽기/쓰기, 위치 제어, 보드레이트 변경, 공장 초기화, xdat 파라미터 백업 |
| xdat 파라미터 | 현재 서보 EEPROM 파라미터를 저장하거나 백업을 열어 복원합니다 |
| LeRobot 캘리브레이션 | LeRobot 형식의 JSON 캘리브레이션 파일을 생성합니다 |
| 캘리브레이션 파일로 중심으로 이동 | 캘리브레이션 파일을 기반으로 팔을 중심으로 이동시킵니다 |

---

## 📚 상세 튜토리얼

### 중국어

| OS | 튜토리얼 |
|-|-|
| Windows | \[Windows 튜토리얼\](docs/zh/Windows教程.md) |
| Linux | \[Linux 튜토리얼\](docs/zh/Linux教程.md) |
| macOS | \[macOS 튜토리얼\](docs/zh/macOS教程.md) |

### 영어

| OS | 가이드 |
|-|-|
| Windows | \[Windows 가이드\](docs/en/Windows.md) |
| Linux | \[Linux 가이드\](docs/en/Linux.md) |
| macOS | \[macOS 가이드\](docs/en/macOS.md) |

---

## 🖥️ 인터페이스 개요

메인 프로그램에는 세 개의 탭이 있습니다:

```Plain Text
┌─────────────────────────────────────────────────────────────┐
│  SoARM Series Calibration Tool  [Port1▾] [Port2▾] [🔄]  [🎮Remote][EN]│  ← Top bar
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────┬──────────────────────────────┐ │
│  │ Port1 - Servo Calib.    │ Port2 - Servo Calib.         │ │
│  │  [🔴Disconnected] Cur:… │  [🔴Disconnected] Cur:…      │ │
│  │  Servo1~6 status table  │  Servo1~6 status table       │ │
│  │  [CenterCal][CenterTest]│  [CenterCal][CenterTest]…    │ │
│  └─────────────────────────┴──────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

- **상단 바**: 앱 제목, 포트 선택 드롭다운, 새로 고침 버튼, 원격 제어 버튼, 언어 전환 버튼.
- **🦾 Tab1 서보 캘리브레이션**: 좌우 패널의 빠른 작업 (중심 캘리브레이션, 중심 테스트, 모터 비활성화)과 실시간 상태.
- **🎚️ Tab2 단일 서보 제어**: 슬라이더로 각 온라인 서보의 위치를 미세 조정하고 토크를 전환합니다.
- **🔬 Tab3 FT 디버거**: 시리얼 연결, 스캔, 파라미터 읽기/쓰기, 위치 제어, 보드레이트/공장 초기화, xdat 파라미터 백업 및 복원.

---

## 🚀 빠른 시작

> 시스템별 전체 튜토리얼은 \[📚 상세 튜토리얼\](#-详细教程)을 참고하십시오. 아래는 각 시스템의 핵심 사항입니다.

### Windows

1. [Python 3.10+](https://www.python.org/downloads/)를 설치합니다 (**Add to PATH** 체크)
2. 가상 환경을 만들고 의존성을 설치합니다:

```Bash
cd Juxi_ServoController
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

1. 환경을 확인하고 실행합니다:

```Bash
python setup.py
python -m src.gui.factory_calibration_tool
```

1. 장치 관리자에서 포트 번호 (예: `COM3`)를 확인하고 상단 바에서 선택합니다. 포트를 수동으로 지정하려면:

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux (Ubuntu / Debian)

1. CJK 폰트와 의존성을 설치합니다:

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ 시리얼 포트 권한 (dialout 그룹) 추가** [필수]:

```Bash
sudo usermod -a -G dialout $USER
# 로그아웃 후 다시 로그인하면 적용됩니다
```

1. 가상 환경을 만들고 의존성을 설치한 뒤 실행합니다:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. 시리얼 디바이스는 `/dev/ttyUSB0` / `/dev/ttyACM0`입니다. 수동으로 지정하려면:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/ttyUSB0 --port2 /dev/ttyUSB1
```

### macOS

1. `Homebrew `로 `Python`을 설치합니다:

```Bash
brew install python
```

1. 가상 환경을 만들고 의존성을 설치한 뒤 실행합니다:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. **⚠️ 시리얼 포트 명명**: macOS에서는 `/dev/tty.*` 대신 `/dev/cu.usbserial-*` (**권장, 비블로킹**)를 사용하십시오. 목록을 보려면:

```Bash
ls /dev/cu.*
```

수동으로 지정하려면:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### 일반 명령줄 도구 (GUI 불필요)

```Bash
# 서보 스캔
python -m src.tools.scan_id

# 빠른 서보 중심 캘리브레이션
python -m src.tools.servo_quick_calibration

# 서보 중심 테스트
python -m src.tools.servo_center_test

# 모든 서보 비활성화
python -m src.tools.servo_disable

# LeRobot 형식 캘리브레이션
python -m src.tools.lerobot_calibrate

# 듀얼 포트 동기 원격 제어
python -m src.tools.servo_remote_control
```

---

## 📖 사용 단계

### 1. 서보 연결 및 감지

1. USB-시리얼 어댑터를 통해 팔의 제어 보드를 연결하고 서보에 전원을 공급합니다.
2. GUI를 열고 상단 바 드롭다운에서 포트를 선택합니다 (또는 `🔄`를 클릭해 새로 고칩니다).
3. 패널 상단에 `🟢 Connected`가 표시되고 ID 1–20 범위 (보통 1–6)의 온라인 서보를 자동으로 스캔합니다.

> 포트가 사용 중이라고 보고되면 다른 프로그램 (시리얼 모니터, 종료되지 않은 이전 도구 등)이 포트를 사용하고 있지 않은지 확인하십시오.

### 2. 중심 캘리브레이션 (현재 위치를 2048로 설정)

> 캘리브레이션 전에 각 관절이 원하는 "영점 / 중심" 위치에 오도록 팔의 자세를 물리적으로 잡으십시오.

1. 패널에서 **PortX Center Calibration** 버튼을 클릭합니다.
2. 프로그램이 먼저 서보를 비활성화하고, 원하는 중심으로 수동 이동하라는 안내를 표시합니다.
3. 확인하면 프로그램이 각 서보에 대해 다음을 수행합니다: EEPROM 잠금 해제 → 캘리브레이션 명령 기록 (값 128을 주소 40에) → EEPROM 재잠금.
4. 캘리브레이션 후 "Center test"로 검증하십시오. 서보가 제자리에 머물면 (움직임이 거의 없으면) 캘리브레이션이 성공한 것입니다.

### 3. 중심 테스트

1. **PortX Center Test**를 클릭합니다.
2. 프로그램이 토크를 활성화하고 모든 서보를 2048로 이동시킵니다.
3. 서보가 현재 위치에서 거의 움직이지 않으면 캘리브레이션이 올바른 것이고, 많이 움직이면 캘리브레이션 값이 신뢰할 수 없으므로 다시 해야 합니다.

### 4. 모터 비활성화 (수동 조정)

- **PortX Disable Motors**를 클릭하면 해당 포트의 모든 서보 토크가 꺼져 손으로 자유롭게 회전시킬 수 있습니다.
- 단일 서보의 경우 **Single-Servo Control** 페이지에서 슬라이더 아래의 토크 스위치로 개별적으로 토크를 전환합니다.

### 5. 서보 ID 변경

1. **🔬 FT Debugger** 페이지로 이동해 시리얼 포트를 연결하고 서보를 스캔합니다.
2. 대상 서보를 선택하고 파라미터 테이블에서 "Servo ID" 값 (주소 0x05)을 변경한 뒤 쓰기를 클릭합니다.
3. 프로그램이 다음을 수행합니다: 잠금 해제 → 주소 5에 쓰기 → 새 ID 검증 → 재잠금.

> ⚠️ ID를 변경하기 전에 이 서보가 버스 위의 유일한 서보인지 확인해 ID 충돌을 피하십시오.

### 6. 보드레이트 변경 / 공장 초기화

- **보드레이트 변경**: FT Debugger 페이지의 "Baud rate / factory reset" 영역에서 새 보드레이트 (38400 – 1000000 bps)를 선택하고 적용합니다. 기록 후 시리얼 보드레이트가 자동으로 전환되고 ping으로 검증되며, 실패하면 자동으로 롤백됩니다.
- **공장 초기화**: 서보가 공장 기본값으로 되돌아갑니다 (ID=1, 보드레이트=1000000). 이후 다시 스캔하십시오.

### 7. xdat 파라미터 백업 및 복원

FT Debugger 페이지의 "xdat parameters (EEPROM only)" 영역에서:

1. **💾 Save current servo**: 현재 선택된 서보의 EEPROM 파라미터를 xdat 파일로 저장합니다 (백업).
2. 서보 파라미터를 자유롭게 변경한 뒤 복원하려면:
3. **📂 Open xdat**: 백업 파일을 불러옵니다.
4. **📤 Restore parameters to servo**: 백업을 현재 서보의 EEPROM에 다시 기록합니다.

### 8. 듀얼 포트 동기 원격 제어

> ⚠️ **방향: 포트 1이 포트 2를 제어합니다**. 포트 1 (Leader)은 서보 각도만 읽고, 포트 2 (Follower)가 동기로 제어됩니다.

1. 상단 바에서 **🎮 Remote**를 클릭합니다 (포트 1이 각도를 읽음 → 포트 2가 동일한 ID의 서보를 동기로 제어).
2. 두 포트에 일치하는 서보 ID가 있어야 하며, 교집합에 있는 서보만 동기화됩니다.
3. 같은 버튼을 다시 클릭하면 중지되며, 이후 좌우 패널 스캔 스레드가 자동으로 재개됩니다.

### 9. LeRobot 캘리브레이션 (명령줄)

```Bash
# Follower 암 캘리브레이션 (~/.cache/huggingface/lerobot/calibration/robots/so_follower/에 저장됩니다)
python -m src.tools.lerobot_calibrate --arm-type follower

# Leader 암 캘리브레이션
python -m src.tools.lerobot_calibrate --arm-type leader
```

흐름: 서보 비활성화 → 각 관절을 중심으로 이동해 `homing_offset` 기록 → 전체 행정을 천천히 스윕하며 `range_min/max` 기록 (`wrist_roll`은 연속 회전 관절로 범위가 `[0,4095]`로 고정) → JSON 저장.

캘리브레이션 파일을 사용해 중심으로 이동:

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ 주의 사항



1. **안전 우선**: 중심 캘리브레이션은 EEPROM에 영구 저장됩니다. 캘리브레이션 전에 전원 공급이 안정적이고 팔이 사람이나 물체와 충돌하지 않을지 확인하십시오.
2. **전원**: 표준 SoARM 101은 DC 5V 5A를 권장하고, 프로 버전은 DC 12V 5A입니다. 전원이 부족하면 서보 스텝 로스나 통신 실패가 발생합니다.
3. **시리얼 포트 배타성**: Windows에서는 포트가 배타적으로 잠기므로, 같은 포트를 GUI 스캔 스레드와 캘리브레이션 하위 프로세스가 동시에 사용할 수 없습니다. 도구는 작업 전에 스캔 스레드를 자동으로 중지하고 이전 프로세스를 종료하므로, 손으로 반복해서 클릭하지 마십시오.
4. **Linux 시리얼 권한**: `/dev/ttyUSB*` / `/dev/ttyACM*`에 접근하려면 사용자를 `dialout` 그룹에 추가해야 합니다 (\[Linux 튜토리얼\](docs/zh/Linux教程.md) 참고).
5. **macOS 시리얼 명명**: `/dev/tty.*` (블로킹, 멈출 수 있음) 대신 `/dev/cu.*` (비블로킹)를 사용하십시오. \[macOS 튜토리얼\](docs/zh/macOS教程.md)을 참고하십시오.
6. **핫 플러그**: USB를 뽑으면 프로그램이 자동으로 재연결을 시도합니다. 다시 꽂은 후 `🔄`를 클릭해 포트 목록을 새로 고치십시오.
7. **과온 / 과전압 보호**: 프로그램은 전압과 온도를 모니터링합니다 (60°C 초과 시 알람). 서보가 뜨거운 상태로 유지되면 멈추고 식히십시오.
8. **중심 캘리브레이션은 되돌릴 수 없음**: 기록 후 원래 오프셋이 덮어써지고 복구할 수 없습니다. 캘리브레이션 전에 원래 위치를 먼저 기록하십시오.
9. **ID 변경 위험**: 쓰기나 검증이 실패하면 프로그램이 오류를 보고하고 스캔을 재개하지만, 극단적인 경우 서보를 "잃을" 수 있습니다. 그런 경우 "Factory reset"을 시도하십시오 (초기화 후 ID는 1로 돌아갑니다).
10. **인코딩 문제**: Windows 콘솔에서 이모지가 깨져 보이면 명령줄 도구를 실행하기 전에 `PYTHONIOENCODING=utf-8`을 설정하십시오. 네이티브 UTF-8을 사용하는 Linux/macOS는 일반적으로 이 문제가 없습니다.

---

## 🛠️ 문제 해결

| 증상 | 가능한 원인 | 해결 방법 |
|-|-|-|
| 시리얼 포트를 열 수 없음 / 포트 사용 중 | 다른 프로그램이 사용 중 | 시리얼 모니터 등의 프로그램을 닫거나, 포트를 바꾸고 도구를 재시작합니다 |
| 스캔에서 서보를 찾지 못함 | 전원 부족 / 배선 오류 / 보드레이트 불일치 | 전원과 배선을 확인하고 서보가 1M 보드레이트인지 확인합니다 |
| 중심 캘리브레이션 후 서보가 폭주함 | 캘리브레이션 전에 자세를 올바르게 설정하지 않음 | "비활성화 → 수동 자세 → 중심 캘리브레이션"을 다시 수행합니다 |
| 온도가 너무 빠르게 상승 | 과부하 또는 스톨 | 기구에 걸림이 없는지 확인하고 속도/가속도를 낮춥니다 |
| ID 변경 후 서보를 찾지 못함 | ID 충돌 또는 쓰기 실패 | 공장 초기화 후 다시 스캔합니다 |
| 원격 제어가 동기화되지 않음 | 두 포트의 ID가 불일치 | Leader와 Follower 포트 양쪽에 동일 ID의 서보가 온라인인지 확인합니다 |

---

## 📁 디렉터리 구조

```Plain Text
Juxi_ServoController/
├── docs/                    # Per-system tutorials (Chinese/English)
│   ├── zh/                  # Chinese tutorials
│   │   ├── Windows教程.md
│   │   ├── Linux教程.md
│   │   └── macOS教程.md
│   └── en/                  # English tutorials
│       ├── Windows.md
│       ├── Linux.md
│       └── macOS.md
├── src/
│   ├── gui/                  # PySide6 GUI
│   │   ├── factory_calibration_tool.py   # Main tool (dual-port calibration + remote control + language switching)
│   │   ├── ft_debugger.py                # FT debugger (parameter read/write / xdat backup)
│   │   ├── calibration_wizard.py         # LeRobot calibration wizard
│   │   ├── theme_utils.py                # Light theme
│   │   └── language_dialog.py            # Language-selection dialog
│   ├── tools/                # Command-line tools
│   ├── xdat_utils.py         # xdat parameter file read/write
│   ├── i18n*.py / i18n_translations/     # Chinese/English internationalization
│   ├── port_utils.py         # Serial port detection
│   └── calibration_manager.py# LeRobot calibration file management
├── scservo_sdk/              # FTServo servo communication SDK
├── requirements.txt
└── setup.py                  # Environment check script
```
