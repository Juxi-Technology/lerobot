[English](../en/so-arm101-tutorial.md) | [简体中文](../zh-hans/so-arm101-tutorial.md) | [繁體中文](../zh-hant/so-arm101-tutorial.md) | [Deutsch](../de/so-arm101-tutorial.md) | [Español](../es/so-arm101-tutorial.md) | [Français](../fr/so-arm101-tutorial.md) | Italiano | [日本語](../ja/so-arm101-tutorial.md) | [한국어](../ko/so-arm101-tutorial.md) | [Português (BR)](../pt-br/so-arm101-tutorial.md) | [Português (PT)](../pt-pt/so-arm101-tutorial.md)

<title>Tutorial del braccio robotico SO-ARM101</title>

# Panoramica del prodotto

Il SO-ARM101 è un **braccio robotico a 6 gradi di libertà a basso costo e completamente open source** realizzato dal team LeRobot di Hugging Face, pensato per l'avvio in ambito didattico, la validazione della ricerca e la prototipazione industriale leggera. Grazie all'elevata flessibilità e a un ecosistema open source completo, abbassa la barriera per l'applicazione dell'intelligenza embodied e della tecnologia robotica.

### 1. Progettazione hardware: prestazioni elevate, modulare, facile da assemblare e personalizzare

- **Materiale strutturale**: la struttura principale combina parti stampate in 3D con componenti portanti rinforzati, con instradamento dei cavi e progettazione delle articolazioni ottimizzati per evitare interferenze di movimento, bilanciando leggerezza e durata; gli utenti possono stampare da soli parti di ricambio o di estensione.
- **Configurazione di azionamento**: il braccio Follower monta **6 servo con encoder magnetico ad alta coppia da 12V 30KG**, combinati con feedback dell'encoder magnetico a 360° e un algoritmo di controllo PID — movimento fluido e senza vibrazioni, elevata precisione di posizionamento ripetuto, potenza elevata e movimento preciso.
- **Sistema di visione**: di serie con un **sistema di visione intelligente a doppia telecamera**; la telecamera sull'end-effector cattura i dettagli di presa a corto raggio, mentre la telecamera globale copre l'ambiente di lavoro. La fusione dei dati delle due telecamere costruisce un modello 3D e fornisce un ricco supporto dati per l'imitation learning.
- **Connessione di controllo**: dotato di una scheda driver dei servo che si collega direttamente a un PC o a un Raspberry Pi tramite un'interfaccia USB-C — plug and play, il che semplifica la procedura di connessione hardware e consente di costruire rapidamente l'ambiente di controllo.

### 2. Ecosistema software: integrazione profonda con LeRobot, sviluppo AI senza barriere

- **Compatibilità con il framework principale**: profondamente adattato al **framework di machine learning per robot open source LeRobot** di Hugging Face, basato su PyTorch, con modelli preaddestrati integrati, dataset multi-scenario e un ambiente di simulazione, e compatibile con dataset open source noti come Stanford ALOHA.
- **Comunicazione a bassa latenza**: utilizza il **motore di dataflow distribuito DORA** per un'interazione a bassa latenza tra hardware e algoritmi; Python è 17 volte più veloce di ROS2, ed è supportato l'hot reload del codice, così puoi regolare le policy in tempo reale senza riavviare.
- **Open source full-stack**: i file di stampa 3D dell'hardware, il codice di controllo software, gli script di addestramento AI e l'intero set di tutorial sono **completamente open source**; gli utenti possono modificarli e svilupparli ulteriormente liberamente per implementare rapidamente estensioni personalizzate.

### 3. Scenari applicativi principali: soluzioni per ogni contesto, dall'avvio al deployment

1. **Avvio alla robotica didattica**: fornisce un tutorial end-to-end dall'assemblaggio del braccio e dalla programmazione di base fino al deployment delle policy AI, con un'interfaccia di utilizzo visuale e codice di esempio, così i principianti possono padroneggiare rapidamente il controllo del robot e le competenze di applicazione dell'AI.
2. **Validazione di algoritmi di ricerca**: incentrato sulla ricerca su **imitation learning e reinforcement learning**, con supporto per la registrazione dei dati di operazione umana tramite VR per addestrare il robot; un caso tipico: basandosi su 50 clip di video operativo da 15 secondi, 2 ore di addestramento bastano per padroneggiare compiti come piegare i vestiti, inserire una chiave e smistare materiali.
3. **Prototipazione industriale leggera**: validazione a basso costo di soluzioni di automazione, adatta a scenari come **movimentazione dei materiali, assemblaggio di precisione e smistamento dei componenti**, offrendo le funzioni principali di un braccio robotico di livello industriale a un costo nella fascia dei mille yuan per una rapida validazione dei prototipi.

