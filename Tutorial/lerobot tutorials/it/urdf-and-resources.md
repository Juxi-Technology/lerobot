[English](../en/urdf-and-resources.md) | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | [Español](../es/urdf-and-resources.md) | [Français](../fr/urdf-and-resources.md) | Italiano | [日本語](../ja/urdf-and-resources.md) | [한국어](../ko/urdf-and-resources.md) | [Português (BR)](../pt-br/urdf-and-resources.md) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>File URDF e risorse di riferimento</title>

# Il [file URDF](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf) ufficiale di Lerbot



## URDF Studio

https://urdf.d-robotics.cc/



## Controllo della simulazione ROS2 (implementalo tu stesso)

https://github.com/holmsslk/so-arm-moveit-hardware



## L'interfaccia grafica ufficiale di LeRobot

https://github.com/huggingface/leLab

LeLab è una web app che riunisce l'intero flusso di lavoro di LeRobot — calibrazione, teleoperazione, registrazione, addestramento, riproduzione — in un'unica interfaccia nel browser. Basta collegare il braccio robotico, aprire l'app e puoi iniziare a lavorare. Nessun lavoro complicato da riga di comando e nessun input da tastiera necessario.

🤗 Il punto di accesso web nativo di LeRobot, pensato per portare i nuovi utenti da "pronto all'uso" ad "addestrare la propria prima policy" in pochi minuti.

🤗 Installa e avvia tutto con un solo comando.



# Controllare il braccio Follower da un telefono

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## Sviluppo di robotica cloud: dispositivi ROS 2 e simulazione Isaac Sim LeRobot e streaming di dati su AWS

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## Impostare gli ID dei servo e la calibrazione del centro nella UI web

https://bambot.org/feetech.js?lang=zh

1. Inserisci 0 o 1 a seconda del modello di servo, poi fai clic su "Connect"

![L'immagine mostra l'interfaccia di connessione per impostare gli ID dei servo e la calibrazione del centro nella UI web. L'interfaccia ha una sezione "Connect" che contiene un menu a tendina per il baud rate, attualmente impostato su "1,000,000 bps (Index 0)"; un menu a tendina per il protocollo, attualmente impostato su "0=STS/SMS"; e un pulsante "Connect". In fondo all'interfaccia è mostrato "Status: Disconnected". L'immagine è strettamente legata al contesto: dopo aver inserito 0 o 1 a seconda del modello di servo e aver fatto clic su "Connect", vengono scansionati i servo con ID 1~6 per confermare il servo con l'ID corrispondente — questa è un'interfaccia chiave di quel flusso.](../en/images/d68-01.png)

2. Scansiona i servo con ID da 1\~6; usa FOUND nei risultati della scansione per confermare il servo con l'ID corrispondente. Ad esempio, nell'immagine è stato trovato il servo con ID 1

![L'immagine mostra l'interfaccia di scansione dei servo nell'URDF Studio ufficiale di Lerbot. L'interfaccia mostra un ID iniziale di 1 e un ID finale di 6, con un pulsante "Start scan" sotto. Nei risultati della scansione, scansionando l'ID1 è stato trovato l'ID1239, mentre scansionando dall'ID2 all'ID6 viene segnalato ogni volta "ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0". Questa immagine è legata all'operazione di scansione dei servo nell'URDF Studio ufficiale di Lerbot descritta nel contesto e presenta visivamente il processo di scansione e i suoi risultati.](../en/images/fix-01.png)

3. Impostazione dell'ID e calibrazione del centro

① Imposta l'ID del servo corrente sul valore dell'ID del servo scansionato

② Inserisci un numero in "ID management" e fai clic su "Change ID" per impostare l'ID

③ Calibrazione del centro (il centro del servo STS3215 è 2047, il centro del servo SCS0009 è 511)

Servo STS: inserisci 2047 in "Position control" e fai clic su "Set"

Servo SCS: inserisci 511 in "Position control" e fai clic su "Set"

![L'immagine mostra l'interfaccia di controllo di un singolo servo di Lerbot. Il "Current servo ID" è mostrato come 1; sotto, in "ID management", ci sono il numero 1 e un pulsante "Change ID", con il messaggio "Success: ID changed to 1" al di sotto. Nell'area Position Control c'è un pulsante "Read position" che mostra la posizione 2047, accanto a un pulsante "Set". Questa immagine è legata alla sezione "Impostazione dell'ID e calibrazione del centro" del documento e presenta visivamente l'interfaccia per impostare gli ID dei servo e calibrare il centro, aiutando gli utenti a comprendere come eseguire queste impostazioni in Lerbot.](../en/images/d68-02.png)
