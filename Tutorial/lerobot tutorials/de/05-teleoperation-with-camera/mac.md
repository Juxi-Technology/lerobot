[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | Deutsch | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Mac-Rechner

## Die Kamera an den Computer anschließen

```Shell
lerobot-find-cameras opencv
```

![Das Bild zeigt das Erkennungsergebnis nach dem Anschließen einer Kamera an einen Mac. Es listet die zwei automatisch erzeugten Kameras auf, die externe Kamera und die integrierte Frontkamera des Mac. Die Fps der externen Kamera betragen 60.00024 und die der integrierten Kamera 30.0. Dieses Bild gehört zum Inhalt über das Anschließen einer Kamera an einen Mac, veranschaulicht das Erkennungsergebnis nach dem Anschließen und hilft Anwendern, Typ, ID, Backend-API und Bildrate jeder Kamera zu verstehen.](../../en/images/d31-01.png)

## Eine Kamera: Teleoperation mit angezeigtem Kamerabild

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

Nach der Ausführung startet die Teleoperation

Das rerun.io-Fenster öffnet sich und zeigt die Trajektorie jedes Servogelenks in Echtzeit zusammen mit dem Live-Kamerabild

und speichert die Bilder im Verzeichnis `~/username/outputs/captured_images`

![Das Bild zeigt das rerun.io-Fenster, das sich öffnet, wenn die Teleoperation nach der Ausführung startet. Links befinden sich Diagramme der Trajektorien mehrerer Servogelenke, dargestellt als Kurven, die die Bewegung verschiedener Gelenke zeigen. Rechts wird das Kamerabild der Innenraumszene in Echtzeit angezeigt, in der ein Tisch, Stühle und einige Objekte zu sehen sind. Unten gibt es außerdem einige balkenförmige Informationen. Dieses Bild steht in engem Zusammenhang mit dem Kontext und veranschaulicht die Servogelenk-Trajektorien und das Live-Kamerabild während der Teleoperation; außerdem verdeutlicht es, dass die Bilder im angegebenen Verzeichnis gespeichert werden.](../../en/images/d31-02.png)

## Mehrere Kameras: Teleoperation mit angezeigten Kamerabildern

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 1920, height: 1080, fps: 30, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

![Das Bild zeigt das rerun.io-Fenster, das für die Teleoperation mit mehreren Kamerabildern verwendet wird. Links ist das Live-Kamerabild, das Objekte auf einem Schreibtisch zeigt; rechts befinden sich Datendiagramme, die die Trajektorien verschiedener Gelenke darstellen, etwa observation_wip. Unten gibt es einen Bereich Streams, der die Daten mehrerer Gelenke auflistet. Oben rechts stehen Dateninformationen wie Application ID und Source IP. Dieses Bild entspricht dem Inhalt „Mehrere Kameras: Teleoperation mit angezeigten Kamerabildern" und veranschaulicht die Bilder und Daten während der Teleoperation.](../../en/images/d31-03.png)
