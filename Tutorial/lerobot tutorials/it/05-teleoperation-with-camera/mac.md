[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | Italiano | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Computer Mac

## Collegare la telecamera al computer

```Shell
lerobot-find-cameras opencv
```

![L'immagine mostra il risultato di rilevamento dopo aver collegato una telecamera a un Mac. Elenca le due telecamere generate automaticamente, la telecamera esterna e la webcam frontale integrata del Mac. La Fps della telecamera esterna è 60.00024 e la Fps della telecamera integrata è 30.0. Questa immagine è collegata al contenuto sul collegamento di una telecamera a un Mac, presenta il risultato di rilevamento dopo la connessione e aiuta gli utenti a comprendere il tipo, l'ID, l'API di backend e la frequenza di fotogrammi di ciascuna telecamera.](../../en/images/d31-01.png)

## Una telecamera, teleoperazione con il feed della telecamera visualizzato

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

Dopo l'esecuzione, inizia la teleoperazione

Si apre la finestra di rerun.io, che mostra in tempo reale la traiettoria di ciascun giunto dei servo, insieme al feed live della telecamera

e salva le immagini nella directory `~/username/outputs/captured_images`

![L'immagine mostra la finestra di rerun.io che si apre all'avvio della teleoperazione dopo l'esecuzione. A sinistra ci sono i grafici delle traiettorie di diversi giunti dei servo, presentati come curve che mostrano il movimento dei diversi giunti. A destra, il feed della telecamera della scena interna è mostrato in tempo reale, dove si possono vedere un tavolo, delle sedie e alcuni oggetti. In basso c'è anche qualche informazione a barre. Questa immagine è strettamente correlata al contesto e presenta le traiettorie dei giunti dei servo e il feed live della telecamera durante la teleoperazione, e illustra anche che le immagini vengono salvate nella directory specificata.](../../en/images/d31-02.png)

## Più telecamere, teleoperazione con i feed delle telecamere visualizzati

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

![L'immagine mostra la finestra di rerun.io utilizzata per la teleoperazione con più feed di telecamera. A sinistra c'è il feed live della telecamera, che mostra oggetti su una scrivania; a destra ci sono i grafici dei dati che mostrano le traiettorie dei diversi giunti, come observation_wip. In basso c'è un'area Streams che elenca i dati di diversi giunti. In alto a destra ci sono le informazioni sui dati, come Application ID e Source IP. Questa immagine corrisponde al contenuto "Più telecamere, teleoperazione con i feed delle telecamere" e presenta i feed e i dati durante la teleoperazione.](../../en/images/d31-03.png)
