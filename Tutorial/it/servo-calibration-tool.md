[English](../en/servo-calibration-tool.md) | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | [Deutsch](../de/servo-calibration-tool.md) | [Español](../es/servo-calibration-tool.md) | [Français](../fr/servo-calibration-tool.md) | Italiano | [日本語](../ja/servo-calibration-tool.md) | [한국어](../ko/servo-calibration-tool.md) | [Português (BR)](../pt-br/servo-calibration-tool.md) | [Português (PT)](../pt-pt/servo-calibration-tool.md)

# Strumento di calibrazione dei servo STS3215 per la serie So-ARM (opzionale)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**Un toolkit di calibrazione in fabbrica dei servo FTServo e di calibrazione LeRobot, pensato per i bracci della serie So-ARM 10X**

> ⚠️ **Nota di compatibilità: questo sistema attualmente supporta solo servo Feetech (serie STS3215)**. La tabella dei registri, il formato dei parametri xdat e la tabella dei baud rate sono tutti pensati per la serie Feetech STS3215.

> 📜 **Origine e crediti: questo strumento è adattato e potenziato dal progetto** [**Seeed_RoboController di Seeed Studio**](https://github.com/Seeed-Studio), originariamente rilasciato con licenza MIT. Pur mantenendo la funzionalità principale originale, questo progetto riorganizza la GUI e aggiunge il debugger FT, il backup/ripristino dei parametri xdat, il supporto multipiattaforma, la commutazione cinese/inglese e altri miglioramenti.

---

## ✨ Funzionalità

| Funzionalità | Descrizione |
|-|-|
| Rilevamento automatico della porta | Rileva in modo intelligente le porte seriali USB e filtra i dispositivi virtuali |
| Supporto multipiattaforma | Compatibile con Windows / Ubuntu / macOS |
| Sincronizzazione a doppia porta | Le porte seriali sinistra e destra operano in modo indipendente, con supporto per il controllo remoto a doppia porta sincronizzato leader/follower |
| Commutazione cinese/inglese | Passaggio con un clic tra cinese/inglese nella UI, con la scelta ricordata automaticamente |
| Calibrazione del centro | Scrive la posizione attuale del servo come centro 2048 (salvata in modo persistente nell'EEPROM) |
| Test del centro | Abilita la coppia e porta il servo al centro per verificare il risultato della calibrazione |
| Disattiva i motori | Disattiva con un clic la coppia su tutti i servo per facilitare la regolazione manuale |
| Scansione automatica | Rileva automaticamente tutti i servo online con ID da 1 a 20 |
| Controllo di un singolo servo | Un cursore controlla in tempo reale la posizione di un servo e l'attivazione/disattivazione della coppia |
| Debugger FT | Connessione seriale, scansione, lettura/scrittura dei parametri, controllo della posizione, cambio del baud rate, ripristino di fabbrica, backup dei parametri xdat |
| Parametri xdat | Salva i parametri EEPROM correnti del servo / apri un backup per ripristinarli |
| Calibrazione LeRobot | Genera file di calibrazione JSON in formato LeRobot |
| Esecuzione verso il centro da un file di calibrazione | Porta il braccio al centro in base a un file di calibrazione |

---

## 📚 Tutorial dettagliati

### Cinese

| OS | Tutorial |
|-|-|
| Windows | \[Tutorial Windows\](docs/zh/Windows教程.md) |
| Linux | \[Tutorial Linux\](docs/zh/Linux教程.md) |
| macOS | \[Tutorial macOS\](docs/zh/macOS教程.md) |

### Inglese

| OS | Guida |
|-|-|
| Windows | \[Guida Windows\](docs/en/Windows.md) |
| Linux | \[Guida Linux\](docs/en/Linux.md) |
| macOS | \[Guida macOS\](docs/en/macOS.md) |

---

## 🖥️ Panoramica dell'interfaccia

Il programma principale ha tre schede:

```Plain Text
┌─────────────────────────────────────────────────────────────┐
│  SoARM Series Calibration Tool  [Port1▾] [Port2▾] [🔄]  [🎮Remote][EN]│  ← Top bar
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────┬──────────────────────────────┐ │
│  │ Port1 - Servo Calib.    │ Port2 - Servo Calib.         │ │
│  │  [🔴Disconnected] Cur:… │  [🔴Disconnected] Cur:…      │ │
│  │  Servo1~6 status table  │  Servo1~6 status table       │ │
│  │  [CenterCal][CenterTest]│  [CenterCal][CenterTest]…    │ │
│  └─────────────────────────┴──────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

- **Barra superiore**: titolo dell'app, menu a tendina di selezione della porta, pulsante di aggiornamento, pulsante di controllo remoto, pulsante di cambio lingua.
- **🦾 Tab1 Servo Calibration**: azioni rapide per i pannelli sinistro e destro (calibrazione del centro, test del centro, disattivazione dei motori) più lo stato in tempo reale.
- **🎚️ Tab2 Single-Servo Control**: regola con precisione la posizione di ogni servo online con un cursore e attiva/disattiva la sua coppia.
- **🔬 Tab3 FT Debugger**: connessione seriale, scansione, lettura/scrittura dei parametri, controllo della posizione, baud rate/ripristino di fabbrica, backup e ripristino dei parametri xdat.

---

## 🚀 Avvio rapido

> Per i tutorial completi per ogni sistema, consulta \[📚 Tutorial dettagliati\](#-详细教程). Di seguito sono riportati i punti chiave per ciascun sistema.

### Windows

1. Installa [Python 3.10+](https://www.python.org/downloads/) (seleziona **Add to PATH**)
2. Crea un ambiente virtuale e installa le dipendenze:

```Bash
cd Juxi_ServoController
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

1. Controlla l'ambiente e avvia:

```Bash
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Conferma il numero di porta nel Gestore dispositivi (ad es. `COM3`) e selezionalo nella barra superiore. Per specificare le porte manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux (Ubuntu / Debian)

1. Installa i font CJK e le dipendenze:

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ Aggiungi i permessi della porta seriale (gruppo dialout)** [obbligatorio]:

```Bash
sudo usermod -a -G dialout $USER
# Ha effetto dopo il logout e il nuovo login
```

1. Crea un ambiente virtuale, installa le dipendenze e avvia:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. I dispositivi seriali sono `/dev/ttyUSB0` / `/dev/ttyACM0`. Per specificarli manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/ttyUSB0 --port2 /dev/ttyUSB1
```

### macOS

1. Installa `Python` con `Homebrew `:

```Bash
brew install python
```

1. Crea un ambiente virtuale, installa le dipendenze e avvia:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. **⚠️ Denominazione della porta seriale**: su macOS usa `/dev/cu.usbserial-*` (**consigliata, non bloccante**) invece di `/dev/tty.*`. Per elencarle:

```Bash
ls /dev/cu.*
```

Per specificare manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### Strumenti generali da riga di comando (senza GUI)

```Bash
# Scansiona i servo
python -m src.tools.scan_id

# Calibrazione rapida del centro dei servo
python -m src.tools.servo_quick_calibration

# Test del centro dei servo
python -m src.tools.servo_center_test

# Disattiva tutti i servo
python -m src.tools.servo_disable

# Calibrazione in stile LeRobot
python -m src.tools.lerobot_calibrate

# Controllo remoto sincronizzato a doppia porta
python -m src.tools.servo_remote_control
```

---

## 📖 Procedura d'uso

### 1. Connettere e rilevare i servo

1. Collega la scheda di controllo del braccio tramite un adattatore USB-seriale e alimenta i servo.
2. Apri la GUI e seleziona la porta nel menu a tendina della barra superiore (oppure fai clic su `🔄` per aggiornare).
3. In alto nel pannello compare `🟢 Connected` e vengono scansionati automaticamente i servo online con ID da 1 a 20 (di solito da 1 a 6).

> Se segnala che la porta è occupata, assicurati che nessun altro programma (un monitor seriale, uno strumento aperto in precedenza e non chiuso) la stia usando.

### 2. Calibrazione del centro (impostare la posizione attuale su 2048)

> Prima di calibrare, posiziona fisicamente il braccio in modo che ogni articolazione si trovi nella posizione "zero / centro" desiderata.

1. Fai clic sul pulsante **PortX Center Calibration** sul pannello.
2. Il programma disattiva prima i servo e ti invita a spostarli manualmente al centro desiderato.
3. Dopo la conferma, il programma esegue, per ogni servo: sblocco dell'EEPROM → scrittura del comando di calibrazione (valore 128 all'indirizzo 40) → nuovo blocco dell'EEPROM.
4. Dopo la calibrazione, usa "Center test" per verificare: il servo dovrebbe restare fermo (movimento minimo), il che significa che la calibrazione è riuscita.

### 3. Test del centro

1. Fai clic su **PortX Center Test**.
2. Il programma abilita la coppia e porta tutti i servo a 2048.
3. Se i servo si muovono appena rispetto alla loro posizione attuale, la calibrazione è corretta; se si muovono molto, il valore di calibrazione non è affidabile e va rifatto.

### 4. Disattivare i motori (regolazione manuale)

- Fai clic su **PortX Disable Motors** per disattivare la coppia di tutti i servo su quella porta, così possono essere ruotati liberamente a mano.
- Per un singolo servo, attiva/disattiva la sua coppia singolarmente nella pagina **Single-Servo Control** usando l'interruttore della coppia sotto il cursore.

### 5. Cambiare l'ID di un servo

1. Vai alla pagina **🔬 FT Debugger**, collega la porta seriale e scansiona i servo.
2. Seleziona il servo di destinazione, cambia il valore "Servo ID" (indirizzo 0x05) nella tabella dei parametri e fai clic su write.
3. Il programma esegue: sblocco → scrittura all'indirizzo 5 → verifica del nuovo ID → nuovo blocco.

> ⚠️ Prima di cambiare un ID, assicurati che sia l'unico servo sul bus per evitare conflitti di ID.

### 6. Cambiare il baud rate / ripristino di fabbrica

- **Cambiare il baud rate**: nell'area "Baud rate / factory reset" della pagina FT Debugger, seleziona il nuovo baud rate (38400 – 1000000 bps) e applicalo. Dopo la scrittura, il baud rate seriale viene commutato automaticamente e verificato con un ping; in caso di errore viene ripristinato automaticamente.
- **Ripristino di fabbrica**: il servo torna ai valori predefiniti di fabbrica (ID=1, baud rate=1000000); riscansiona successivamente.

### 7. Backup e ripristino dei parametri xdat

Nell'area "xdat parameters (EEPROM only)" della pagina FT Debugger:

1. **💾 Save current servo**: salva i parametri EEPROM del servo attualmente selezionato in un file xdat (backup).
2. Dopo aver modificato liberamente i parametri dei servo, se vuoi ripristinare:
3. **📂 Open xdat**: carica il file di backup.
4. **📤 Restore parameters to servo**: riscrivi il backup nell'EEPROM del servo corrente.

### 8. Controllo remoto sincronizzato a doppia porta

> ⚠️ **Direzione: la Porta 1 controlla la Porta 2**. La Porta 1 (leader) legge solo gli angoli dei servo; la Porta 2 (follower) viene controllata in sincronia.

1. Fai clic su **🎮 Remote** nella barra superiore (la Porta 1 legge gli angoli → la Porta 2 controlla in modo sincrono i servo con gli stessi ID).
2. Entrambe le porte devono avere ID dei servo corrispondenti; vengono sincronizzati solo i servo nell'intersezione.
3. Fai clic di nuovo sullo stesso pulsante per fermarti; in seguito i thread di scansione dei pannelli sinistro e destro riprendono automaticamente.

### 9. Calibrazione LeRobot (riga di comando)

```Bash
# Calibra il braccio follower (salvato in ~/.cache/huggingface/lerobot/calibration/robots/so_follower/)
python -m src.tools.lerobot_calibrate --arm-type follower

# Calibra il braccio leader
python -m src.tools.lerobot_calibrate --arm-type leader
```

Flusso: disattiva i servo → porta ogni articolazione al centro e registra `homing_offset` → percorri lentamente l'intera corsa e registra `range_min/max` (`wrist_roll` è un'articolazione a rotazione continua con un intervallo fisso di `[0,4095]`) → salva il JSON.

