[English](../en/ros2-simulation.md) | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | [Deutsch](../de/ros2-simulation.md) | [Español](../es/ros2-simulation.md) | [Français](../fr/ros2-simulation.md) | Italiano | [日本語](../ja/ros2-simulation.md) | [한국어](../ko/ros2-simulation.md) | [Português (BR)](../pt-br/ros2-simulation.md) | [Português (PT)](../pt-pt/ros2-simulation.md)

# Controllo della simulazione ROS2

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

Un workspace ROS 2 completo per il braccio robotico SO-ARM101 a 6 DOF, che copre la descrizione del robot, un driver hardware integrato, la simulazione Gazebo e la pianificazione del movimento con MoveIt 2.

Il SO-ARM101 è il braccio follower open source di seconda generazione co-progettato da [TheRobotStudio](https://www.therobotstudio.com/) e dalla community [LeRobot](https://huggingface.co/lerobot), che utilizza sei servo STS3215, una scheda driver dei servo e parti in PLA+ stampate in 3D.

<callout emoji="📌">
**Nota: il braccio richiede la calibrazione del centro; esegui la calibrazione del centro mentre tutte le articolazioni sono a metà della loro corsa**
</callout>

## Struttura dei pacchetti

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

Piattaforma di destinazione: **ROS 2 Humble / Jazzy**.

---

## Preparare l'ambiente ROS 2

Prima di compilare questo progetto, assicurati che ROS 2 e i componenti pertinenti siano installati sul tuo sistema.

### Requisiti di sistema

- Ubuntu 22.04 (consigliato) o 24.04
- Almeno 4 GB di RAM
- Per la modalità hardware reale è richiesta una porta seriale USB

### 0.1  Installare ROS 2 Humble

```Bash
# Imposta la locale
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# Aggiungi il repository software di ROS 2
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Installa ROS 2 Humble Desktop
sudo apt update
sudo apt install ros-humble-desktop
```

### 0.2  Installare strumenti di compilazione e dipendenze

```Bash
# strumento di compilazione colcon
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  Impostare le variabili d'ambiente

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  Impostare i permessi della porta seriale (necessario per l'hardware reale)

**Configurazione permanente (consigliata)**:

```Bash
sudo usermod -a -G dialout $USER
# Ha effetto dopo il logout e il nuovo login
```

**Configurazione temporanea (da rifare dopo ogni riavvio)**:

```Bash
sudo chmod 666 /dev/ttyACM0
```

## Installare il workspace

```Markdown
# Passo 1  Crea il workspace
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# Passo 2  Inserisci il codice sorgente
cp -r /path/to/SO-ARM101_ROS2 ./

# Passo 3  Installa le dipendenze di sistema
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# Passo 4  Compila tutti i pacchetti
colcon build --symlink-install

# Passo 5  Carica l'ambiente  ← esegui questo in ogni nuova terminale
source install/setup.bash
```

<callout emoji="💡">
**Nota sull'hardware reale** — il pacchetto `so_arm_hardware` è integrato. Non è necessario installare alcun driver aggiuntivo;  
comunica direttamente con i servo STS3215 attraverso la porta seriale usando il protocollo SCS.
</callout>

## Verifica visiva

Inizia da qui — è il percorso più semplice: nessun controller, nessun hardware.

```Bash
#  Terminale 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

RViz mostra il modello completo del robot; trascina i cursori per verificare che ogni articolazione si muova correttamente.

---

## Test dei controller (hardware virtuale / modalità Mock)

Nessun robot reale necessario — tutto gira in memoria.

```Bash
#  Terminale 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

Quando il log mostra quanto segue, è pronto:

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**Nota**: la modalità simulazione avvia solo due controller (`joint_state_broadcaster` e  
`joint_trajectory_controller`). `gripper_controller` è stato rimosso; il gripper  
viene controllato insieme a tutte le 6 articolazioni da `joint_trajectory_controller`.
</callout>

### Responsabilità dei controller

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## Pianificazione del movimento con MoveIt (hardware Mock)

**Serve una sola terminale** — MoveIt avvia internamente lo stack dei controller.

```Bash
#  Terminale 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

Quando la finestra di RViz si apre:

1. Nel pannello **MotionPlanning**, imposta **Planning Group → manipulator**
2. **Start State → `<current>`**, **Goal State → extended**
3. Fai clic su **Plan** e poi su **Execute**

Pose preimpostate disponibili: `open`, `zero`, `extended`, `rest`.

### 4.1  Panoramica dell'interfaccia MoveIt

Dopo l'avvio di RViz, il pannello **MotionPlanning** compare a sinistra con le seguenti schede principali:

#### Scheda Planning

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Parametri di pianificazione

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **Suggerimento per il primo test**: imposta Velocity e Acceleration su 0.3 per rallentare il movimento in sicurezza.

#### Scheda Scene Objects

- Aggiungi ostacoli (Box / Sphere / Cylinder) per il controllo delle collisioni
- Importa / esporta scene
- MoveIt pianifica automaticamente aggirando gli ostacoli

#### Scheda Stored States

- Salva le pose del braccio usate di frequente
- Pose predefinite: `open`, `zero`, `extended`, `rest`

### 4.2  Flusso di lavoro di base

#### Metodo A: trascinamento interattivo (consigliato)

1. Nella vista 3D, trova l'**interactive marker** all'estremità del braccio (frecce e anelli colorati)
2. Trascina le frecce per traslare la posizione dell'end-effector e trascina gli anelli per ruotare l'orientamento
3. Il sistema risolve automaticamente la cinematica inversa (IK) e aggiorna gli angoli delle articolazioni in tempo reale
4. Fai clic su **Plan** per visualizzare la traiettoria pianificata (arancione)
5. Quando sei soddisfatto, fai clic su **Execute** per eseguirla

> Se il trascinamento è a scatti, parti dalla posa preimpostata `rest` prima di trascinare.

#### Metodo B: pose preimpostate

1. Menu a tendina **Query Goal State** → seleziona `open` / `extended` / `rest`, ecc.
2. Fai clic su **Update**
3. Fai clic su **Plan**
4. Fai clic su **Execute**

#### Metodo C: impostare manualmente gli angoli delle articolazioni

1. **Query Goal State** → scheda **Joints**
2. Trascina il cursore di ogni articolazione per impostare l'angolo desiderato
3. Riferimento degli intervalli delle articolazioni:

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. Fai clic su **Update**
2. Fai clic su **Plan**
3. Fai clic su **Execute**

#### Metodo D: obiettivo casuale valido

Fai clic su **Random Valid** per generare una posa raggiungibile casuale, poi Plan → Execute.

### 4.3  Note di sicurezza

1. **Rallenta al primo utilizzo**: imposta Velocity / Acceleration su 0,1–0.3
2. **Arresto di emergenza**: premi Ctrl+C in qualsiasi momento per terminare il programma, oppure togli l'alimentazione
3. **Limiti delle articolazioni**: MoveIt non pianificherà oltre gli intervalli in `joint_limits.yaml`, ma assicurati che siano configurati correttamente
4. **Hardware reale**: assicurati che ci sia spazio sufficiente attorno al braccio prima di eseguire

### Panoramica della configurazione di MoveIt

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Simulazione Gazebo

La simulazione Gazebo richiede **4 terminali in esecuzione contemporaneamente**. Segui l'ordine scrupolosamente.

### 5.1  Avviare la simulazione Gazebo  (Terminale 1)

```Bash
#  Terminale 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Attendi che compaia la finestra di Gazebo; il robot resta brevemente sospeso in aria e poi atterra.

### 5.2  Caricare il controller della traiettoria  (Terminale 2)

Per impostazione predefinita Gazebo attiva solo `forward_position_controller`; devi passare manualmente a  
`joint_trajectory_controller`:

```Markdown
#  Terminale 2
source ~/so101_ws/install/setup.bash

# Passo A — disattiva forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# Passo B — carica e attiva joint_trajectory_controller con lo spawner
ros2 run controller_manager spawner joint_trajectory_controller

# Passo C — verifica
ros2 control list_controllers
```

Output previsto:

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ Non usare `ros2 control load_controller` per primo! Mette il controller nello  
stato `unconfigured`, il che impedisce allo spawner di attivarlo. Se lo hai già fatto,  
esegui prima `unload_controller` e ricomincia da capo.
</callout>

### 5.3  Avviare move_group  (Terminale 3)

```Bash
#  Terminale 3
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py use_sim_time:=True
```

### 5.4  Avviare RViz  (Terminale 4)

```Bash
#  Terminale 4
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

Quando RViz è pronto:

1. **Planning Group → manipulator**
2. **Goal State → open** (o `extended`, `rest`)
3. Fai clic su **Plan** e poi su **Execute**

Le articolazioni del braccio in Gazebo seguiranno il movimento.

<callout emoji="💡">
**Nota**: a causa della limitazione del guadagno PID nella versione Humble di `gz_ros2_control`,  
il gripper potrebbe non aprirsi fisicamente in Gazebo (il log di esecuzione riporta comunque successo).  
La modalità Mock e l'hardware reale non hanno questo problema.
</callout>

### 5.5  Modalità headless (senza GUI)

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  Risoluzione dei problemi: errori di caricamento ripetuti

Se lo spawner continua a segnalare `Failed to activate controller`, fai quanto segue per un reset completo:

```Bash
# 1. Scarica il controller bloccato
ros2 control unload_controller joint_trajectory_controller

# 2. Disattiva forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# 3. Esegui di nuovo lo spawn
ros2 run controller_manager spawner joint_trajectory_controller
```

## Hardware reale

Prerequisito: il braccio SO-ARM101 è assemblato e la scheda driver dei servo è collegata al PC via USB.

### 6.1  Avviare i controller (opzionale)

```Bash
#  Terminale 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

Il plugin `so_arm_hardware` automaticamente:

1. Apre la porta seriale
2. Scansiona i 6 ID dei servo (1–6)
3. Verifica che ogni servo risponda
4. Abilita la coppia e legge la posizione corrente

Quando i controller sono pronti, apri altre due terminali per avviare MoveIt:

```Bash
#  Terminale 2 — move_group
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py
```

```Bash
#  Terminale 3 — RViz
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

### 6.2  MoveIt (avvio con un solo comando)

> Il comando seguente **sostituisce** il punto 6.1 (non eseguire entrambi contemporaneamente; interrompi i comandi del punto 6.1) — `demo.launch.py` include già internamente lo stack dei controller.

```Bash
#  Terminale 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  Risoluzione dei problemi della porta seriale

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  La visualizzazione di RViz non corrisponde alla posa reale

Se la posa del braccio in RViz non corrisponde all'hardware reale (ad esempio un offset di un'articolazione o una falsa segnalazione di collisione):

1. Verifica che i servo siano stati calibrati al centro
2. Regola il `position_offset` di ciascuna articolazione in `so_arm101.ros2_control.xacro`
3. Formula di conversione: `new offset = current offset + (currently displayed rad / 0.00153398)`
4. Ricompila il pacchetto `so_arm101_description` dopo la modifica

---

## Domande frequenti

### D1: "package not found" in fase di compilazione

**R**: Assicurati che tutte le dipendenze di sistema siano installate correttamente e che l'ambiente ROS 2 sia stato caricato con source:

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### D2: "Permission denied" all'accesso alla porta seriale all'avvio

**R**: Controlla i permessi della porta seriale:

```Bash
# Correzione temporanea
sudo chmod 666 /dev/ttyACM0

# Correzione permanente (ha effetto dopo il logout)
sudo usermod -a -G dialout $USER
```

### D3: La pianificazione MoveIt fallisce con "Motion planning start tree could not be initialized"

**R**: Di solito ci sono due cause:

1. **Articolazioni fuori dai limiti** — controlla l'output di `FixStartStateBounds` nel log. La tolleranza attuale è  
0,3 rad; se lo sforamento rientra in quell'intervallo, passa. Altrimenti regola `start_state_max_bounds_error`  
o controlla gli offset dei servo.
2. **Stato iniziale in collisione** — controlla l'output di `FixStartStateCollision` nel log. Se  
compare "Unable to find a valid state nearby", la posa corrente è in autocollisione.  
Il braccio potrebbe trovarsi in una posa ripiegata (ad esempio il gripper che tocca la spalla), oppure gli offset sono errati.  
Regola `position_offset` e riprova.

### D4: Il braccio non si muove dopo Execute

**R**: Controlla gli stati dei controller:

```Bash
ros2 control list_controllers
```

Assicurati che `joint_trajectory_controller` sia `active`. In caso contrario, eseguilo di nuovo con lo spawn:

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### D5: RViz si avvia lentamente o si blocca

**R**: È normale. All'avvio MoveIt carica il modello URDF, i plugin di controllo delle collisioni,  
i risolutori di cinematica e così via; il primo avvio richiede circa 10 secondi.

### D6: Il percorso pianificato non è fluido o è a scatti

**R**: Prova quanto segue:

- Passa a un altro planner (scegli `RRTConnect` dal menu a tendina Planner in RViz)
- Aumenta il Planning Time a 10 secondi
- Assicurati che l'obiettivo sia all'interno del workspace (prova con `Random Valid`)

### D7: Il gripper non si muove in Gazebo

**R**: È una limitazione del guadagno PID codificata in modo fisso nella versione Humble di `gz_ros2_control`  
(fissata a 0.1) che non può essere sovrascritta tramite i parametri URDF. Execute riporta successo nel log,  
ma il gripper non si apre nella simulazione fisica di Gazebo. La modalità Mock e l'hardware reale non hanno questo problema.

## Appendice: riferimento rapido dei parametri di launch

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Struttura delle directory

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # Libreria di utility Python
├── so_arm101_description/          # URDF · controller · mesh · RViz · MuJoCo
├── so_arm101_moveit_config/        # File SRDF · planner · launch di MoveIt 2
├── so_arm_gz/                      # Launch della simulazione Gazebo
├── so_arm_hardware/                # Driver seriale SCS integrato (C++)
└── Simulation/                     # URDF CAD originale (conservato come riferimento)
```
