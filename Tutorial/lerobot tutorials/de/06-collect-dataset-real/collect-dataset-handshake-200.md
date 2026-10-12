[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | Deutsch | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# Einen Datensatz durch Vorführen aufnehmen — Handshake 200

## Ein Dataset-Repo auf HuggingFace erstellen

https://huggingface.co/new-dataset

![Das Bild zeigt die Oberfläche zum Erstellen eines neuen Datensatz-Repositories auf HuggingFace. „Owner" wird als TommyZihao angezeigt, der Datensatzname ist „lerobot_zihao_dataset_shake200", „License" ist auf mit gesetzt und der Datensatztyp ist „Public", für alle sichtbar, wobei nur der Datensatzeigentümer oder Organisationsmitglieder committen können. Darunter wird darauf hingewiesen, dass Sie den Datensatz nach dem Erstellen über die Weboberfläche oder git hochladen können, und unten befindet sich eine Schaltfläche „Create dataset". Dieses Bild gehört zum Inhalt über das Erstellen eines Dataset-Repos auf HuggingFace und zeigt die Oberfläche für den Vorgang des Erstellens eines Datensatzes.](../../en/images/d37-01.png)

## Einen vorhandenen Datensatz mit demselben Namen löschen (falls vorhanden)

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Datensatzaufnahme Shake200

Eine Kamera: einen Datensatz aufnehmen - Mac-Rechner

```Shell
lerobot-record \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true \
    --dataset.repo_id=Tommymy/lerobot_my_dataset_shake200 \
    --dataset.num_episodes=200 \
    --dataset.single_task="Shanke Hands" \
    --dataset.push_to_hub=false \
    --dataset.episode_time_s=12 \
    --dataset.reset_time_s=1
```

## Während der Aufnahme

<grid>
<column width-ratio="0.508765">
![Das Bild zeigt die Terminaloberfläche während der Aufnahme eines Datensatzes auf einem Mac. Es zeigt die Ausgabe von SvtInfo() und SvtInfo(), einschließlich Versionsnummer, Compiler und Architektur. Außerdem werden die Konfigurationsparameter von SvtConfig() dargestellt, etwa Breite, Höhe, Bildrate und Preset. Darunter gibt es eine mit „INFO" und „INFO 0" gekennzeichnete Ausgabe, etwa „Starting second pass: moving the moving atom to the beginning of the file". Dieses Bild gehört zum Inhalt „Während der Aufnahme" und veranschaulicht die während der Aufnahme im Terminal angezeigte Konfiguration und Informationen.](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![Das Bild zeigt die Terminalausgabe während der Aufnahme eines Datensatzes mit dem Skript Open_Duck_Mini_Runtime_2 auf einem Mac. Es zeigt SVT und weitere Konfigurationsparameter der Videocodierung, etwa gop size und key - frame type, und stellt die Version und das Build-Datum des Videoencoders dar. Darunter gibt es MP4-Dateiprotokolle, etwa „Starting second pass: moving the moov atom to the beginning of the file". Dieses Bild gehört zum Arbeitsablauf der Datensatzaufnahme und veranschaulicht die Terminalrückmeldung während der Aufnahme.](../../en/images/d37-03.png)
</column>
</grid>

Tastatursteuerung über die Pfeiltasten:  
→ (Pfeil nach rechts) Die aktuelle Episode vorzeitig beenden; zur nächsten Episode übergehen.  
← (Pfeil nach links) Die aktuelle Episode verwerfen; erneut aufnehmen.  
ESC: sofort stoppen, das Video codieren und den Datensatz hochladen.

## Aufnahme abgeschlossen — Speicherverzeichnis des Datensatzes

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
