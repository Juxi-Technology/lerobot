[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | Italiano | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# Bug comuni e soluzioni

## La cattura della telecamera fallisce

![Questa immagine mostra l'output del terminale quando viene eseguito il codice robot di LeRobot. I log `INFO` mostrano l'apertura della telecamera OpenCV e la disconnessione del Follower; il log `ERROR` segnala che nel file `camera_opencv.py` la funzione `read` ha sollevato un `RuntimeError` a causa di `OpenCVCamera(0) read failed`. L'immagine è collegata al problema "La cattura della telecamera fallisce", mostrando visivamente il problema che compare quando il codice viene eseguito e aiutando a spiegare la causa specifica del fallimento della cattura.](../../en/images/d65-01.png)

Controlla se il cavo della telecamera del polso è allentato, soprattutto l'estremità vicino alla telecamera — quel connettore è molto soggetto a falsi contatti

## La telecamera si disconnette

![Questa immagine mostra l'interfaccia in esecuzione per il codice /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py. In alto mostra l'orario, l'ID del processo e altre informazioni; sotto ci sono percorsi di codice e messaggi di errore come /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py e "INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.". La parte chiave è "raise TimeoutError" e "TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.", che indica che la cattura della telecamera è fallita. L'immagine è collegata al problema "La cattura della telecamera fallisce" e mostra visivamente l'errore.](../../en/images/d65-02.png)

Riavvia la riga di comando

## Problema di comunicazione con il servo 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![Questa immagine mostra quanto segue.](../../en/images/d65-03.png)

La soluzione: cambia ogni `num_retry` nel codice in `lerobot/src/lerobot/motors/motors_bus.py` a 99, soprattutto quello sulla riga che genera l'errore

![Questa immagine mostra il contenuto del file di codice `motors_bus.py` nel progetto LeRobot. È evidenziato il metodo `write` della classe `MotorsBusABC`, con la variabile `num_retry` impostata a `99`. L'immagine è collegata alla sezione "Problema di comunicazione con il servo 1" e corrisponde alla correzione che imposta a 99 ogni `num_retry` nel codice in `lerobot/src/lerobot/motors/motors_bus.py`, soprattutto quello sulla riga che genera l'errore.](../../en/images/d65-04.png)

## Problema di comunicazione con il servo 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![Questa immagine mostra una sessione da riga di comando nel terminale zsh su macOS. Il terminale mostra diversi percorsi di file e numeri di riga del codice, come `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`. La riga 587 del file `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` solleva un `ConnectionError`, segnalando un fallimento di scrittura di `Torque_Enable` su id=1 senza alcun status packet. L'immagine è collegata al contenuto "Problema di comunicazione con il servo 2" e mostra visivamente l'esecuzione del codice al momento dell'errore.](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![Questa immagine mostra una sessione da riga di comando nel terminale zsh su macOS. Il terminale mostra diversi percorsi di file e numeri di riga del codice, come `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`. Qui, `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

Soluzione: ricalibra il braccio robotico