Esegui verso il centro usando un file di calibrazione:

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ Note



1. **La sicurezza prima di tutto**: la calibrazione del centro viene salvata in modo persistente nell'EEPROM. Prima di calibrare, assicurati che l'alimentazione sia stabile e che il braccio non entri in collisione con persone o oggetti.
2. **Alimentazione**: per lo SoARM 101 standard si consiglia 5V 5A DC; per la versione Pro, 12V 5A DC. Un'alimentazione insufficiente causa perdita di passi dei servo o errori di comunicazione.
3. **Esclusività della porta seriale**: su Windows la porta è bloccata in modo esclusivo, quindi la stessa porta non può essere usata contemporaneamente sia dal thread di scansione della GUI sia dal sottoprocesso di calibrazione. Lo strumento interrompe automaticamente il thread di scansione e termina il vecchio processo prima di operare; non fare clic ripetutamente a mano.
4. **Permessi seriali su Linux**: per accedere a `/dev/ttyUSB*` / `/dev/ttyACM*` è necessario aggiungere l'utente al gruppo `dialout` (vedi il \[tutorial Linux\](docs/zh/Linux教程.md)).
5. **Denominazione seriale su macOS**: usa `/dev/cu.*` (non bloccante) invece di `/dev/tty.*` (bloccante, potrebbe bloccarsi); vedi il \[tutorial macOS\](docs/zh/macOS教程.md).
6. **Hot-plug**: dopo aver scollegato l'USB il programma tenta di riconnettersi automaticamente; dopo averlo ricollegato, fai clic su `🔄` per aggiornare l'elenco delle porte.
7. **Protezione da sovratemperatura / sovratensione**: il programma monitora tensione e temperatura (allarme sopra i 60°C). Se i servo rimangono caldi, fermati e lasciali raffreddare.
8. **La calibrazione del centro è irreversibile**: dopo la scrittura, l'offset originale viene sovrascritto e non può essere annullato. Registra prima la posizione originale prima di calibrare.
9. **Rischio nel cambio di ID**: se la scrittura o la verifica fallisce, il programma segnala un errore e riprende la scansione, ma in casi estremi il servo può andare "perso". Se accade, prova il "Ripristino di fabbrica" (dopo il ripristino l'ID torna a 1).
10. **Problema di codifica**: se le emoji appaiono illeggibili nella console di Windows, imposta `PYTHONIOENCODING=utf-8` prima di eseguire gli strumenti da riga di comando. Linux/macOS con UTF-8 nativo di solito non hanno questo problema.

---

## 🛠️ Risoluzione dei problemi

| Sintomo | Causa possibile | Soluzione |
|-|-|-|
| Impossibile aprire la porta seriale / porta occupata | Un altro programma la sta usando | Chiudi programmi come i monitor seriali, oppure cambia porta e riavvia lo strumento |
| Nessun servo trovato nella scansione | Alimentazione insufficiente / cablaggio errato / baud rate non corrispondente | Controlla l'alimentazione e il cablaggio e conferma che i servo siano a 1M di baud rate |
| I servo si muovono in modo anomalo dopo la calibrazione del centro | La posa non è stata impostata correttamente prima della calibrazione | Ripeti "disattiva → posiziona manualmente → calibrazione del centro" |
| La temperatura sale troppo in fretta | Carico eccessivo o stallo | Controlla che il meccanismo non si blocchi; riduci velocità/accelerazione |
| Servo non trovato dopo averne cambiato l'ID | Conflitto di ID o scrittura fallita | Esegui il ripristino di fabbrica e riscansiona |
| Controllo remoto non sincronizzato | Le due porte hanno ID non corrispondenti | Conferma che i servo con lo stesso ID siano online sia sulla porta leader sia su quella follower |

---

## 📁 Struttura delle directory

```Plain Text
Juxi_ServoController/
├── docs/                    # Tutorial per sistema (cinese/inglese)
│   ├── zh/                  # Tutorial in cinese
│   │   ├── Windows教程.md
│   │   ├── Linux教程.md
│   │   └── macOS教程.md
│   └── en/                  # Tutorial in inglese
│       ├── Windows.md
│       ├── Linux.md
│       └── macOS.md
├── src/
│   ├── gui/                  # GUI PySide6
│   │   ├── factory_calibration_tool.py   # Strumento principale (calibrazione a doppia porta + controllo remoto + cambio lingua)
│   │   ├── ft_debugger.py                # Debugger FT (lettura/scrittura dei parametri / backup xdat)
│   │   ├── calibration_wizard.py         # Procedura guidata di calibrazione LeRobot
│   │   ├── theme_utils.py                # Tema chiaro
│   │   └── language_dialog.py            # Finestra di selezione della lingua
│   ├── tools/                # Strumenti da riga di comando
│   ├── xdat_utils.py         # Lettura/scrittura del file di parametri xdat
│   ├── i18n*.py / i18n_translations/     # Internazionalizzazione cinese/inglese
│   ├── port_utils.py         # Rilevamento della porta seriale
│   └── calibration_manager.py# Gestione dei file di calibrazione LeRobot
├── scservo_sdk/              # SDK di comunicazione dei servo FTServo
├── requirements.txt
└── setup.py                  # Script di verifica dell'ambiente
```
