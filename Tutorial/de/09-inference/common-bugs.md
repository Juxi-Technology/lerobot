[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | Deutsch | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# Häufige Fehler und Behebungen

## Kameraaufnahme schlägt fehl

![Dieses Bild zeigt die Terminalausgabe beim Ausführen des LeRobot-Robotercodes. Die `INFO`-Logs zeigen das Öffnen der OpenCV-Kamera und das Trennen des Follower; das `ERROR`-Log weist darauf hin, dass in der Datei `camera_opencv.py` die Funktion `read` wegen `OpenCVCamera(0) read failed` einen `RuntimeError` ausgelöst hat. Das Bild bezieht sich auf das Problem „Kameraaufnahme schlägt fehl" und zeigt das auftretende Problem beim Ausführen des Codes, um die konkrete Ursache des Ausfalls der Kameraaufnahme zu erläutern.](../../en/images/d65-01.png)

Prüfen Sie, ob das Kabel der Handgelenkkamera locker ist, insbesondere das Ende nahe der Kamera – dieser Steckverbinder neigt stark zu schlechtem Kontakt

## Kamera trennt die Verbindung

![Dieses Bild zeigt die Laufzeitoberfläche des Codes /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py. Oben sind Uhrzeit, Prozess-ID und weitere Informationen zu sehen; darunter Code-Pfade und Fehlermeldungen wie /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py und „INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.". Der zentrale Teil ist „raise TimeoutError" und „TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.", was anzeigt, dass die Kameraaufnahme fehlgeschlagen ist. Das Bild bezieht sich auf das Problem „Kameraaufnahme schlägt fehl" und zeigt den Fehler.](../../en/images/d65-02.png)

Starten Sie die Kommandozeile neu

## Servo-Kommunikationsproblem 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![Dieses Bild zeigt Folgendes.](../../en/images/d65-03.png)

Die Lösung: Ändern Sie im Code unter `lerobot/src/lerobot/motors/motors_bus.py` jedes `num_retry` auf 99, insbesondere das in der Zeile, die den Fehler auslöst

![Dieses Bild zeigt den Inhalt der Codedatei `motors_bus.py` im LeRobot-Projekt. Die Methode `write` der Klasse `MotorsBusABC` ist hervorgehoben, wobei die Variable `num_retry` auf `99` geändert wurde. Das Bild bezieht sich auf den Abschnitt „Servo-Kommunikationsproblem 1" und entspricht der Behebung, im Code unter `lerobot/src/lerobot/motors/motors_bus.py` jedes `num_retry` auf 99 zu ändern, insbesondere das in der Zeile, die den Fehler auslöst.](../../en/images/d65-04.png)

## Servo-Kommunikationsproblem 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![Dieses Bild zeigt eine Kommandozeilensitzung im zsh-Terminal unter macOS. Das Terminal zeigt mehrere Dateipfade und Codezeilennummern, etwa `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`. Zeile 587 der Datei `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` löst einen `ConnectionError` aus und meldet ein fehlgeschlagenes Schreiben von `Torque_Enable` bei id=1 ohne Statuspaket. Das Bild bezieht sich auf den Inhalt „Servo-Kommunikationsproblem 2" und zeigt die Codeausführung im Moment des Fehlers.](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![Dieses Bild zeigt eine Kommandozeilensitzung im zsh-Terminal unter macOS. Das Terminal zeigt mehrere Dateipfade und Codezeilennummern, etwa `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`. Hier, `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

Lösung: Kalibrieren Sie den Roboterarm neu