### 4. Vantaggi del prodotto

- **Rapporto qualità-prezzo eccezionale**: la versione base parte da circa 100 $, e il design open source abbassa i costi di acquisto e di sviluppo secondario, rendendolo adatto al deployment in lotti da parte di privati, laboratori e piccole e medie imprese.
- **Open source su tutta la filiera**: hardware, software e tutorial sono tutti completamente aperti e senza barriere tecniche, supportando personalizzazione ed estensione delle funzionalità libere per adattarsi rapidamente a molti scenari.
- **Amichevole per lo sviluppo AI**: supportato dall'ecosistema LeRobot, richiama modelli preaddestrati e dataset con un clic, semplificando l'intero flusso dalla raccolta dati e l'addestramento delle policy al deployment, e accelerando l'introduzione degli algoritmi di intelligenza embodied.

### 5. Specifiche del prodotto

| **Specifica** | **Dettagli** |
|-|-|
| Gradi di libertà | 6 assi (pan/tilt della spalla, flessione del gomito, flessione/rotazione del polso, apertura/chiusura del gripper) |
| Materiale strutturale | Parti stampate in 3D (PLA+) |
| Motori di azionamento | 12 \* motori servo Feetech STS3215 (alimentazione 12V)  <br/>Rapporto di riduzione braccio Follower STS3215-C018: 1/345  <br/>Rapporto di riduzione braccio Leader STS3215-C001: 1/345 (spalla), STS3215-C044 1/191 (gomito), STS3215-C046 1/147 (polso) |
| Capacità di carico | Carico massimo sull'end-effector 200g (gripper chiuso) |
| Precisione di posizionamento ripetuto | ±1,5mm (influenzata dalla calibrazione e dal gioco del motore) |
| Raggio di lavoro | Portata massima dell'end-effector 350mm |
| Requisiti di alimentazione | Leader: alimentatore 5V 6A; Follower: alimentatore 12V 5A (per esigenze di coppia elevata) |
| Interfaccia di comunicazione | Collegamento diretto USB-C al PC (trasferimento dei comandi di controllo) |
| Sistema di visione | Telecamera (1080P@30FPS, FOV86° non distorta, oppure 1080P@60FPS FOV100° a fuoco fisso) |
| Tipo di gripper | Gripper in PLA+, gripper in TPU, gripper parallelo a due dita supportato, apertura 0-50mm, forza di presa massima 5N |
| Framework di controllo | Libreria LeRobot basata su Python, che fornisce un'API di controllo dei motori (lerobot.control) |
| Modelli preaddestrati | Supporta algoritmi di imitation learning come ACT (Action Chunking Transformer) e Diffusion Policy |
| Modello leggero | Modello vision-language-action SmolVLA (450M parametri): ・Inferenza CPU in tempo reale (gira su MacBook) ・Risposta asincrona più veloce del 30% ・Solo 64 visual token per fotogramma ・Visualizzazione dello stato: monitoraggio in tempo reale con la libreria rerun |
| Peso complessivo | ≈1,2kg (motori e cavi inclusi) |
| Dimensioni assemblate | Diametro della base 120mm, altezza (completamente esteso) 650mm |
| Temperatura di esercizio | 0℃–40℃ (limite dei motori servo) |
| Livello di rumorosità | <45dB (funzionamento a vuoto) |
| Tutorial per principianti | Sì |
| GITHUB ufficiale | Sì |

