[English](../../en/so-arm101-assembly/parallel-jaw-gripper.md) | [简体中文](../../zh-hans/so-arm101-assembly/parallel-jaw-gripper.md) | [繁體中文](../../zh-hant/so-arm101-assembly/parallel-jaw-gripper.md) | Deutsch | [Español](../../es/so-arm101-assembly/parallel-jaw-gripper.md) | [Français](../../fr/so-arm101-assembly/parallel-jaw-gripper.md) | [Italiano](../../it/so-arm101-assembly/parallel-jaw-gripper.md) | [日本語](../../ja/so-arm101-assembly/parallel-jaw-gripper.md) | [한국어](../../ko/so-arm101-assembly/parallel-jaw-gripper.md) | [Português (BR)](../../pt-br/so-arm101-assembly/parallel-jaw-gripper.md) | [Português (PT)](../../pt-pt/so-arm101-assembly/parallel-jaw-gripper.md)

# Montageanleitung für den Parallelgreifer

Sehen Sie sich die Modelldateien auf [Onshape](https://cad.onshape.com/documents/96518c699fd03eea508b06d3/w/d5f95a6266b027d84ae48634/e/317bed52afdde5ea3dcfc236) an

<figure view-type="Card">[Attachment: PincOpen装配体.step](../../en/images/PincOpen装配体.step)</figure>



<figure view-type="Card">[Attachment: 平行指夹爪安装步骤.mp4](../../en/images/平行指夹爪安装步骤.mp4)</figure>

![Dies ist eine Illustration der Montageschritte für den Parallelgreifer mit 12 schrittweisen Demonstrationsmodulen, die den 11 Schritten der Montageanleitung entsprechen. Jedes Modul hat eine Nummer, und unter jedem Schritt ist der zugehörige Vorgang beschrieben: Modul 1 zeigt das Lösen der vier kleinen Schrauben und deren Beiseitelegen, Modul 2 zeigt das Abnehmen der hinteren Abdeckung; Modul 3 erläutert die Montage von Servo 6 an der Kupplung mit fünf Schrauben, Modul 4 fordert dazu auf, im Feetech-Host-Tool die Mittelpunkt-Kalibrierung anzuklicken und dabei den Greifer geschlossen zu halten; die übrigen Module entsprechen der Reihe nach der Montage der Servo-Halterung, dem Anbringen der Kamera, dem Verbinden des Adapterteils und weiteren Vorgängen und veranschaulichen durch die schrittweisen Abbildungen die Objekte und Bauteilbeziehungen jedes Schritts.](../../en/images/d12-01.png)

## 1. Die vier kleinen Schrauben lösen und die hintere Abdeckung abnehmen

## 2. Servo 6 mit fünf Schrauben an der Kupplung montieren

## 3. Im Feetech-Host-Tool auf Center calibration klicken (den Greifer geschlossen halten!)

**Das Feetech-Servo-Debugging-Tool herunterladen**

- Windows-PC

https://gitee.com/ftservo/fddebug

Laden Sie [`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z) herunter, entpacken Sie es und führen Sie das darin enthaltene EXE-Programm aus

- Ubuntu-PC

https://github.com/Kotakku/FT_SCServo_Debug_Qt

1. Öffnen Sie das Feetech-Host-Debugging-Tool, wählen Sie den COM-Port, stellen Sie die Baudrate auf eine Million ein und klicken Sie auf „Open“
2. Klicken Sie auf „Search“; sobald „STS3215“ erscheint, klicken Sie auf „Stop“ und dann auf „STS3215“
3. Wählen Sie oben „Program“
4. Klicken Sie auf „Center calibration“

## 4. Den Zylinder ausrichten und die hintere Abdeckung anbringen

## 5. Die vier kleinen Schrauben wieder eindrehen

## 6. Die Servo-Halterung mit vier kleinen Schrauben montieren

## 7. Die Servo-Halterung, die die Kamera-Halterung aufnehmen kann, mit 6 kleinen Schrauben montieren

## 8. Die Kamera mit 4 Unterlegscheibenschrauben an der Halterung befestigen

## 9. Die Kamera-Halterung mit 2 kleinen Schrauben mit der Servo-Halterung verbinden

## 10. Das Adapterteil am Servohorn von Servo 5 montieren

## 11. Das Adapterteil mit dem Parallelgreifer verbinden
