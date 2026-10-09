[English](../en/servo-calibration-tool.md) | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | Deutsch | [Español](../es/servo-calibration-tool.md) | [Français](../fr/servo-calibration-tool.md) | [Italiano](../it/servo-calibration-tool.md) | [日本語](../ja/servo-calibration-tool.md) | [한국어](../ko/servo-calibration-tool.md) | [Português (BR)](../pt-br/servo-calibration-tool.md) | [Português (PT)](../pt-pt/servo-calibration-tool.md)

# STS3215-Servo-Kalibrierungstool für die So-ARM-Serie (optional)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**Ein Toolkit zur Werkskalibrierung von FTServo-Servos und zur LeRobot-Kalibrierung, entwickelt für Arme der So-ARM-10X-Serie**

> ⚠️ **Kompatibilitätshinweis: Dieses System unterstützt derzeit nur Feetech-Servos (STS3215-Serie)**. Die Registertabelle, das xdat-Parameterformat und die Baudrate-Tabelle sind alle für die Feetech-STS3215-Serie ausgelegt.

> 📜 **Herkunft und Danksagung: Dieses Tool wurde aus dem Projekt** [**Seeed_RoboController von Seeed Studio**](https://github.com/Seeed-Studio) **übernommen und weiterentwickelt**, das ursprünglich unter der MIT-Lizenz veröffentlicht wurde. Unter Beibehaltung der ursprünglichen Kernfunktionalität überarbeitet dieses Projekt die GUI und fügt den FT-Debugger, die xdat-Parameter-Sicherung/-Wiederherstellung, plattformübergreifende Unterstützung, Umschaltung Chinesisch/Englisch und weitere Verbesserungen hinzu.

---

## ✨ Funktionen

| Funktion | Beschreibung |
|-|-|
| Automatische Port-Erkennung | Erkennt USB-seriell-Ports intelligent und filtert virtuelle Geräte heraus |
| Plattformübergreifende Unterstützung | Kompatibel mit Windows / Ubuntu / macOS |
| Dual-Port-Synchronisierung | Die linken und rechten seriellen Ports arbeiten unabhängig, mit Unterstützung für synchronisierte Leader/Follower-Dual-Port-Fernsteuerung |
| Umschaltung Chinesisch/Englisch | Ein-Klick-Umschaltung zwischen Chinesisch/Englisch in der UI, wobei die Wahl automatisch gespeichert wird |
| Mittelpunkt-Kalibrierung | Brennt die aktuelle Position des Servos als Mittelpunkt 2048 ein (dauerhaft im EEPROM gespeichert) |
| Mittelpunkt-Test | Aktiviert das Drehmoment und bewegt das Servo zum Mittelpunkt, um das Kalibrierungsergebnis zu überprüfen |
| Motoren deaktivieren | Deaktiviert mit einem Klick das Drehmoment aller Servos für einfache manuelle Anpassung |
| Automatischer Scan | Erkennt automatisch alle online befindlichen Servos im ID-Bereich 1–20 |
| Einzel-Servo-Steuerung | Ein Schieberegler steuert die Position eines Servos und das Drehmoment in Echtzeit ein/aus |
| FT-Debugger | Serielle Verbindung, Scannen, Parameter lesen/schreiben, Positionssteuerung, Baudrate ändern, Werksreset, xdat-Parameter-Sicherung |
| xdat-Parameter | Aktuelle EEPROM-Parameter des Servos speichern / eine Sicherung zum Wiederherstellen öffnen |
| LeRobot-Kalibrierung | Erzeugt JSON-Kalibrierungsdateien im LeRobot-Format |
| Zum Mittelpunkt aus einer Kalibrierungsdatei fahren | Bewegt den Arm anhand einer Kalibrierungsdatei zum Mittelpunkt |

---

## 📚 Ausführliche Tutorials

### Chinesisch

| OS | Tutorial |
|-|-|
| Windows | \[Windows tutorial\](docs/zh/Windows教程.md) |
| Linux | \[Linux tutorial\](docs/zh/Linux教程.md) |
| macOS | \[macOS tutorial\](docs/zh/macOS教程.md) |

### Englisch

| OS | Anleitung |
|-|-|
| Windows | \[Windows Guide\](docs/en/Windows.md) |
| Linux | \[Linux Guide\](docs/en/Linux.md) |
| macOS | \[macOS Guide\](docs/en/macOS.md) |

---

## 🖥️ Überblick über die Oberfläche

Das Hauptprogramm hat drei Tabs:

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

- **Obere Leiste**: App-Titel, Dropdowns zur Portauswahl, Aktualisieren-Schaltfläche, Fernsteuerungs-Schaltfläche, Sprachumschalt-Schaltfläche.
- **🦾 Tab1 Servo-Kalibrierung**: Schnellaktionen für das linke und rechte Panel (Mittelpunkt-Kalibrierung, Mittelpunkt-Test, Motoren deaktivieren) plus Live-Status.
- **🎚️ Tab2 Einzel-Servo-Steuerung**: Feinabstimmung der Position jedes online befindlichen Servos mit einem Schieberegler und Umschalten seines Drehmoments.
- **🔬 Tab3 FT-Debugger**: serielle Verbindung, Scannen, Parameter lesen/schreiben, Positionssteuerung, Baudrate/Werksreset, xdat-Parameter-Sicherung und -Wiederherstellung.

---

## 🚀 Schnellstart

> Die vollständigen Tutorials je System finden Sie unter \[📚 Ausführliche Tutorials\](#-详细教程). Nachfolgend die wichtigsten Punkte für jedes System.

### Windows

1. Installieren Sie [Python 3.10+](https://www.python.org/downloads/) (aktivieren Sie **Add to PATH**)
2. Erstellen Sie eine virtuelle Umgebung und installieren Sie die Abhängigkeiten:

```Bash
cd Juxi_ServoController
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

1. Prüfen Sie die Umgebung und starten Sie:

```Bash
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Bestätigen Sie die Portnummer im Geräte-Manager (z. B. `COM3`) und wählen Sie sie in der oberen Leiste aus. Um Ports manuell anzugeben:

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux (Ubuntu / Debian)

1. Installieren Sie CJK-Schriften und Abhängigkeiten:

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ Berechtigungen für die serielle Schnittstelle hinzufügen (Gruppe dialout)** [erforderlich]:

```Bash
sudo usermod -a -G dialout $USER
# Wird nach Ab- und erneutem Anmelden wirksam
```

1. Erstellen Sie eine virtuelle Umgebung, installieren Sie die Abhängigkeiten und starten Sie:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Die seriellen Geräte sind `/dev/ttyUSB0` / `/dev/ttyACM0`. Um sie manuell anzugeben:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/ttyUSB0 --port2 /dev/ttyUSB1
```

### macOS

1. Installieren Sie `Python` mit `Homebrew `:

```Bash
brew install python
```

1. Erstellen Sie eine virtuelle Umgebung, installieren Sie die Abhängigkeiten und starten Sie:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. **⚠️ Benennung der seriellen Schnittstelle**: Verwenden Sie unter macOS `/dev/cu.usbserial-*` (**empfohlen, nicht blockierend**) statt `/dev/tty.*`. Zum Auflisten:

```Bash
ls /dev/cu.*
```

Um sie manuell anzugeben:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### Allgemeine Kommandozeilen-Tools (ohne GUI)

```Bash
# Servos scannen
python -m src.tools.scan_id

# Schnelle Servo-Mittelpunkt-Kalibrierung
python -m src.tools.servo_quick_calibration

# Servo-Mittelpunkt-Test
python -m src.tools.servo_center_test

# Alle Servos deaktivieren
python -m src.tools.servo_disable

# Kalibrierung im LeRobot-Stil
python -m src.tools.lerobot_calibrate

# Synchronisierte Dual-Port-Fernsteuerung
python -m src.tools.servo_remote_control
```

---

## 📖 Anwendungsschritte

### 1. Servos verbinden und erkennen

1. Verbinden Sie das Steuerboard des Arms über einen USB-zu-Seriell-Adapter und versorgen Sie die Servos mit Strom.
2. Öffnen Sie die GUI und wählen Sie den Port im Dropdown der oberen Leiste aus (oder klicken Sie auf `🔄`, um zu aktualisieren).
3. Oben im Panel erscheint `🟢 Connected`, und es wird automatisch nach online befindlichen Servos im ID-Bereich 1–20 gesucht (üblicherweise 1–6).

> Wenn gemeldet wird, dass der Port belegt ist, stellen Sie sicher, dass kein anderes Programm ihn verwendet (ein serieller Monitor, ein zuvor geöffnetes Tool, das nicht beendet wurde).

### 2. Mittelpunkt-Kalibrierung (aktuelle Position auf 2048 setzen)

> Bringen Sie den Arm vor der Kalibrierung physisch in die Position, in der sich jedes Gelenk an der gewünschten „Null- / Mittelstellung“ befindet.

1. Klicken Sie im Panel auf die Schaltfläche **PortX Center Calibration**.
2. Das Programm deaktiviert zunächst die Servos und fordert Sie auf, sie manuell in den gewünschten Mittelpunkt zu bewegen.
3. Nach Ihrer Bestätigung führt das Programm für jedes Servo Folgendes aus: EEPROM entsperren → Kalibrierbefehl schreiben (Wert 128 an Adresse 40) → EEPROM wieder sperren.
4. Überprüfen Sie die Kalibrierung anschließend mit „Center test“: Das Servo sollte an Ort und Stelle bleiben (sehr geringe Bewegung), was eine erfolgreiche Kalibrierung bedeutet.

### 3. Mittelpunkt-Test

1. Klicken Sie auf **PortX Center Test**.
2. Das Programm aktiviert das Drehmoment und bewegt alle Servos auf 2048.
3. Wenn sich die Servos kaum von ihrer aktuellen Position bewegen, ist die Kalibrierung korrekt; wenn sie sich stark bewegen, ist der Kalibrierungswert unzuverlässig und muss erneuert werden.

### 4. Motoren deaktivieren (manuelle Anpassung)

- Klicken Sie auf **PortX Disable Motors**, um das Drehmoment aller Servos an diesem Port auszuschalten, sodass sie von Hand frei gedreht werden können.
- Für ein einzelnes Servo schalten Sie sein Drehmoment separat auf der Seite **Single-Servo Control** über den Drehmomentschalter unter dem Schieberegler um.

### 5. Servo-ID ändern

1. Wechseln Sie zur Seite **🔬 FT Debugger**, verbinden Sie die serielle Schnittstelle und scannen Sie nach Servos.
2. Wählen Sie das Zielservo aus, ändern Sie den Wert „Servo ID“ (Adresse 0x05) in der Parametertabelle und klicken Sie auf Schreiben.
3. Das Programm führt aus: entsperren → an Adresse 5 schreiben → neue ID überprüfen → wieder sperren.

> ⚠️ Stellen Sie vor dem Ändern einer ID sicher, dass dies das einzige Servo am Bus ist, um ID-Konflikte zu vermeiden.

### 6. Baudrate ändern / Werksreset

- **Baudrate ändern**: Wählen Sie im Bereich „Baud rate / factory reset“ der FT-Debugger-Seite die neue Baudrate (38400 – 1000000 bps) und wenden Sie sie an. Nach dem Schreiben wird die serielle Baudrate automatisch umgestellt und per Ping überprüft; bei Fehlschlag wird automatisch zurückgerollt.
- **Werksreset**: Das Servo wird auf die Werkseinstellungen zurückgesetzt (ID=1, Baudrate=1000000); scannen Sie danach erneut.

### 7. xdat-Parameter sichern und wiederherstellen

Im Bereich „xdat parameters (EEPROM only)“ der FT-Debugger-Seite:

1. **💾 Save current servo**: Speichert die EEPROM-Parameter des aktuell ausgewählten Servos in eine xdat-Datei (Sicherung).
2. Wenn Sie nach freiem Ändern der Servo-Parameter wiederherstellen möchten:
3. **📂 Open xdat**: Lädt die Sicherungsdatei.
4. **📤 Restore parameters to servo**: Schreibt die Sicherung zurück in das EEPROM des aktuellen Servos.

### 8. Synchronisierte Dual-Port-Fernsteuerung

> ⚠️ **Richtung: Port 1 steuert Port 2**. Port 1 (Leader) liest nur die Servo-Winkel; Port 2 (Follower) wird synchron gesteuert.

1. Klicken Sie in der oberen Leiste auf **🎮 Remote** (Port 1 liest Winkel → Port 2 steuert die Servos mit denselben IDs synchron).
2. Beide Ports müssen übereinstimmende Servo-IDs haben; nur Servos in der Schnittmenge werden synchronisiert.
3. Klicken Sie erneut auf dieselbe Schaltfläche, um zu stoppen; danach werden die Scan-Threads des linken und rechten Panels automatisch fortgesetzt.

### 9. LeRobot-Kalibrierung (Kommandozeile)

```Bash
# Follower-Arm kalibrieren (gespeichert unter ~/.cache/huggingface/lerobot/calibration/robots/so_follower/)
python -m src.tools.lerobot_calibrate --arm-type follower

# Leader-Arm kalibrieren
python -m src.tools.lerobot_calibrate --arm-type leader
```

Ablauf: Servos deaktivieren → jedes Gelenk zum Mittelpunkt bewegen und `homing_offset` aufzeichnen → den gesamten Verfahrweg langsam durchfahren und `range_min/max` aufzeichnen (`wrist_roll` ist ein Gelenk mit kontinuierlicher Drehung und festem Bereich von `[0,4095]`) → die JSON-Datei speichern.

Mit einer Kalibrierungsdatei zum Mittelpunkt fahren:

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ Hinweise



1. **Sicherheit zuerst**: Die Mittelpunkt-Kalibrierung wird dauerhaft im EEPROM gespeichert. Stellen Sie vor der Kalibrierung sicher, dass die Stromversorgung stabil ist und der Arm nicht mit Personen oder Gegenständen kollidiert.
2. **Stromversorgung**: Für den Standard-SoARM 101 werden DC 5 V 5 A empfohlen; für die Pro-Version DC 12 V 5 A. Unzureichende Leistung führt zu Schrittverlusten des Servos oder Kommunikationsfehlern.
3. **Exklusivität des seriellen Ports**: Unter Windows wird der Port exklusiv gesperrt, sodass derselbe Port nicht gleichzeitig vom Scan-Thread der GUI und vom Kalibrierungs-Subprozess verwendet werden kann. Das Tool stoppt vor dem Betrieb automatisch den Scan-Thread und beendet den alten Prozess; klicken Sie nicht wiederholt von Hand.
4. **Serielle Berechtigungen unter Linux**: Für den Zugriff auf `/dev/ttyUSB*` / `/dev/ttyACM*` muss der Benutzer zur Gruppe `dialout` hinzugefügt werden (siehe \[Linux tutorial\](docs/zh/Linux教程.md)).
5. **Serielle Benennung unter macOS**: Verwenden Sie `/dev/cu.*` (nicht blockierend) statt `/dev/tty.*` (blockierend, kann hängen bleiben); siehe \[macOS tutorial\](docs/zh/macOS教程.md).
6. **Hot-Plugging**: Nach dem Abziehen des USB versucht das Programm, sich automatisch neu zu verbinden; klicken Sie nach dem erneuten Anstecken auf `🔄`, um die Portliste zu aktualisieren.
7. **Überhitzungs- / Überspannungsschutz**: Das Programm überwacht Spannung und Temperatur (Alarm über 60 °C). Wenn die Servos heiß bleiben, stoppen Sie und lassen Sie sie abkühlen.
8. **Die Mittelpunkt-Kalibrierung ist irreversibel**: Nach dem Schreiben wird der ursprüngliche Offset überschrieben und kann nicht rückgängig gemacht werden. Notieren Sie vor der Kalibrierung zunächst die ursprüngliche Position.
9. **Risiko beim Ändern der ID**: Wenn das Schreiben oder die Überprüfung fehlschlägt, meldet das Programm einen Fehler und setzt den Scan fort; in extremen Fällen kann das Servo jedoch „verloren gehen“. Versuchen Sie in diesem Fall „Factory reset“ (nach dem Zurücksetzen ist die ID wieder 1).
10. **Kodierungsproblem**: Wenn Emojis in der Windows-Konsole verstümmelt erscheinen, setzen Sie `PYTHONIOENCODING=utf-8`, bevor Sie die Kommandozeilen-Tools ausführen. Linux/macOS mit nativem UTF-8 haben dieses Problem in der Regel nicht.

---

## 🛠️ Fehlerbehebung

| Symptom | Mögliche Ursache | Lösung |
|-|-|-|
| Serielle Schnittstelle lässt sich nicht öffnen / Port belegt | Ein anderes Programm verwendet sie | Schließen Sie Programme wie serielle Monitore, oder wechseln Sie den Port und starten Sie das Tool neu |
| Beim Scan werden keine Servos gefunden | Unzureichende Leistung / falsche Verkabelung / Baudrate stimmt nicht überein | Prüfen Sie Stromversorgung und Verkabelung und bestätigen Sie, dass die Servos mit 1M Baudrate laufen |
| Servos laufen nach der Mittelpunkt-Kalibrierung unkontrolliert | Die Position wurde vor der Kalibrierung nicht korrekt eingestellt | Wiederholen Sie „deaktivieren → manuell positionieren → Mittelpunkt-Kalibrierung“ |
| Die Temperatur steigt zu schnell | Übermäßige Last oder Blockierung | Prüfen Sie den Mechanismus auf Verklemmen; reduzieren Sie Geschwindigkeit/Beschleunigung |
| Servo nach dem Ändern seiner ID nicht gefunden | ID-Konflikt oder Schreibfehler | Werksreset durchführen und erneut scannen |
| Fernsteuerung nicht synchron | Die beiden Ports haben nicht übereinstimmende IDs | Bestätigen Sie, dass an beiden Ports (Leader und Follower) Servos mit derselben ID online sind |

---

## 📁 Verzeichnisstruktur

```Plain Text
Juxi_ServoController/
├── docs/                    # Tutorials je System (Chinesisch/Englisch)
│   ├── zh/                  # Chinesische Tutorials
│   │   ├── Windows教程.md
│   │   ├── Linux教程.md
│   │   └── macOS教程.md
│   └── en/                  # Englische Tutorials
│       ├── Windows.md
│       ├── Linux.md
│       └── macOS.md
├── src/
│   ├── gui/                  # PySide6-GUI
│   │   ├── factory_calibration_tool.py   # Haupttool (Dual-Port-Kalibrierung + Fernsteuerung + Sprachumschaltung)
│   │   ├── ft_debugger.py                # FT-Debugger (Parameter lesen/schreiben / xdat-Sicherung)
│   │   ├── calibration_wizard.py         # LeRobot-Kalibrierungsassistent
│   │   ├── theme_utils.py                # Helles Theme
│   │   └── language_dialog.py            # Dialog zur Sprachauswahl
│   ├── tools/                # Kommandozeilen-Tools
│   ├── xdat_utils.py         # xdat-Parameterdatei lesen/schreiben
│   ├── i18n*.py / i18n_translations/     # Chinesisch/Englisch-Internationalisierung
│   ├── port_utils.py         # Erkennung der seriellen Schnittstelle
│   └── calibration_manager.py# Verwaltung der LeRobot-Kalibrierungsdateien
├── scservo_sdk/              # FTServo-Servo-Kommunikations-SDK
├── requirements.txt
└── setup.py                  # Skript zur Umgebungsprüfung
```