![L'immagine mostra i diagrammi dimensionali dei bracci Leader e Follower del braccio robotico SO-ARM101, insieme al nome del prodotto, al materiale, alle dimensioni e ad altre informazioni. I diagrammi dimensionali etichettano le dimensioni di ogni parte, ad esempio il braccio Leader è lungo 525mm e il braccio Follower è lungo 532mm. Il materiale del prodotto è PLA+ con ottimizzazione topologica e le dimensioni del prodotto sono 111x239x525mm (Leader) e 111x173x532mm (Follower). Questa immagine corrisponde alla sezione Specifiche del prodotto del documento e presenta visivamente le specifiche dimensionali del braccio.](../en/images/d01-01.png)

| **Voce / nome del pacchetto** | **Funzione / descrizione** |
|-|-|
| Libreria LeRobot | Versione: ≥0.1.0 Framework di controllo principale: • API Python (lerobot.control) ・Pianificazione del movimento in tempo reale ・Elaborazione dello stream di dati dei sensori |
| PyTorch | Versione: ≥2.0 Motore di inferenza per deep learning (supporta modelli come SmolVLA) |
| Transformers | Versione: ≥4.40.0 Libreria di modelli Hugging Face (carica ACT/Diffusion Policy preaddestrati) |
| rerun | Versione: ≥0.16.0 Strumento di visualizzazione in tempo reale dello stato del robot (rendering 3D degli angoli delle articolazioni / della traiettoria) |
| ROS 2 | Versione: Humble/Foxy Opzionale: interfaccia driver ROS2 (pacchetto soarm100_ros) |
| ACT | Action Chunking Transformer, previsione di azioni a sequenza lunga (es. compiti di presa continua) |
| Diffusion Policy | Policy di diffusione, controllo robusto in spazi di azione ad alta dimensionalità (manipolazione resistente ai disturbi) |
| SmolVLA | Modello vision-language-action, esecuzione di istruzioni multimodali (es. "afferra il blocco rosso") ・450M parametri, funziona su CPU/GPU |

| **Categoria di funzione** | **Descrizione della funzione** |
|-|-|
| Controllo a livello di articolazione | ・Controllo indipendente di angolo/velocità sui 6 assi (intervallo ±180°) ・Protezione con limiti software delle articolazioni ・Feedback in tempo reale di temperatura/tensione del motore |
| Controllo nello spazio cartesiano | ・Posizionamento dell'end-effector tramite coordinate XYZ (precisione ±1,5mm) ・Regolazione dell'orientamento tramite angoli di Eulero (Roll/Pitch/Yaw) |
| Azionamento del gripper | ・Regolazione continua dell'apertura da 0 a 50mm ・Regolazione dinamica della forza di presa (0,1-5N) ・Presa adattiva allo spessore dell'oggetto |
| Modalità Leader/Follower | ・Insegnamento manuale con il braccio Leader → imitazione in tempo reale con il braccio Follower ・Registrazione/riproduzione dei dati di azione |

| **Categoria di funzione** | **Descrizione della funzione** |
|-|-|
| Imitation learning | ・Registrazione dei dati di dimostrazione umana → addestramento dei modelli ACT/Diffusion Policy ・Supporto al trasferimento di policy multi-compito (es. impilare blocchi → smistare oggetti) |
| Interazione multimodale | ・Il modello SmolVLA interpreta istruzioni in linguaggio naturale (es. "afferra il blocco blu") ・Esecuzione end-to-end visione-azione |
| Interfaccia di reinforcement learning | ・Ambiente compatibile con Gymnasium ・Funzioni di ricompensa personalizzate (es. tempo di completamento del compito / ottimizzazione dell'energia) |
| Sistema di calibrazione | ・Calibrazione dello zero Leader/Follower ・Calibrazione occhio-mano telecamera-braccio ・Compensazione automatica della coppia delle articolazioni |
| Gestione degli stream di dati | ・Registrazione/riproduzione di dataset in formato .h5 ・Sincronizzazione cloud con Hugging Face Hub ・Allineamento dei timestamp dei dati dei sensori |
| Monitoraggio in tempo reale | ・Visualizzazione con rerun degli angoli delle articolazioni / della traiettoria dell'end-effector ・Allarmi di anomalia dei motori (surriscaldamento / stallo) ・Diagnostica della latenza di comunicazione |
| Integrazione con ROS 2 | ・Pubblicazione dello stato delle articolazioni (/joint_states) ・Sottoscrizione dei comandi di controllo (/arm_controller) ・Trasferimento dello stream di point cloud (/depth_points) |
| Deployment multipiattaforma | • Linux/Windows/macOS (API Python) ・Containerizzazione Docker ・Controllo remoto web (interfaccia FastAPI) |
