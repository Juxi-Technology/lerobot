[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | Deutsch | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Windows-Rechner

## Die Kamera an den Computer anschließen

```Shell
lerobot-find-cameras opencv
```

![Dieses Bild ist das Kommandozeilenfenster von Windows und zeigt Kamerafehler bei der Verbindung sowie Geräteerkennungsergebnisse. Oben steht ein Fehler: „ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range". Darunter werden die erkannten Kameras aufgelistet, darunter Camera #0 und Camera #1, mit Name, Typ, Backend-API, Standard-Stream-Konfiguration, Format, Quelle, Breite, Höhe und Bildrate; unten stehen Fehler wie „lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0". Dies entspricht dem im Dokument genannten Fehlerszenario „Die Kamera kann keine Verbindung herstellen, aber beim Wechseln der Kamera in Tencent Meeting öffnet sie sich trotzdem normal" und ist die tatsächliche Laufzeitfehler-Rückmeldung vor dem Ändern des OpenCV-Backend-Codes.](../../en/images/d32-01.png)

## Teleoperation mit angezeigtem Kamerabild

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

Das rerun.io-Fenster öffnet sich und zeigt die Trajektorie jedes Servogelenks in Echtzeit zusammen mit dem Live-Kamerabild

und speichert die Bilder im Verzeichnis `C:\Users\username\outputs\captured_images`

![Das Bild zeigt das rerun.io-Fenster, das die Trajektorien der Servogelenke und das Live-Kamerabild in Echtzeit anzeigt. Links befindet sich die Blueprint-Oberfläche mit Optionen wie „teleoperation". In der Mitte ist das Trajektoriendiagramm, das Gelenkpositionsdaten wie „observation_wrist_rot.pos" zeigt. Rechts ist das Kamerabild, das die Szene aus der Perspektive des Roboters zeigt. Oben rechts steht „Waiting for data on rerun: http://127.0.0.1:9876/remote...", darunter Informationen zur Datenquelle. Dieses Bild gehört zum Inhalt, der das rerun.io-Fenster mit dem Echtzeit-Kamerabild beschreibt, und veranschaulicht den Effekt.](../../en/images/d32-02.png)

## Wenn der folgende Fehler auftritt

Die Kamera kann keine Verbindung herstellen, aber beim Wechseln der Kamera in Tencent Meeting öffnet sie sich trotzdem normal

![Das Bild zeigt die Windows-Kommandozeilenoberfläche mit Kameraerkennungsergebnissen. Oben werden „Detected Cameras" und kamerabezogene Informationen wie Name, Typ, ID und Backend-API angezeigt. Darunter steht ein Fehler, dass beim Ausführen von lerobot_find_cameras_openpyc die OpenCV-Kamera nicht verbunden oder konfiguriert werden konnte, mit der Aufforderung, lerobot_find_cameras_opencv auszuführen, um eine verfügbare Kamera zu finden, und dass keine Kamera verbunden werden kann, sodass das Speichern von Bildern abgebrochen wird. Dieses Bild entspricht dem Kontext des Kameraverbindungsproblems und veranschaulicht den Fehler.](../../en/images/d32-03.png)

Ändern Sie die Datei `lerobot\src\lerobot\cameras\utils.py`, um das OpenCV-Backend auf `cv2.CAP_SHOW` umzustellen

![Das Bild zeigt den Code der Funktion `get_cv2_backend()` in der Datei `lerobot\\src\\lerobot\\cameras\\utils.py`. Wenn das System Windows ist, gibt die Funktion `int(cv2.CAP_DSHOW)` zurück, um unter Windows MSMF statt AVFOUNDATION zu verwenden. Der Code enthält außerdem einen Kommentar zu `cv2.CAP_MSMF` und dazu, wie andere Systeme wie Darwin (macOS) und Linux behandelt werden. Dieses Bild gehört zum Vorgang des Änderns der Datei `lerobot\\src\\lerobot\\cameras\\utils.py`, um das OpenCV-Backend zu `cv2.CAP_SHOW` zu ändern, und ist ein Beispiel für eine Codeänderung.](../../en/images/d32-04.png)

> Das ist ein Fehler, den nicht einmal Doubao lösen kann; das liegt alles daran, dass die lerobot-Bibliothek zu tief verschachtelt ist, und es ist für Anfänger sehr schwer zu debuggen

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## Mehrere Kameras anschließen: Teleoperation mit angezeigten Kamerabildern

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![Das Bild zeigt das rerun.io-Fenster, das für die Teleoperation mit Kamerabildern verwendet wird. Links ist ein Trajektoriendiagramm, das Trajektoriendaten für mehrere Gelenke zeigt, etwa observation_wrist_l_pos und observation_wrist_r_pos. Rechts ist oben das Live-Kamerabild und unten das Tencent-Meeting-Fenster. Oben rechts steht „Waiting for data on rerun: http://127.0.0.1:9678/remote...". Dieses Bild gehört zum Inhalt über das Anschließen mehrerer Kameras und die Anzeige von Kamerabildern während der Teleoperation und veranschaulicht den Effekt.](../../en/images/d32-05.png)
