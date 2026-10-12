[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | Deutsch | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>Montageanleitung für das SO-ARM101-Roboterarm-Kit</title>

<callout emoji="💡">
Hinweis: Überspringen Sie dieses Tutorial, wenn Sie einen vormontierten Arm haben
</callout>

## 3D-Druckteile für den Follower-Arm

![Dieses Bild zeigt die 3D-Druckteile für den Follower-Arm, die zur Montage des Roboterarms SO-ARM101 benötigt werden, allesamt weiße Kunststoffteile aus PLA, die auf einer hellen Holzmaserungsoberfläche angeordnet sind. Zu den Teilen gehören Verbindungsstücke verschiedener Formen, eine gegabelte Struktur mit Gitter, ein basisartiges Teil mit Löchern, ein speziell geformter gegabelter Tragarm und so weiter, was zur Aussage des Tutorials passt, dass das Ende des Follower-Arms ein Greifer ist. Diese Teile sind die grundlegenden Formteile für den Follower-Arm des Arms und die Objekte, die im Schritt zum Entfernen der Stützen behandelt werden, und entsprechen direkt den im Tutorial vorgestellten 3D-Druckteilen des Follower-Arms.](../en/images/d09-01.jpg)

## 3D-Druckteile für den Leader-Arm

![Das Bild zeigt 3D-Druckteile für den Roboterarm SO-ARM101. Im Bildausschnitt sind verschiedene schwarze 3D-Druckteile ordentlich angeordnet, wobei einige Teile blaue Linien an den Kanten aufweisen. Zu diesen Teilen gehören Strukturteile für den Leader- und den Follower-Arm, wie der Greifer, der Griff und der Auslöser, sowie Verbindungsstücke. Das Bild entspricht dem Abschnitt „3D-Druckteile für den Leader-Arm“ des Dokuments und veranschaulicht das Aussehen der 3D-Druckteile und bietet eine Referenz für die späteren Schritte zum Entfernen der Reststützen und zum Unterscheiden der Servos.](../en/images/d09-02.jpg)

Der Leader- und der Follower-Arm sind sich sehr ähnlich; nur das Ende unterscheidet sich

Der Leader hat einen Griff und einen Auslöser; der Follower hat einen Greifer

## Reststützen von den 3D-Druckteilen entfernen

Prüfen Sie jedes Loch, jede Öffnung, jeden Schlitz und jedes Gitter, insbesondere die fünf Löcher, die der Mahjong-Kachel „fünf Punkte“ ähneln

Dieser Schritt ist sehr wichtig; sonst lassen sich die Schrauben später nicht eindrehen

## Die vier Servos unterscheiden

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">Große Ausführung</td><td vertical-align="middle">Kleine Ausführung</td><td vertical-align="middle">Spannung (V)</td><td vertical-align="middle">Übersetzungsverhältnis</td><td vertical-align="middle">Armgelenk</td><td vertical-align="middle">Anzahl</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Alle Follower-Gelenke</td><td vertical-align="middle">6</td></tr></tbody></table>

> Das Übersetzungsverhältnis ist das Verhältnis von „Motordrehzahl : Drehzahl der Servo-Abtriebswelle“; 1:345 bedeutet zum Beispiel, dass sich der Motor 345-mal dreht, damit sich die Abtriebswelle einmal dreht.
> 
> Ein hohes Übersetzungsverhältnis vervielfacht das Drehmoment über das Getriebe, sodass eine schwerere Last bewegt werden kann (wie der Follower-Arm)
> 
> Gleichzeitig dreht sich die Abtriebswelle aber langsamer (weil sie „herunterübersetzt“ wird)
> 
> Auch das Ziehen am Gelenk erfordert mehr Kraft

Nachfolgend sind die Modelle und Übersetzungsverhältnisse aller Servos in diesem Projekt aufgeführt; die unterstrichenen Teile sind ihre Nummern

![Das Bild zeigt die im Arm verwendeten Servo-Modelle, Spannungen und Übersetzungsverhältnisse. Links ist der Leader-Arm mit zwei Modellen, C046 (7,4 V, 1:147) und C044 (7,4 V, 1:191); rechts ist der Follower-Arm mit zwei Modellen, C001 (7,4 V, 1:345) und C047 (12 V, 1:345). Das Bild ist eng mit dem Kontext verknüpft, der die Servo-Modelle, Spannungen und Übersetzungsverhältnisse des Leader- und Follower-Arms ausführlich vorstellt; dieses Bild veranschaulicht diese zentralen Werte, damit Leser die Servo-Konfiguration besser verstehen.](../en/images/d09-03.png)

![Das Bild zeigt vier Schachteln mit Servos der Bezeichnung „STS3215“. Auf jeder Schachtel ist das Wort „SPECIFICATION“ aufgedruckt, und es sind Parameter wie Drehmoment, Geschwindigkeit und Abmessungen angegeben, zum Beispiel ein Drehmoment von 9,2 kg·cm/127,98 oz·in (6 V). Der STS3215-C001 hat ein Drehmoment von 12,5 kg·cm/173,88 oz·in (6 V), und der STS3215-C046 hat ein Drehmoment von 16 kg·cm/220,58 oz·in (7 V). Diese Servos sind das Modell, das für alle Gelenke des Follower-Arms des Arms verwendet wird, entsprechend dem im Dokument vorgestellten Follower-Arm, und sie werden für die Servo-Montage in den späteren Montageschritten verwendet.](../en/images/d09-04.jpg)

## Die beiden Netzteile unterscheiden

5 V 6 A 30 W Netzteil: versorgt die 7,4-V-Servos (Leader-Arm), schwarz

12 V 5 A 60 W Netzteil: versorgt die 12-V-Servos (Follower-Arm), weiß

## Das Feetech-Servo-Debugging-Tool herunterladen

### Windows-PC

https://gitee.com/ftservo/fddebug

Laden Sie [`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z) herunter, entpacken Sie es und führen Sie das darin enthaltene EXE-Programm aus

### Ubuntu und Mac (das Archiv enthält ein Tutorial)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![Dieses Bild ist eine ergänzende Illustration zur Montageanleitung des SO-ARM101-Roboterarm-Kits und entspricht dem Abschnitt zum Unterscheiden der Netzteile. Es zeigt zwei Servo-Modelle und ihre Einbaupositionen, STS3215-C001 und STS3215-C018, und kennzeichnet außerdem Servos wie STS3215-C004, entsprechend den verschiedenen Gelenken des Arms. Die Abbildung listet außerdem die Parameter dieser beiden Servos auf, darunter Drehzahl, Haltemoment, Servo-Präzision, Schutzfunktionen und Parameterrückmeldung, und bietet damit eine Referenz für die Servo-Auswahl und -Montage beim Zusammenbau des Arms.](../en/images/d09-05.jpg)

**Pro-Version: Der Leader-Arm verwendet ein 5V6A-Netzteil, der Follower-Arm ein 12V5A-Netzteil**

Servo-ID-Einrichtung, Servo-Winkelkalibrierung und Montage müssen im Voraus erfolgen; siehe das [offizielle Montage-Tutorial](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# Schritt 1: Servo-IDs einstellen und Servohörner montieren (außer Servo 5)

<grid>
<column width-ratio="0.500000">
![Das Bild zeigt die Oberfläche des Feetech-Host-Debugging-Tools. Die Oberfläche hat drei Tabs, „Debug“, „Program“ und „Upgrade“, wobei „Program“ aktuell ausgewählt ist. Wichtige Informationen: 1. In den Kommunikationseinstellungen ist die Portnummer COM6 und die Baudrate 1000000; 2. Unter den Servo-Operationen sind synchrones Schreiben, asynchrones Schreiben und Drehmomentausgabe alle angehakt; 3. Bei der Servo-Rückmeldung zeigen Parameter wie Spannung, Strom, Temperatur und Position alle 0; 4. Bei der Servo-Suche ist id 1 ausgewählt, Modell ST53215. Dieses Bild gehört zu den oben beschriebenen Debugging-Vorgängen, etwa dem Einstellen der Servo-IDs und der Montage des Servohorns, und zeigt die Oberfläche des Debugging-Tools.](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![Das Bild zeigt die Oberfläche des Feetech-Host-Debugging-Tools, das zum Einstellen der Servo-IDs dient. Die Oberfläche hat drei Tabs, „Debug“, „Program“ und „Upgrade“, wobei „Program“ aktuell ausgewählt ist. Im Bereich „Center calibration“ ist die ID-Nummer 4, mit einer Schaltfläche „Save“ rechts. Die linke Seite der Oberfläche zeigt die Servo-ID, das Modell und weitere Informationen. Dieses Bild gehört zum Inhalt „Schritt 1: Servo-IDs einstellen und Servohörner montieren (außer Servo 5)“ des Dokuments und zeigt die Oberfläche der Servo-ID-Einrichtung und veranschaulicht, wo die ID-Nummer festgelegt wird.](../en/images/d09-07.png)
</column>
</grid>

1. Öffnen Sie das Feetech-Host-Debugging-Tool, wählen Sie den COM-Port, stellen Sie die Baudrate auf eine Million ein und klicken Sie auf „Open“
2. Klicken Sie auf „Search“; sobald „STS3215“ erscheint, klicken Sie auf „Stop“ und dann auf „STS3215“
3. Wählen Sie oben „Debug“; Sie können den Schieberegler ziehen, um das Servo zu drehen, oder auf „Scan“ klicken, damit es sich hin und her bewegt. Bestätigen Sie, dass das Servo normal läuft
4. Wählen Sie oben „Program“
5. Klicken Sie auf „Center calibration“, um die aktuelle Position der Drehwelle des Servos als Mittelpunkt festzulegen (0-4095)
6. Klicken Sie auf „ID“, stellen Sie die ID-Nummer des entsprechenden Servos in der unteren rechten Ecke ein und klicken Sie auf „Save“. Beachten Sie, dass die Nummer aus einfachen arabischen Ziffern ohne Buchstaben besteht.
7. Ziehen Sie das Kabel ab, das das Servo mit dem Steuerboard verbindet
8. Stecken Sie das Servokabel in das Servo

Servo 1 bekommt zwei Kabel; die übrigen Servos erhalten vorerst nur ein Kabel

![Das Bild zeigt die Servo-Montage beim Zusammenbau des SO-ARM101-Arm-Kits. Im Bildausschnitt sind der Follower-Arm und der Leader-Arm zu sehen, wobei der Follower-Arm mit 123456 und der Leader-Arm mit 123456 nummeriert ist. Die Servos tragen Beschriftungen mit Übersetzungsverhältnissen von 1:345, 1:191 und 1:147. Darunter befindet sich das Steuerboard, das mit zwei Kabeln verbunden ist, einem weißen und einem schwarzen. Dieses Bild gehört zu den obigen Montageschritten und veranschaulicht die Einbaupositionen und Nummern der Servos, damit der Monteur die Servos korrekt dem Steuerboard zuordnen kann.](../en/images/d09-08.png)

<callout emoji="💡">
Nochmals: Stellen Sie sicher, dass die Gelenk-ID und das Übersetzungsverhältnis jedes Servos genau zu **SO-ARM101** passen.
</callout>

Jeder Motor am Bus hat eine eindeutige ID. Neue Motoren haben üblicherweise die Standard-ID `1`. Damit die Kommunikation zwischen den Motoren und dem Controller funktioniert, müssen wir zunächst für jeden Motor eine eindeutige ID festlegen. Außerdem wird die Datenübertragungsgeschwindigkeit am Bus durch die Baudrate bestimmt. Um miteinander zu kommunizieren, müssen der Controller und alle Motoren mit derselben Baudrate konfiguriert sein; die Servos dieses Arms verwenden eine Baudrate von 100000.

Dazu müssen wir den Controller zunächst nacheinander mit jedem Motor verbinden, um sie konfigurieren zu können. Da wir diese Parameter in den nichtflüchtigen Bereich des internen Motorspeichers (EEPROM) schreiben, ist dies nur einmal nötig.

Wenn Sie Motoren von einem anderen Roboter wiederverwenden, müssen Sie diesen Schritt möglicherweise ebenfalls durchführen, da die IDs und Baudraten nicht übereinstimmen.

Das folgende Video zeigt die Abfolge der Schritte zum Einstellen der Motor-IDs.

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Verwenden Sie das Feetech-Servo-Host-Tool, um Servo-IDs einzustellen und den Mittelpunkt zu kalibrieren. Die IDs werden von 1 bis 6 vergeben!

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu und Mac

<callout emoji="💡">
Wenn Sie das Feetech-Servo-Host-Tool benötigen, siehe oben das [Feetech-Servo-Debugging-Tool](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb)
</callout>

Schließen Sie zunächst die Umgebungseinrichtung gemäß der Seite [offizielle LeRobot-Installation](https://huggingface.co/docs/lerobot/installation) ab

<callout emoji="💡">
Denken Sie daran, die virtuelle Umgebung zu aktivieren und in das entsprechende src/lerobot-Verzeichnis zu wechseln
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. Ermitteln Sie den USB-Port für den Arm. Um den richtigen Port für jeden Arm zu finden, führen Sie das Hilfsskript zweimal aus::

```Plain Text
lerobot-find-port
```

Beispielausgabe bei der Ermittlung des Leader-Arm-Ports (zum Beispiel `/dev/tty.usbmodem575E0031751` auf einem Mac oder möglicherweise `/dev/ttyACM0` unter Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

Beispielausgabe bei der Ermittlung des Follower-Arm-Ports (zum Beispiel `/dev/tty.usbmodem575E0032081` oder möglicherweise `/dev/ttyACM1` unter Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
Denken Sie daran, den USB-Stecker abzuziehen, sonst kann der Port nicht erkannt werden.
</callout>

2. Verbinden Sie den PC mit einem USB-Kabel mit dem Servo-Treiberboard des Follower-Arms und schalten Sie es ein. Führen Sie dann den folgenden Befehl aus. Ändern Sie `--robot.port=/dev/ttyACM0` im Befehl auf den von Ihnen gefundenen Port. Wenn der gefundene Port beispielsweise `/dev/ttyACM1` ist, ändern Sie ihn zu `--robot.port=/dev/ttyACM1`

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

Sie sehen die folgende Ausgabe.

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

Schließen Sie gemäß den Anweisungen den Greifer-Servo an. Stellen Sie sicher, dass es der einzige Servo ist, der mit dem Servo-Treiberboard verbunden ist, und dass dieser Servo noch nicht mit einem anderen Servo verbunden ist. Nachdem Sie **[Enter]** gedrückt haben, legt das Skript automatisch die ID und die Baudrate dieses Servos fest. Die IDs werden von 6 bis 1 vergeben!

Danach sollten Sie Folgendes sehen:

```Python
'gripper' motor id set to 6
```

Die nächste Ausgabe lautet dann:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**Hinweis** Wiederholen Sie den Vorgang gemäß den Anweisungen für jeden Servo.
Wie bei den vorherigen Servos stellen Sie sicher, dass es der einzige Servo ist, der mit dem Treiberboard verbunden ist, und dass das Servo selbst nicht mit einem anderen Servo verbunden ist.
</callout>

Prüfen Sie vor jedem Drücken von **Enter** Ihre Kabelverbindungen. Das Stromkabel kann sich beispielsweise beim Hantieren mit der Platine lösen.

Wenn Sie alle Schritte abgeschlossen haben, endet das Skript automatisch und die Servos sind einsatzbereit. Sie können nun nacheinander den 3-poligen Stecker jedes Servos anschließen und das Kabel des ersten Servos (des „shoulder pan“-Servos mit ID 1) mit dem Treiberboard verbinden. Das Treiberboard kann nun auf der Basis des Arms montiert werden.

Wiederholen Sie dieselben Schritte für den Leader-Arm.

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# Schritt 2: Montage

<callout emoji="💡">
- Die Montageschritte für den Follower-Arm sind im Wesentlichen dieselben wie für den Leader-Arm. Der einzige Unterschied besteht darin, dass nach Schritt 12 der Endeffektor (Greifer und Griff) anders montiert wird.
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
Montage des Servo-Treiberboards: Bringen Sie zuerst die 4 Messing-Abstandshalter an und befestigen Sie dann das Treiberboard mit vier M2.5\*8-Schrauben
</callout>

<grid>
<column width-ratio="0.525947">
![Die vier Messing-Abstandshalter anbringen](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![Das Servo-Treiberboard mit M2.5*8-Schrauben befestigen](../en/images/d09-10.webp)
</column>
</grid>

![Am Arm montieren und verkabeln](../en/images/d09-11.png)

**Pro-Version: Der schwarze Leader-Arm verwendet ein 5V6A-Netzteil, der weiße Follower-Arm ein 12V5A-Netzteil**







# Servo-IDs und Mittelpunkt-Kalibrierung in der Web-Oberfläche einstellen

https://bambot.org/feetech.js?lang=zh

1. Geben Sie je nach Servo-Modell 0 oder 1 ein und klicken Sie dann auf „Connect“

![Das Bild zeigt die Oberfläche „Connect“ in der Montageanleitung des Arm-Kits. Links in der Oberfläche steht das Wort „Connect“, rechts befinden sich ein Dropdown „Baud rate“, das auf 1,000,000 bps (Index 0) eingestellt ist, und ein Eingabefeld für „Protocol end (0=STS/SMS, 1=SCS)“, das auf 0 gesetzt ist, wobei um die Zahl „1“ neben dem Eingabefeld ein roter Rahmen liegt. Darunter befindet sich eine grüne Schaltfläche „Connect“, wobei um die Zahl „2“ daneben ein roter Rahmen liegt. Unten steht „Status: Disconnected“. Dieses Bild entspricht dem obigen Inhalt „Geben Sie je nach Servo-Modell 0 oder 1 ein und klicken Sie dann auf ‚Connect‘“ und veranschaulicht die Einstellungen des Verbindungsvorgangs.](../en/images/d09-12.png)

2. Servos mit den IDs 1\~6 scannen; mit FOUND in den Scan-Ergebnissen bestätigen, welcher Servo zur jeweiligen ID gehört. Im Bild wurde zum Beispiel Servo-ID 1 gefunden

![Das Bild zeigt die Oberfläche des Schritts „Scan servos“ in der Montageanleitung des SO-ARM101-Arm-Kits. Oben in der Oberfläche befinden sich die Eingabefelder „Start ID“ und „End ID“, aktuell mit Start-ID 1 und End-ID 6. Darunter befindet sich eine Schaltfläche „Start scan“. In den Scan-Ergebnissen findet das Scannen der IDs 1-6 keine Servos und meldet „Exception: No status packet! Error code: 0“. Dieses Bild ist eng mit dem Kontext verknüpft und veranschaulicht die Oberfläche und die Ergebnisse beim Scannen nach Servos, damit Nutzer den Servo-Scan-Status verstehen.](../en/images/d09-13.png)

3. ID-Einstellung und Mittelpunkt-Kalibrierung

① Stellen Sie die Eingabe der aktuellen Servo-ID auf die ID des gescannten Servos ein

② Geben Sie unter „ID management“ eine Zahl ein und klicken Sie auf „Change ID“, um die ID festzulegen

③ Mittelpunkt-Kalibrierung (der Mittelpunkt des STS3215-Servos ist 2047, der des SCS0009-Servos ist 511)

STS-Servo: geben Sie 2047 unter „Position control“ ein und klicken Sie auf „Set“

SCS-Servo: geben Sie 511 unter „Position control“ ein und klicken Sie auf „Set“

![Das Bild zeigt eine Oberfläche zur Steuerung eines einzelnen Servos. Die aktuelle Servo-ID ist 1; nachdem unter ID management die Zahl 1 eingegeben und auf „Change ID“ geklickt wurde, erscheint die Meldung „Success: ID changed to 1“. Unter Position Control steht der Wert 2047, und ein Klick auf die Schaltfläche „Set“ übernimmt ihn. Dieses Bild gehört zum Kontext „ID-Einstellung und Mittelpunkt-Kalibrierung“ und veranschaulicht die Oberfläche für den ID-Einrichtungsvorgang, damit Nutzer verstehen, wie sie unter „ID management“ eine Zahl eingeben, um die ID festzulegen, und wie sie unter „Position control“ den Mittelpunktwert eingeben und auf „Set“ klicken, um den Vorgang abzuschließen.](../en/images/d09-14.png)
