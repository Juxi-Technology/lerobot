English | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | [Deutsch](../de/servo-calibration-tool.md) | [Español](../es/servo-calibration-tool.md) | [Français](../fr/servo-calibration-tool.md) | [Italiano](../it/servo-calibration-tool.md) | [日本語](../ja/servo-calibration-tool.md) | [한국어](../ko/servo-calibration-tool.md) | [Português (BR)](../pt-br/servo-calibration-tool.md) | [Português (PT)](../pt-pt/servo-calibration-tool.md)

# STS3215 Servo Calibration Tool for the So-ARM Series (optional)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**An FTServo servo factory-calibration and LeRobot calibration toolkit designed for So-ARM 10X series arms**

> ⚠️ **Compatibility note: this system currently supports only Feetech (STS3215 series) servos**. The register table, xdat parameter format and baud-rate table are all designed for the Feetech STS3215 series.

> 📜 **Origin and credits: this tool is adapted and upgraded from** [**Seeed Studio's Seeed_RoboController**](https://github.com/Seeed-Studio) **project**, originally released under the MIT license. While keeping the original core functionality, this project refactors the GUI and adds the FT debugger, xdat parameter backup/restore, cross-platform support, Chinese/English switching and other enhancements.

---

## ✨ Features

| Feature | Description |
|-|-|
| Automatic port detection | Intelligently detects USB serial ports and filters out virtual devices |
| Cross-platform support | Compatible across Windows / Ubuntu / macOS |
| Dual-port sync | The left and right serial ports operate independently, with support for synchronized leader/follower dual-port remote control |
| Chinese/English switching | One-click switch between Chinese/English in the UI, with the choice remembered automatically |
| Center calibration | Burns the servo's current position as the 2048 center (persisted to EEPROM) |
| Center test | Enables torque and moves the servo to the center to verify the calibration result |
| Disable motors | One-click disables torque on all servos for easy manual adjustment |
| Auto scan | Automatically detects all online servos within ID 1–20 |
| Single-servo control | A slider controls one servo's position and torque on/off in real time |
| FT debugger | Serial connection, scanning, parameter read/write, position control, baud-rate change, factory reset, xdat parameter backup |
| xdat parameters | Save the current servo EEPROM parameters / open a backup to restore |
| LeRobot calibration | Generates LeRobot-format JSON calibration files |
| Run to center from a calibration file | Moves the arm to the center based on a calibration file |

---

## 📚 Detailed Tutorials

### Chinese

| OS | Tutorial |
|-|-|
| Windows | \[Windows tutorial\](docs/zh/Windows教程.md) |
| Linux | \[Linux tutorial\](docs/zh/Linux教程.md) |
| macOS | \[macOS tutorial\](docs/zh/macOS教程.md) |

### English

| OS | Guide |
|-|-|
| Windows | \[Windows Guide\](docs/en/Windows.md) |
| Linux | \[Linux Guide\](docs/en/Linux.md) |
| macOS | \[macOS Guide\](docs/en/macOS.md) |

---

## 🖥️ Interface Overview

The main program has three tabs:

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

- **Top bar**: app title, port-selection dropdowns, refresh button, remote-control button, language-switch button.
- **🦾 Tab1 Servo Calibration**: quick actions for the left and right panels (center calibration, center test, disable motors) plus live status.
- **🎚️ Tab2 Single-Servo Control**: fine-tune each online servo's position with a slider and toggle its torque.
- **🔬 Tab3 FT Debugger**: serial connection, scanning, parameter read/write, position control, baud rate/factory reset, xdat parameter backup and restore.

---

## 🚀 Quick Start

> For the full per-system tutorials, see \[📚 Detailed Tutorials\](#-详细教程). Below are the key points for each system.

### Windows

1. Install [Python 3.10+](https://www.python.org/downloads/) (check **Add to PATH**)
2. Create a virtual environment and install dependencies:

```Bash
cd Juxi_ServoController
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

1. Check the environment and launch:

```Bash
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Confirm the port number in Device Manager (e.g. `COM3`) and select it in the top bar. To specify ports manually:

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux (Ubuntu / Debian)

1. Install CJK fonts and dependencies:

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ Add serial port permissions (dialout group)** [required]:

```Bash
sudo usermod -a -G dialout $USER
# Takes effect after you log out and back in
```

1. Create a virtual environment, install dependencies and launch:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. The serial devices are `/dev/ttyUSB0` / `/dev/ttyACM0`. To specify manually:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/ttyUSB0 --port2 /dev/ttyUSB1
```

### macOS

1. Install `Python` with `Homebrew `:

```Bash
brew install python
```

1. Create a virtual environment, install dependencies and launch:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. **⚠️ Serial port naming**: on macOS use `/dev/cu.usbserial-*` (**recommended, non-blocking**) rather than `/dev/tty.*`. To list them:

```Bash
ls /dev/cu.*
```

To specify manually:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### General command-line tools (no GUI needed)

```Bash
# Scan servos
python -m src.tools.scan_id

# Quick servo center calibration
python -m src.tools.servo_quick_calibration

# Servo center test
python -m src.tools.servo_center_test

# Disable all servos
python -m src.tools.servo_disable

# LeRobot-style calibration
python -m src.tools.lerobot_calibrate

# Dual-port synchronized remote control
python -m src.tools.servo_remote_control
```

---

## 📖 Usage Steps

### 1. Connect and detect servos

1. Connect the arm's control board through a USB-to-serial adapter and power the servos.
2. Open the GUI and select the port in the top-bar dropdown (or click `🔄` to refresh).
3. The top of the panel shows `🟢 Connected` and automatically scans for online servos within ID 1–20 (usually 1–6).

> If it reports that the port is busy, make sure no other program (a serial monitor, a previously opened tool that did not exit) is using it.

### 2. Center calibration (set the current position to 2048)

> Before calibrating, physically pose the arm so that each joint is at the "zero / center" position you want.

1. Click the **PortX Center Calibration** button on the panel.
2. The program first disables the servos and prompts you to manually move them to the desired center.
3. After you confirm, the program performs, for each servo: unlock EEPROM → write the calibration command (value 128 to address 40) → relock EEPROM.
4. After calibration, use "Center test" to verify: the servo should stay in place (very little movement), which means the calibration succeeded.

### 3. Center test

1. Click **PortX Center Test**.
2. The program enables torque and moves all servos to 2048.
3. If the servos barely move from their current position, the calibration is correct; if they move a lot, the calibration value is unreliable and needs to be redone.

### 4. Disable motors (manual adjustment)

- Click **PortX Disable Motors** to turn off torque for all servos on that port so they can be rotated freely by hand.
- For a single servo, toggle its torque individually in the **Single-Servo Control** page using the torque switch below the slider.

### 5. Change a servo ID

1. Go to the **🔬 FT Debugger** page, connect the serial port and scan for servos.
2. Select the target servo, change the "Servo ID" value (address 0x05) in the parameter table, and click write.
3. The program performs: unlock → write to address 5 → verify the new ID → relock.

> ⚠️ Before changing an ID, make sure this is the only servo on the bus to avoid ID conflicts.

### 6. Change baud rate / factory reset

- **Change baud rate**: in the "Baud rate / factory reset" area of the FT Debugger page, select the new baud rate (38400 – 1000000 bps) and apply it. After writing, the serial baud rate is switched automatically and verified by ping; on failure it rolls back automatically.
- **Factory reset**: the servo returns to factory defaults (ID=1, baud rate=1000000); rescan afterwards.

### 7. xdat parameter backup and restore

In the "xdat parameters (EEPROM only)" area of the FT Debugger page:

1. **💾 Save current servo**: save the currently selected servo's EEPROM parameters to an xdat file (backup).
2. After changing servo parameters freely, if you want to restore:
3. **📂 Open xdat**: load the backup file.
4. **📤 Restore parameters to servo**: write the backup back to the current servo's EEPROM.

### 8. Dual-port synchronized remote control

> ⚠️ **Direction: Port 1 controls Port 2**. Port 1 (leader) only reads servo angles; Port 2 (follower) is controlled in sync.

1. Click **🎮 Remote** in the top bar (Port 1 reads angles → Port 2 synchronously controls the servos with the same IDs).
2. Both ports must have matching servo IDs; only servos in the intersection are synchronized.
3. Click the same button again to stop; afterwards the left and right panel scan threads resume automatically.

### 9. LeRobot calibration (command line)

```Bash
# Calibrate the follower arm (saved to ~/.cache/huggingface/lerobot/calibration/robots/so_follower/)
python -m src.tools.lerobot_calibrate --arm-type follower

# Calibrate the leader arm
python -m src.tools.lerobot_calibrate --arm-type leader
```

Flow: disable servos → move each joint to the center and record `homing_offset` → slowly sweep the full travel and record `range_min/max` (`wrist_roll` is a continuous-rotation joint with a fixed range of `[0,4095]`) → save the JSON.

Run to the center using a calibration file:

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ Notes



1. **Safety first**: center calibration persists to EEPROM. Before calibrating, make sure the power supply is stable and the arm will not collide with people or objects.
2. **Power**: for the standard SoARM 101, DC 5V 5A is recommended; for the Pro version, DC 12V 5A. Insufficient power causes servo step loss or communication failures.
3. **Serial port exclusivity**: on Windows the port is locked exclusively, so the same port cannot be used by both the GUI scan thread and the calibration subprocess at the same time. The tool automatically stops the scan thread and ends the old process before operating; do not click repeatedly by hand.
4. **Linux serial permissions**: accessing `/dev/ttyUSB*` / `/dev/ttyACM*` requires adding the user to the `dialout` group (see the \[Linux tutorial\](docs/zh/Linux教程.md)).
5. **macOS serial naming**: use `/dev/cu.*` (non-blocking) rather than `/dev/tty.*` (blocking, may hang); see the \[macOS tutorial\](docs/zh/macOS教程.md).
6. **Hot-plugging**: after unplugging the USB the program tries to reconnect automatically; after plugging it back in, click `🔄` to refresh the port list.
7. **Over-temperature / over-voltage protection**: the program monitors voltage and temperature (alarm above 60°C). If the servos stay hot, stop and let them cool.
8. **Center calibration is irreversible**: after writing, the original offset is overwritten and cannot be undone. Record the original position first before calibrating.
9. **ID change risk**: if the write or verification fails, the program reports an error and resumes scanning, but in extreme cases the servo may be "lost". If that happens, try "Factory reset" (after reset the ID returns to 1).
10. **Encoding issue**: if emoji appear garbled in the Windows console, set `PYTHONIOENCODING=utf-8` before running the command-line tools. Linux/macOS with native UTF-8 generally do not have this problem.

---

## 🛠️ Troubleshooting

| Symptom | Possible cause | Solution |
|-|-|-|
| Cannot open the serial port / port busy | Another program is using it | Close programs such as serial monitors, or switch ports and restart the tool |
| No servos found in scan | Insufficient power / wrong wiring / baud-rate mismatch | Check the power and wiring, and confirm the servos are at 1M baud rate |
| Servos run wild after center calibration | The pose was not set correctly before calibration | Redo "disable → manually pose → center calibration" |
| Temperature rises too fast | Excessive load or stall | Check the mechanism for binding; reduce speed/acceleration |
| Servo not found after changing its ID | ID conflict or write failure | Factory reset and rescan |
| Remote control out of sync | The two ports have mismatched IDs | Confirm that servos with the same ID are online on both the leader and follower ports |

---

## 📁 Directory Structure

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
