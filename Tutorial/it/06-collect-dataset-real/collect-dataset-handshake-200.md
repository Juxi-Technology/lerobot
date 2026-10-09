[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | Italiano | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# Raccogliere un dataset per dimostrazione — Handshake 200

## Creare un repository di dataset su HuggingFace

https://huggingface.co/new-dataset

![L'immagine mostra l'interfaccia per creare un nuovo repository di dataset su HuggingFace. "Owner" è mostrato come TommyZihao, il nome del dataset è "lerobot_zihao_dataset_shake200", "License" è impostata su mit, e il tipo di dataset è "Public", visibile a chiunque mentre solo il proprietario del dataset o i membri dell'organizzazione possono fare commit. In basso, si nota che dopo aver creato il dataset è possibile caricare i file tramite l'interfaccia web o git, e c'è un pulsante "Create dataset" in fondo. Questa immagine è collegata al contenuto sulla creazione di un repository di dataset su HuggingFace e mostra l'interfaccia per l'operazione di creazione del dataset.](../../en/images/d37-01.png)

## Eliminare qualsiasi dataset esistente con lo stesso nome (se presente)

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Raccolta del dataset Shake200

Una telecamera, raccolta di un dataset - computer Mac

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

## Durante la raccolta

<grid>
<column width-ratio="0.508765">
![L'immagine mostra l'interfaccia del terminale durante la raccolta di un dataset su un Mac. Visualizza l'output di SvtInfo() e SvtInfo(), inclusi numero di versione, compilatore e architettura. Presenta anche i parametri di configurazione di SvtConfig(), come larghezza, altezza, frequenza di fotogrammi e preset. In basso c'è un output contrassegnato "INFO" e "INFO 0", come "Starting second pass: moving the moving atom to the beginning of the file". Questa immagine è collegata al contenuto "Durante la raccolta" e presenta la configurazione e le informazioni mostrate nel terminale durante la raccolta.](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![L'immagine mostra l'output del terminale durante la raccolta di un dataset con lo script Open_Duck_Mini_Runtime_2 su un Mac. Mostra SVT e altri parametri di configurazione della codifica video, come gop size e key - frame type, e presenta la versione del codificatore video e la data di build. In basso ci sono i log dei file MP4, come "Starting second pass: moving the moov atom to the beginning of the file". Questa immagine è collegata al flusso di lavoro della raccolta del dataset e presenta il riscontro del terminale durante la raccolta.](../../en/images/d37-03.png)
</column>
</grid>

Controlli con i tasti freccia della tastiera:  
→ (Freccia destra) Termina anticipatamente l'episodio corrente; passa all'episodio successivo.  
← (Freccia sinistra) Annulla l'episodio corrente; registralo di nuovo.  
ESC, ferma immediatamente, codifica il video e carica il dataset.

## Raccolta terminata — Directory di salvataggio del dataset

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
