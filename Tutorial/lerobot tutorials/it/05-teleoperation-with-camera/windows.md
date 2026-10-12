[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | Italiano | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Computer Windows

## Collegare la telecamera al computer

```Shell
lerobot-find-cameras opencv
```

![Questa immagine è la finestra della riga di comando di Windows, che mostra errori di connessione della telecamera e risultati di rilevamento dei dispositivi. In alto c'è un errore: "ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range". Sotto elenca le telecamere rilevate, tra cui Camera #0 e Camera #1, con nome, tipo, API di backend, configurazione di stream predefinita, formato, origine, larghezza, altezza e frequenza di fotogrammi; in basso ci sono errori come "lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0". Questo corrisponde allo scenario di errore menzionato nel documento, "la telecamera non riesce a connettersi, ma cambiando telecamera in Tencent Meeting si apre comunque normalmente", ed è il riscontro reale dell'errore di runtime prima di modificare il codice del backend OpenCV.](../../en/images/d32-01.png)

## Teleoperazione con il feed della telecamera visualizzato

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

Si apre la finestra di rerun.io, che mostra in tempo reale la traiettoria di ciascun giunto dei servo, insieme al feed live della telecamera

e salva le immagini nella directory `C:\Users\username\outputs\captured_images`

![L'immagine mostra la finestra di rerun.io, che visualizza in tempo reale le traiettorie dei giunti dei servo e il feed live della telecamera. A sinistra c'è l'interfaccia blueprint con opzioni come "teleoperation". Al centro c'è il grafico delle traiettorie, che mostra i dati di posizione dei giunti come "observation_wrist_rot.pos". A destra c'è il feed della telecamera, che mostra la scena dal punto di vista del robot. In alto a destra mostra "Waiting for data on rerun: http://127.0.0.1:9876/remote...", con sotto le informazioni sull'origine dei dati. Questa immagine è collegata al contenuto che descrive la finestra di rerun.io che mostra il feed della telecamera in tempo reale e ne presenta l'effetto.](../../en/images/d32-02.png)

## Se incontri il seguente errore

La telecamera non riesce a connettersi, ma cambiando telecamera in Tencent Meeting si apre comunque normalmente

![L'immagine mostra l'interfaccia a riga di comando di Windows con i risultati di rilevamento delle telecamere. In alto mostra "Detected Cameras" e informazioni relative alle telecamere come nome, tipo, ID e API di backend. In basso c'è un errore che indica che durante l'esecuzione di lerobot_find_cameras_openpyc la telecamera OpenCV non è riuscita a connettersi o a essere configurata, invitando a eseguire lerobot_find_cameras_opencv per trovare una telecamera disponibile, e che non è possibile connettere alcuna telecamera perciò il salvataggio delle immagini verrà interrotto. Questa immagine corrisponde al contesto del problema di connessione della telecamera e presenta l'errore.](../../en/images/d32-03.png)

Modifica il file `lerobot\src\lerobot\cameras\utils.py` per cambiare il backend OpenCV in `cv2.CAP_SHOW`

![L'immagine mostra il codice della funzione `get_cv2_backend()` nel file `lerobot\\src\\lerobot\\cameras\\utils.py`. Quando il sistema è Windows, la funzione restituisce `int(cv2.CAP_DSHOW)`, usato per utilizzare MSMF invece di AVFOUNDATION su Windows. Il codice contiene anche un commento su `cv2.CAP_MSMF`, e su come vengono gestiti altri sistemi come Darwin (macOS) e Linux. Questa immagine è collegata all'operazione di modifica del file `lerobot\\src\\lerobot\\cameras\\utils.py` per cambiare il backend OpenCV in `cv2.CAP_SHOW`, ed è un esempio di modifica del codice.](../../en/images/d32-04.png)

> Questo è un bug che nemmeno Doubao riesce a risolvere; tutto perché la libreria lerobot è incapsulata in modo troppo profondo, ed è molto difficile per i principianti fare il debug

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## Collegare più telecamere, teleoperazione con i feed delle telecamere visualizzati

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![L'immagine mostra la finestra di rerun.io utilizzata per la teleoperazione con i feed delle telecamere. A sinistra c'è un grafico delle traiettorie che mostra i dati di traiettoria di diversi giunti, come observation_wrist_l_pos e observation_wrist_r_pos. A destra, in alto c'è il feed live della telecamera e in basso la finestra di Tencent Meeting. In alto a destra mostra "Waiting for data on rerun: http://127.0.0.1:9678/remote...". Questa immagine è collegata al contenuto sul collegamento di più telecamere e sulla visualizzazione dei feed delle telecamere durante la teleoperazione e ne presenta l'effetto.](../../en/images/d32-05.png)
