[English](../en/urdf-and-resources.md) | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | Deutsch | [Español](../es/urdf-and-resources.md) | [Français](../fr/urdf-and-resources.md) | [Italiano](../it/urdf-and-resources.md) | [日本語](../ja/urdf-and-resources.md) | [한국어](../ko/urdf-and-resources.md) | [Português (BR)](../pt-br/urdf-and-resources.md) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>URDF-Dateien und Referenzressourcen</title>

# Lerbots offizielle [URDF-Datei](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf)



## URDF Studio

https://urdf.d-robotics.cc/



## ROS2-Simulationssteuerung (selbst umsetzen)

https://github.com/holmsslk/so-arm-moveit-hardware



## Die offizielle grafische Oberfläche von LeRobot

https://github.com/huggingface/leLab

LeLab ist eine Web-App, die den gesamten LeRobot-Workflow – Kalibrierung, Teleoperation, Aufnahme, Training, Wiedergabe – in einer einzigen Browser-Oberfläche vereint. Einfach den Roboterarm anschließen, die App öffnen und schon kann es losgehen. Keine umständliche Kommandozeilenarbeit und keine Tastatureingabe nötig.

🤗 Der native Web-Einstiegspunkt von LeRobot, der neue Nutzer in wenigen Minuten von „out of the box“ bis zum „Training ihrer ersten Policy“ bringt.

🤗 Installation und Ausführung von allem mit einem einzigen Befehl.



# Den Follower-Arm vom Handy aus steuern

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## Cloud-Robotik-Entwicklung: ROS-2-Geräte sowie Isaac-Sim-LeRobot-Simulation und Datenstreaming auf AWS

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## Servo-IDs und Mittelpunkt-Kalibrierung in der Web-Oberfläche einstellen

https://bambot.org/feetech.js?lang=zh

1. Geben Sie je nach Servo-Modell 0 oder 1 ein und klicken Sie dann auf „Connect“

![Das Bild zeigt die Verbindungsoberfläche zum Einstellen der Servo-IDs und der Mittelpunkt-Kalibrierung in der Web-Oberfläche. Die Oberfläche enthält einen Abschnitt „Connect“ mit einem Baudrate-Dropdown, das aktuell auf „1,000,000 bps (Index 0)“ steht; ein Dropdown für das Protokollende, aktuell auf „0=STS/SMS“ gesetzt; und eine Schaltfläche „Connect“. Am unteren Rand zeigt die Oberfläche „Status: Disconnected“. Das Bild ist eng mit dem Kontext verknüpft: Nachdem Sie je nach Servo-Modell 0 oder 1 eingegeben und auf „Connect“ geklickt haben, werden Servos mit den IDs 1~6 gescannt, um den passenden ID-Servo zu bestätigen – dies ist eine zentrale Oberfläche in diesem Ablauf.](../en/images/d68-01.png)

2. Servos mit den IDs 1\~6 scannen; mit FOUND in den Scan-Ergebnissen bestätigen, welcher Servo zur jeweiligen ID gehört. Im Bild wurde zum Beispiel Servo-ID 1 gefunden

![Das Bild zeigt die Servo-Scan-Oberfläche in Lerbots offiziellem URDF Studio. Die Oberfläche zeigt eine Start-ID von 1 und eine End-ID von 6, darunter eine Schaltfläche „Start scan“. In den Scan-Ergebnissen findet das Scannen von ID1 die ID1239, während das Scannen von ID2 bis ID6 jeweils meldet „ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0“. Dieses Bild bezieht sich auf die im Kontext beschriebene Servo-Scan-Operation in Lerbots offiziellem URDF Studio und veranschaulicht den Scanvorgang und seine Ergebnisse.](../en/images/fix-01.png)

3. ID-Einstellung und Mittelpunkt-Kalibrierung

① Stellen Sie die Eingabe der aktuellen Servo-ID auf die ID des gescannten Servos ein

② Geben Sie unter „ID management“ eine Zahl ein und klicken Sie auf „Change ID“, um die ID festzulegen

③ Mittelpunkt-Kalibrierung (der Mittelpunkt des STS3215-Servos ist 2047, der des SCS0009-Servos ist 511)

STS-Servo: geben Sie 2047 unter „Position control“ ein und klicken Sie auf „Set“

SCS-Servo: geben Sie 511 unter „Position control“ ein und klicken Sie auf „Set“

![Das Bild zeigt Lerbots Oberfläche zur Steuerung eines einzelnen Servos. Die „Current servo ID“ ist mit 1 angegeben; darunter befinden sich unter „ID management“ die Zahl 1 und eine Schaltfläche „Change ID“, wobei darunter die Meldung „Success: ID changed to 1“ erscheint. Im Bereich Position Control gibt es eine Schaltfläche „Read position“ mit der Position 2047 neben einer Schaltfläche „Set“. Dieses Bild bezieht sich auf den Abschnitt „ID-Einstellung und Mittelpunkt-Kalibrierung“ des Dokuments und veranschaulicht die Oberfläche zum Einstellen der Servo-IDs und zum Kalibrieren des Mittelpunkts, damit Nutzer verstehen, wie sie diese Einstellungen in Lerbot vornehmen.](../en/images/d68-02.png)
