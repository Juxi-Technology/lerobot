[English](../en/ros2-simulation.md) | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | Deutsch | [Español](../es/ros2-simulation.md) | [Français](../fr/ros2-simulation.md) | [Italiano](../it/ros2-simulation.md) | [日本語](../ja/ros2-simulation.md) | [한국어](../ko/ros2-simulation.md) | [Português (BR)](../pt-br/ros2-simulation.md) | [Português (PT)](../pt-pt/ros2-simulation.md)

# ROS2-Simulationssteuerung

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

Ein vollständiger ROS-2-Workspace für den 6-DOF-Roboterarm SO-ARM101, bestehend aus Roboterbeschreibung, integriertem Hardware-Treiber, Gazebo-Simulation und MoveIt-2-Bewegungsplanung.

Der SO-ARM101 ist der quelloffene Follower-Arm der zweiten Generation, der gemeinsam von [TheRobotStudio](https://www.therobotstudio.com/) und der [LeRobot](https://huggingface.co/lerobot)-Community entwickelt wurde und sechs STS3215-Servos, ein Servo-Treiberboard und 3D-gedruckte PLA+-Teile verwendet.

<callout emoji="📌">
**Hinweis: Der Arm muss mittig kalibriert werden; führen Sie die Mittelpunkt-Kalibrierung durch, während sich alle Gelenke in der Mitte ihres Bewegungsbereichs befinden**
</callout>

## Paketstruktur

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

Zielplattform: **ROS 2 Humble / Jazzy**.

---

## Die ROS-2-Umgebung vorbereiten

Vergewissern Sie sich vor dem Bauen dieses Projekts, dass ROS 2 und die relevanten Komponenten auf Ihrem System installiert sind.

### Systemanforderungen

- Ubuntu 22.04 (empfohlen) oder 24.04
- Mindestens 4 GB RAM
- Für den Real-Hardware-Modus ist eine USB-Seriellschnittstelle erforderlich

### 0.1  ROS 2 Humble installieren

```Bash
# Locale festlegen
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# Das ROS-2-Software-Repository hinzufügen
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# ROS 2 Humble Desktop installieren
sudo apt update
sudo apt install ros-humble-desktop
```

### 0.2  Build-Tools und Abhängigkeiten installieren

```Bash
# colcon-Build-Tool
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  Umgebungsvariablen setzen

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  Berechtigungen für die serielle Schnittstelle setzen (für echte Hardware erforderlich)

**Dauerhafte Einrichtung (empfohlen)**:

```Bash
sudo usermod -a -G dialout $USER
# Wird nach Ab- und erneutem Anmelden wirksam
```

**Temporäre Einrichtung (muss nach jedem Neustart erneut durchgeführt werden)**:

```Bash
sudo chmod 666 /dev/ttyACM0
```

## Den Workspace installieren

```Markdown
# Schritt 1  Den Workspace erstellen
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# Schritt 2  Quellcode ablegen
cp -r /path/to/SO-ARM101_ROS2 ./

# Schritt 3  Systemabhängigkeiten installieren
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# Schritt 4  Alle Pakete bauen
colcon build --symlink-install

# Schritt 5  Umgebung laden  ← in jedem neuen Terminal ausführen
source install/setup.bash
```

<callout emoji="💡">
**Hinweis zur echten Hardware** – Das Paket `so_arm_hardware` ist bereits integriert. Es muss kein zusätzlicher Treiber installiert werden;  
es kommuniziert direkt über die serielle Schnittstelle mit den STS3215-Servos unter Verwendung des SCS-Protokolls.
</callout>

## Visuelle Überprüfung

Beginnen Sie hier – das ist der einfachste Weg: keine Controller, keine Hardware.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

RViz zeigt das vollständige Robotermodell; ziehen Sie die Schieberegler, um zu prüfen, ob sich jedes Gelenk korrekt bewegt.

---

## Controller-Test (virtuelle Hardware / Mock-Modus)

Auch hier ist kein echter Roboter nötig – alles läuft im Speicher.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

Wenn im Log Folgendes erscheint, ist es bereit:

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**Hinweis**: Der Simulationsmodus startet nur zwei Controller (`joint_state_broadcaster` und  
`joint_trajectory_controller`). `gripper_controller` wurde entfernt; der Greifer  
wird zusammen mit allen 6 Gelenken von `joint_trajectory_controller` gesteuert.
</callout>

### Zuständigkeiten der Controller

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## MoveIt-Bewegungsplanung (Mock-Hardware)

**Nur ein Terminal erforderlich** – MoveIt startet den Controller-Stack intern.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

Sobald sich das RViz-Fenster öffnet:

1. Stellen Sie im Panel **MotionPlanning** **Planning Group → manipulator** ein
2. **Start State → `<current>`**, **Goal State → extended**
3. Klicken Sie auf **Plan** und dann auf **Execute**

Verfügbare voreingestellte Posen: `open`, `zero`, `extended`, `rest`.

### 4.1  Rundgang durch die MoveIt-Oberfläche

Nach dem Start von RViz erscheint das Panel **MotionPlanning** links mit folgenden Haupt-Tabs:

#### Tab Planning

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Planungsparameter

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **Tipp für den ersten Test**: Stellen Sie Velocity und Acceleration auf 0.3, um die Bewegung sicherheitshalber zu verlangsamen.

#### Tab Scene Objects

- Hindernisse hinzufügen (Box / Sphere / Cylinder) für die Kollisionsprüfung
- Szenen importieren / exportieren
- MoveIt plant Hindernisse automatisch zu umgehen

#### Tab Stored States

- Häufig verwendete Armposen speichern
- Standardposen: `open`, `zero`, `extended`, `rest`

### 4.2  Grundlegender Arbeitsablauf

#### Methode A: Interaktives Ziehen (empfohlen)

1. Suchen Sie in der 3D-Ansicht den **interaktiven Marker** am Ende des Arms (farbige Pfeile und Ringe)
2. Ziehen Sie die Pfeile, um die Endeffektorposition zu verschieben, und die Ringe, um die Ausrichtung zu drehen
3. Das System löst die IK automatisch und aktualisiert die Gelenkwinkel in Echtzeit
4. Klicken Sie auf **Plan**, um die geplante Trajektorie anzuzeigen (orange)
5. Klicken Sie, wenn Sie zufrieden sind, auf **Execute**, um sie auszuführen

> Wenn das Ziehen stockt, beginnen Sie vor dem Ziehen mit der voreingestellten Pose `rest`.

#### Methode B: Voreingestellte Posen

1. Dropdown **Query Goal State** → `open` / `extended` / `rest` usw. auswählen
2. Klicken Sie auf **Update**
3. Klicken Sie auf **Plan**
4. Klicken Sie auf **Execute**

#### Methode C: Gelenkwinkel manuell einstellen

1. **Query Goal State** → Tab **Joints**
2. Ziehen Sie jeden Gelenk-Schieberegler, um den Zielwinkel einzustellen
3. Referenz für die Gelenkbereiche:

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. Klicken Sie auf **Update**
2. Klicken Sie auf **Plan**
3. Klicken Sie auf **Execute**

#### Methode D: Zufälliges gültiges Ziel

Klicken Sie auf **Random Valid**, um eine zufällige erreichbare Pose zu erzeugen, dann Plan → Execute.

### 4.3  Sicherheitshinweise

1. **Beim ersten Einsatz langsamer**: Stellen Sie Velocity / Acceleration auf 0.1–0.3
2. **Not-Aus**: Drücken Sie jederzeit Ctrl+C, um das Programm zu beenden, oder unterbrechen Sie die Stromversorgung
3. **Gelenkgrenzen**: MoveIt plant nicht über die Bereiche in `joint_limits.yaml` hinaus, aber stellen Sie sicher, dass diese korrekt konfiguriert sind
4. **Echte Hardware**: Stellen Sie vor dem Ausführen sicher, dass um den Arm herum genügend Platz ist

### Überblick über die MoveIt-Konfiguration

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Gazebo-Simulation

Die Gazebo-Simulation erfordert **4 gleichzeitig laufende Terminals**. Befolgen Sie die Reihenfolge strikt.

### 5.1  Gazebo-Simulation starten  (Terminal 1)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Warten Sie, bis das Gazebo-Fenster erscheint; der Roboter hängt kurz in der Luft und landet dann.

### 5.2  Den Trajektorien-Controller laden  (Terminal 2)

Standardmäßig aktiviert Gazebo nur `forward_position_controller`; Sie müssen manuell zu  
`joint_trajectory_controller` wechseln:

```Markdown
#  Terminal 2
source ~/so101_ws/install/setup.bash

# Schritt A – forward_position_controller ausschalten
ros2 control set_controller_state forward_position_controller inactive

# Schritt B – joint_trajectory_controller mit dem Spawner laden und aktivieren
ros2 run controller_manager spawner joint_trajectory_controller

# Schritt C – überprüfen
ros2 control list_controllers
```

Erwartete Ausgabe:

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ Verwenden Sie nicht zuerst `ros2 control load_controller`! Dadurch gerät der Controller in den  
Zustand `unconfigured`, was den Spawner daran hindert, ihn zu aktivieren. Wenn Sie es bereits getan haben,  
führen Sie zuerst `unload_controller` aus und beginnen Sie von vorn.
</callout>

### 5.3  move_group starten  (Terminal 3)

```Bash
#  Terminal 3
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py use_sim_time:=True
```

### 5.4  RViz starten  (Terminal 4)

```Bash
#  Terminal 4
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

Sobald RViz bereit ist:

1. **Planning Group → manipulator**
2. **Goal State → open** (oder `extended`, `rest`)
3. Klicken Sie auf **Plan** und dann auf **Execute**

Die Arm­gelenke in Gazebo folgen der Bewegung.

<callout emoji="💡">
**Hinweis**: Aufgrund der PID-Verstärkungsbeschränkung in der Humble-Version von `gz_ros2_control`  
öffnet sich der Greifer in Gazebo möglicherweise nicht physisch (das Ausführungsprotokoll meldet dennoch Erfolg).  
Der Mock-Modus und echte Hardware haben dieses Problem nicht.
</callout>

### 5.5  Headless-Modus (ohne GUI)

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  Fehlerbehebung: wiederholte Ladefehler

Wenn der Spawner weiterhin `Failed to activate controller` meldet, führen Sie Folgendes aus, um vollständig zurückzusetzen:

```Bash
# 1. Den hängengebliebenen Controller entladen
ros2 control unload_controller joint_trajectory_controller

# 2. forward_position_controller ausschalten
ros2 control set_controller_state forward_position_controller inactive

# 3. Erneut spawnen
ros2 run controller_manager spawner joint_trajectory_controller
```

## Echte Hardware

Voraussetzung: Der Arm SO-ARM101 ist montiert und das Servo-Treiberboard ist über USB mit dem PC verbunden.

### 6.1  Die Controller starten (optional)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

Das Plugin `so_arm_hardware` führt automatisch Folgendes aus:

1. Öffnet die serielle Schnittstelle
2. Scannt die 6 Servo-IDs (1–6)
3. Überprüft, ob jedes Servo antwortet
4. Aktiviert das Drehmoment und liest die aktuelle Position

Sobald die Controller bereit sind, öffnen Sie zwei weitere Terminals, um MoveIt zu starten:

```Bash
#  Terminal 2 – move_group
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py
```

```Bash
#  Terminal 3 – RViz
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

### 6.2  MoveIt (Start mit einem Befehl)

> Der folgende Befehl **ersetzt** 6.1 (führen Sie nicht beide gleichzeitig aus; stoppen Sie die Befehle aus 6.1) – `demo.launch.py` enthält den Controller-Stack bereits intern.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  Fehlerbehebung bei der seriellen Schnittstelle

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  Die RViz-Anzeige stimmt nicht mit der tatsächlichen Pose überein

Wenn die Armpose in RViz nicht zur echten Hardware passt (zum Beispiel ein Gelenk-Offset oder eine falsche Kollisionsmeldung):

1. Vergewissern Sie sich, dass die Servos mittig kalibriert wurden
2. Passen Sie den `position_offset` jedes Gelenks in `so_arm101.ros2_control.xacro` an
3. Umrechnungsformel: `new offset = current offset + (aktuell angezeigter rad / 0.00153398)`
4. Bauen Sie das Paket `so_arm101_description` nach der Änderung neu

---

## FAQ

### Frage 1: „package not found“ beim Bauen

**A**: Stellen Sie sicher, dass alle Systemabhängigkeiten korrekt installiert und die ROS-2-Umgebung eingebunden ist:

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### Frage 2: „Permission denied“ beim Zugriff auf die serielle Schnittstelle beim Start

**A**: Prüfen Sie die Berechtigungen der seriellen Schnittstelle:

```Bash
# Vorübergehende Lösung
sudo chmod 666 /dev/ttyACM0

# Dauerhafte Lösung (wirkt nach dem Abmelden)
sudo usermod -a -G dialout $USER
```

### Frage 3: Die MoveIt-Planung schlägt mit „Motion planning start tree could not be initialized“ fehl

**A**: Es gibt meist zwei Ursachen:

1. **Gelenke außerhalb der Grenzen** – Prüfen Sie die Ausgabe von `FixStartStateBounds` im Log. Die aktuelle Toleranz beträgt  
0.3 rad; wenn die Überschreitung innerhalb dieses Bereichs liegt, wird sie akzeptiert. Andernfalls passen Sie `start_state_max_bounds_error`  
an oder prüfen Sie die Servo-Offsets.
2. **Startzustand in Kollision** – Prüfen Sie die Ausgabe von `FixStartStateCollision` im Log. Wenn  
„Unable to find a valid state nearby“ erscheint, kollidiert die aktuelle Pose mit sich selbst.  
Der Arm befindet sich möglicherweise in einer gefalteten Pose (zum Beispiel berührt der Greifer die Schulter) oder die Offsets sind falsch.  
Passen Sie `position_offset` an und versuchen Sie es erneut.

### Frage 4: Der Arm bewegt sich nach Execute nicht

**A**: Prüfen Sie die Controller-Zustände:

```Bash
ros2 control list_controllers
```

Stellen Sie sicher, dass `joint_trajectory_controller` `active` ist. Wenn nicht, spawnen Sie ihn erneut:

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### Frage 5: RViz startet langsam oder hängt

**A**: Das ist normal. Beim Start lädt MoveIt das URDF-Modell, Kollisionsprüfungs-Plugins,  
Kinematik-Löser und so weiter; der erste Start dauert etwa 10 Sekunden.

### Frage 6: Der geplante Pfad ist nicht glatt oder ruckelt

**A**: Versuchen Sie Folgendes:

- Wechseln Sie zu einem anderen Planer (wählen Sie `RRTConnect` aus dem Planner-Dropdown in RViz)
- Erhöhen Sie die Planning Time auf 10 Sekunden
- Stellen Sie sicher, dass das Ziel innerhalb des Arbeitsraums liegt (testen Sie mit `Random Valid`)

### Frage 7: Der Greifer bewegt sich in Gazebo nicht

**A**: Dies ist eine fest codierte PID-Verstärkungsbeschränkung in der Humble-Version von `gz_ros2_control`  
(fest auf 0.1), die nicht über URDF-Parameter überschrieben werden kann. Execute meldet im Log Erfolg,  
doch der Greifer öffnet sich in der Physiksimulation von Gazebo nicht. Der Mock-Modus und echte Hardware haben dieses Problem nicht.

## Anhang: Kurzreferenz der Launch-Parameter

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Verzeichnisstruktur

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # Python-Hilfsbibliothek
├── so_arm101_description/          # URDF · Controller · Meshes · RViz · MuJoCo
├── so_arm101_moveit_config/        # MoveIt 2 SRDF · Planer · Launch-Dateien
├── so_arm_gz/                      # Gazebo-Simulations-Launch
├── so_arm_hardware/                # Integrierter SCS-Serieltreiber (C++)
└── Simulation/                     # Originales CAD-URDF (als Referenz beibehalten)
```
