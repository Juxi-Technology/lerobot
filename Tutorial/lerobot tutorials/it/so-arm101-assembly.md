[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | Italiano | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>Tutorial di assemblaggio del kit del braccio robotico SO-ARM101</title>

<callout emoji="💡">
Nota: salta questo tutorial se hai un braccio premontato
</callout>

## Parti stampate in 3D per il braccio follower

![Questa immagine mostra le parti stampate in 3D per il braccio follower necessarie per assemblare il braccio robotico SO-ARM101, tutte parti in plastica PLA bianche disposte su una superficie chiara con venatura del legno. Le parti includono connettori di varie forme, una struttura a forcella con griglia, una parte tipo base con fori, un braccio di supporto a forcella di forma speciale e così via, in linea con l'osservazione del tutorial che l'estremità del braccio follower è un gripper. Queste parti sono i pezzi stampati di base per il braccio follower e sono gli oggetti manipolati nel passaggio di rimozione dei supporti, e corrispondono direttamente alle parti stampate in 3D del braccio follower presentate nel tutorial.](../en/images/d09-01.jpg)

## Parti stampate in 3D per il braccio leader

![L'immagine mostra parti stampate in 3D per il braccio robotico SO-ARM101. Varie parti stampate in 3D di colore nero sono disposte ordinatamente nella cornice, con linee blu sui bordi di alcune parti. Queste parti includono componenti strutturali per i bracci leader e follower, come il gripper, il manico e il grilletto, oltre ai connettori. L'immagine corrisponde alla sezione "Parti stampate in 3D per il braccio leader" del documento e presenta visivamente l'aspetto delle parti stampate in 3D, offrendo un riferimento per i passaggi successivi di rimozione dei supporti residui e di distinzione dei servo.](../en/images/d09-02.jpg)

I bracci leader e follower sono molto simili; differisce solo l'estremità

Il leader ha un manico e un grilletto; il follower ha un gripper

## Rimuovere i supporti residui dalle parti stampate in 3D

Controlla ogni foro, apertura, fessura e griglia, specialmente i cinque fori che assomigliano alla tessera "cinque punti" del mahjong

Questo passaggio è molto importante; altrimenti non riuscirai ad avvitare le viti più avanti

## Distinguere i quattro servo

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">Dimensione grande</td><td vertical-align="middle">Dimensione piccola</td><td vertical-align="middle">Tensione (V)</td><td vertical-align="middle">Rapporto di riduzione</td><td vertical-align="middle">Articolazione del braccio</td><td vertical-align="middle">Quantità</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7,4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7,4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7,4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Tutte le articolazioni del follower</td><td vertical-align="middle">6</td></tr></tbody></table>

> Il rapporto di riduzione è il rapporto tra "velocità del motore : velocità dell'albero di uscita del servo"; ad esempio, 1:345 significa che il motore compie 345 giri perché l'albero di uscita ne compia uno.
> 
> Un rapporto di riduzione elevato moltiplica la coppia attraverso il treno di ingranaggi, quindi può azionare un carico più pesante (come il braccio follower)
> 
> Ma allo stesso tempo l'albero di uscita gira più lentamente (perché è "ridotto")
> 
> Anche trascinare l'articolazione richiede più sforzo

Di seguito sono riportati i modelli e i rapporti di riduzione di tutti i servo di questo progetto; le parti sottolineate sono i loro numeri

![L'immagine mostra i modelli, le tensioni e i rapporti di riduzione dei servo utilizzati nel braccio. A sinistra c'è il braccio leader, con due modelli, C046 (7,4V, 1:147) e C044 (7,4V, 1:191); a destra c'è il braccio follower, con due modelli, C001 (7,4V, 1:345) e C047 (12V, 1:345). L'immagine è strettamente legata al contesto, che presenta in dettaglio i modelli, le tensioni e i rapporti di riduzione dei servo dei bracci leader e follower; questa immagine presenta visivamente queste cifre chiave per aiutare i lettori a comprendere meglio la configurazione dei servo.](../en/images/d09-03.png)

![L'immagine mostra quattro scatole di servo etichettate "STS3215". Su ogni scatola è stampata la parola "SPECIFICATION" e sono riportati parametri come coppia, velocità e dimensioni, ad esempio una coppia di 9,2kg·cm/127,98oz·in(6V). L'STS3215-C001 ha una coppia di 12,5kg·cm/173,88oz·in(6V), e l'STS3215-C046 ha una coppia di 16kg·cm/220,58oz·in(7V). Questi servo sono il modello utilizzato per tutte le articolazioni del braccio follower, corrispondente al braccio follower presentato nel documento, e vengono usati per l'installazione dei servo nei passaggi di assemblaggio successivi.](../en/images/d09-04.jpg)

## Distinguere i due alimentatori

Alimentatore 5V 6A 30W: alimenta i servo da 7,4V (braccio leader), nero

Alimentatore 12V 5A 60W, alimenta i servo da 12V (braccio follower), bianco

## Scaricare lo strumento di debug per servo Feetech

### Windows PC

https://gitee.com/ftservo/fddebug

Scarica [`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z), estrailo e avvia il programma exe che contiene

### Ubuntu e Mac (l'archivio include un tutorial)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![Questa immagine è un'illustrazione ausiliaria per il tutorial di assemblaggio del kit del braccio robotico SO-ARM101, corrispondente alla sezione sulla distinzione degli alimentatori. Mostra due modelli di servo e le loro posizioni di montaggio, STS3215-C001 e STS3215-C018, e etichetta anche servo come STS3215-C004, corrispondenti alle diverse articolazioni del braccio. La figura elenca inoltre i parametri di questi due servo, tra cui velocità di rotazione, coppia di stallo, precisione del servo, funzioni di protezione e feedback dei parametri, offrendo un riferimento per la scelta e l'installazione dei servo durante l'assemblaggio del braccio.](../en/images/d09-05.jpg)

**Versione Pro: il braccio leader usa un alimentatore 5V6A, e il braccio follower usa un alimentatore 12V5A**

L'impostazione degli ID dei servo, la calibrazione dell'angolo dei servo e l'assemblaggio devono essere fatti in anticipo; fai riferimento al [tutorial di assemblaggio ufficiale](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# Passo 1: Impostare gli ID dei servo e installare i corni dei servo (tranne il servo 5)

<grid>
<column width-ratio="0.500000">
![L'immagine mostra l'interfaccia dello strumento di debug host Feetech. L'interfaccia ha tre schede, "Debug", "Program" e "Upgrade", con "Program" attualmente selezionata. Informazioni chiave: 1. Nelle impostazioni di comunicazione, il numero di porta è COM6 e il baud rate è 1000000; 2. Nelle operazioni sui servo, scrittura sincrona, scrittura asincrona e output di coppia sono tutte selezionate; 3. Nel feedback dei servo, parametri come tensione, corrente, temperatura e posizione mostrano tutti 0; 4. Nella ricerca dei servo, è selezionato l'id 1, modello ST53215. Questa immagine è legata alle operazioni di debug descritte sopra, come l'impostazione degli ID dei servo e l'installazione del corno del servo, e presenta l'interfaccia dello strumento di debug.](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![L'immagine mostra l'interfaccia dello strumento di debug host Feetech, usata per impostare gli ID dei servo. L'interfaccia ha tre schede, "Debug", "Program" e "Upgrade", con "Program" attualmente selezionata. Nell'area "Center calibration", il numero di ID è 4, con un pulsante "Save" a destra. Sul lato sinistro dell'interfaccia sono mostrati l'ID del servo, il modello e altre informazioni. Questa immagine è legata al contenuto "Passo 1: Impostare gli ID dei servo e installare i corni dei servo (tranne il servo 5)" del documento e presenta l'interfaccia dell'operazione di impostazione dell'ID del servo, mostrando visivamente dove viene impostato il numero di ID.](../en/images/d09-07.png)
</column>
</grid>

1. Apri lo strumento di debug host Feetech, seleziona la porta COM, imposta il baud rate a un milione e fai clic su "Open"
2. Fai clic su "Search"; quando compare "STS3215", fai clic su "Stop" e poi su "STS3215"
3. Seleziona "Debug" in alto; puoi trascinare il cursore per ruotare il servo, oppure fare clic su "Scan" per farlo muovere avanti e indietro. Conferma che il servo funzioni normalmente
4. Seleziona "Program" in alto
5. Fai clic su "Center calibration" per impostare la posizione attuale dell'albero di rotazione del servo come centro (0-4095)
6. Fai clic su "ID", imposta il numero di ID del servo corrispondente nell'angolo in basso a destra e fai clic su "Save". Nota che il numero è composto da semplici cifre arabe, senza lettere.
7. Scollega il cavo che collega il servo alla scheda di controllo
8. Collega il cavo del servo al servo

Il servo 1 riceve due cavi; gli altri servo ricevono per ora un solo cavo

![L'immagine mostra l'installazione dei servo durante l'assemblaggio del kit del braccio SO-ARM101. Nella cornice ci sono il braccio follower e il braccio leader, con il braccio follower numerato 123456 e il braccio leader numerato 123456. I servo sono etichettati con rapporti di riduzione di 1:345, 1:191 e 1:147. Sotto c'è la scheda di controllo, collegata a due cavi, uno bianco e uno nero. Questa immagine è legata ai passaggi di assemblaggio sopra e presenta visivamente le posizioni di montaggio e i numeri dei servo, aiutando chi assembla ad abbinare accuratamente i servo alla scheda di controllo.](../en/images/d09-08.png)

<callout emoji="💡">
Di nuovo: assicurati che l'ID dell'articolazione e il rapporto di riduzione di ogni servo corrispondano esattamente al **SO-ARM101**.
</callout>

Ogni motore sul bus ha un ID univoco. I motori nuovi di solito hanno un ID predefinito pari a `1`. Per garantire che la comunicazione tra i motori e il controller funzioni, dobbiamo prima impostare un ID univoco per ogni motore. Inoltre, la velocità di trasmissione dei dati sul bus è determinata dal baud rate. Per comunicare tra loro, il controller e tutti i motori devono essere configurati con lo stesso baud rate; i servo di questo braccio usano un baud rate di 100000.

Per farlo, dobbiamo prima collegare il controller a ciascun motore a turno per poterli configurare. Poiché scriviamo questi parametri nell'area non volatile della memoria interna del motore (EEPROM), questa operazione va eseguita una sola volta.

Se stai riutilizzando motori provenienti da un altro robot, potresti dover eseguire comunque questo passaggio, perché gli ID e i baud rate potrebbero non corrispondere.

Il video seguente mostra la sequenza di passaggi per impostare gli ID dei motori.

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Usa lo strumento host per servo Feetech per impostare gli ID dei servo e calibrare il centro. Gli ID vanno impostati da 1 a 6!

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu e Mac

<callout emoji="💡">
Se ti serve lo strumento host per servo Feetech, fai riferimento allo [strumento di debug per servo Feetech](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb) qui sopra
</callout>

Completa prima la configurazione dell'ambiente seguendo la pagina [dell'installazione ufficiale di LeRobot](https://huggingface.co/docs/lerobot/installation)

<callout emoji="💡">
Ricorda di attivare l'ambiente virtuale e di entrare nella directory src/lerobot corrispondente
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. Trova la porta USB del braccio. Per trovare la porta corretta di ciascun braccio, esegui lo script di utility due volte::

```Plain Text
lerobot-find-port
```

Esempio di output quando si identifica la porta del braccio Leader (ad esempio `/dev/tty.usbmodem575E0031751` su un Mac, o eventualmente `/dev/ttyACM0` su Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

Esempio di output quando si identifica la porta del braccio Follower (ad esempio `/dev/tty.usbmodem575E0032081`, o eventualmente `/dev/ttyACM1` su Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
Ricorda di scollegare il connettore USB, altrimenti la porta non può essere rilevata.
</callout>

2. Collega il PC alla scheda driver dei servo del braccio follower con un cavo USB e accendilo. Poi esegui il comando seguente. Cambia --robot.port=/dev/ttyACM0 nel comando con la porta che hai trovato. Ad esempio, se la porta che hai trovato è /dev/ttyACM1, cambiala in --robot.port=/dev/ttyACM1

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

Vedrai il seguente output.

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

Seguendo le istruzioni, collega il servo del gripper. Assicurati che sia l'unico servo collegato alla scheda driver dei servo e che questo servo non sia ancora collegato a nessun altro servo. Dopo aver premuto **[Enter]**, lo script imposta automaticamente l'ID e il baud rate di quel servo. Gli ID vanno impostati da 6 a 1!

Dopodiché, dovresti vedere quanto segue:

```Python
'gripper' motor id set to 6
```

Poi il successivo output è:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**Nota** Ripeti quanto sopra per ogni servo, seguendo le istruzioni.
Come per i servo precedenti, assicurati che sia l'unico servo collegato alla scheda driver e che il servo stesso non sia collegato a nessun altro servo.
</callout>

Prima di premere **Enter** ogni volta, assicurati di controllare i collegamenti dei cavi. Ad esempio, il cavo di alimentazione potrebbe allentarsi mentre si maneggia la scheda del circuito.

Quando hai completato tutti i passaggi, lo script termina automaticamente e i servo sono pronti all'uso. Ora puoi collegare a turno il connettore a 3 pin di ogni servo e collegare il cavo del primo servo (il servo "shoulder pan" con ID 1) alla scheda driver. La scheda driver può ora essere montata sulla base del braccio.

Ripeti gli stessi passaggi per il braccio leader.

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# Passo 2: Assemblaggio

<callout emoji="💡">
- I passaggi di assemblaggio del braccio follower sono essenzialmente gli stessi di quelli del braccio leader. L'unica differenza è che dopo il passaggio 12 l'end effector (gripper e manico) viene installato in modo diverso.
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
Installazione della scheda driver dei servo: monta prima i 4 distanziali in ottone, poi fissa la scheda driver con quattro viti M2.5\*8
</callout>

<grid>
<column width-ratio="0.525947">
![Installa i quattro distanziali in ottone](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![Fissa la scheda driver dei servo con viti M2.5*8](../en/images/d09-10.webp)
</column>
</grid>

![Monta sul braccio e collega i cavi](../en/images/d09-11.png)

**Versione Pro: il braccio leader nero usa un alimentatore 5V6A, e il braccio follower bianco usa un alimentatore 12V5A**







# Impostare gli ID dei servo e la calibrazione del centro nella UI web

https://bambot.org/feetech.js?lang=zh

1. Inserisci 0 o 1 a seconda del modello di servo, poi fai clic su "Connect"

![L'immagine mostra l'interfaccia "Connect" nel tutorial di assemblaggio del kit del braccio. A sinistra dell'interfaccia c'è la parola "Connect", e a destra ci sono un menu a tendina "Baud rate" impostato su 1,000,000 bps (Index 0), e una casella di input per "Protocol end (0=STS/SMS, 1=SCS)" impostata su 0, con un riquadro rosso attorno al numero "1" accanto alla casella di input. Sotto c'è un pulsante verde "Connect", con un riquadro rosso attorno al numero "2" accanto. In basso è mostrato "Status: Disconnected". Questa immagine corrisponde al contenuto sopra, "Inserisci 0 o 1 a seconda del modello di servo, poi fai clic su 'Connect'", e presenta visivamente le impostazioni dell'operazione di connessione.](../en/images/d09-12.png)

2. Scansiona i servo con ID da 1\~6; usa FOUND nei risultati della scansione per confermare il servo con l'ID corrispondente. Ad esempio, nell'immagine è stato trovato il servo con ID 1

![L'immagine mostra l'interfaccia del passaggio "Scan servos" nel tutorial di assemblaggio del kit del braccio SO-ARM101. In alto nell'interfaccia ci sono le caselle di input "Start ID" e "End ID", attualmente con start ID 1 e end ID 6. Sotto c'è un pulsante "Start scan". Nei risultati della scansione, scansionando gli ID da 1 a 6 non viene trovato alcun servo, con la segnalazione "Exception: No status packet! Error code: 0". Questa immagine è strettamente legata al contesto e presenta visivamente l'interfaccia e i risultati della scansione dei servo, aiutando gli utenti a comprendere lo stato della scansione dei servo.](../en/images/d09-13.png)

3. Impostazione dell'ID e calibrazione del centro

① Imposta l'ID del servo corrente sul valore dell'ID del servo scansionato

② Inserisci un numero in "ID management" e fai clic su "Change ID" per impostare l'ID

③ Calibrazione del centro (il centro del servo STS3215 è 2047, il centro del servo SCS0009 è 511)

Servo STS: inserisci 2047 in "Position control" e fai clic su "Set"

Servo SCS: inserisci 511 in "Position control" e fai clic su "Set"

![L'immagine mostra un'interfaccia di controllo di un singolo servo. L'ID del servo corrente è 1; dopo aver inserito il numero 1 in ID management e aver fatto clic su "Change ID", compare il messaggio "Success: ID changed to 1". In Position Control il valore è 2047 e facendo clic sul pulsante "Set" viene applicato. Questa immagine è legata al contesto "Impostazione dell'ID e calibrazione del centro" e presenta visivamente l'interfaccia dell'operazione di impostazione dell'ID, aiutando gli utenti a comprendere come inserire un numero in "ID management" per impostare l'ID e come inserire il valore del centro in "Position control" e fare clic su "Set" per concludere.](../en/images/d09-14.png)
