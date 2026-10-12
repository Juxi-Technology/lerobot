[English](../en/ros2-simulation.md) | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | [Deutsch](../de/ros2-simulation.md) | [Español](../es/ros2-simulation.md) | Français | [Italiano](../it/ros2-simulation.md) | [日本語](../ja/ros2-simulation.md) | [한국어](../ko/ros2-simulation.md) | [Português (BR)](../pt-br/ros2-simulation.md) | [Português (PT)](../pt-pt/ros2-simulation.md)

# Contrôle en simulation ROS2

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

Un espace de travail ROS 2 complet pour le bras robotique 6 DDL SO-ARM101, couvrant la description du robot, un pilote matériel intégré, la simulation Gazebo et la planification de mouvement MoveIt 2.

Le SO-ARM101 est le bras Follower open source de deuxième génération co-conçu par [TheRobotStudio](https://www.therobotstudio.com/) et la communauté [LeRobot](https://huggingface.co/lerobot), utilisant six servomoteurs STS3215, une carte de pilotage de servomoteurs et des pièces en PLA+ imprimées en 3D.

<callout emoji="📌">
**Remarque : le bras nécessite un étalonnage du centre ; effectuez l'étalonnage du centre lorsque toutes les articulations sont au milieu de leur plage de mouvement**
</callout>

## Structure des packages

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

Plateforme cible : **ROS 2 Humble / Jazzy**.

---

## Préparation de l'environnement ROS 2

Avant de compiler ce projet, assurez-vous que ROS 2 et les composants pertinents sont installés sur votre système.

### Configuration requise

- Ubuntu 22.04 (recommandé) ou 24.04
- Au moins 4 Go de RAM
- Un port série USB est nécessaire pour le mode matériel réel

### 0.1  Installer ROS 2 Humble

```Bash
# Configurer la locale
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# Ajouter le dépôt logiciel ROS 2
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Installer ROS 2 Humble Desktop
sudo apt update
sudo apt install ros-humble-desktop
```

### 0.2  Installer les outils de compilation et les dépendances

```Bash
# outil de build colcon
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  Définir les variables d'environnement

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  Définir les permissions du port série (nécessaire pour le matériel réel)

**Configuration permanente (recommandée)** :

```Bash
sudo usermod -a -G dialout $USER
# Prend effet après déconnexion puis reconnexion
```

**Configuration temporaire (à refaire après chaque redémarrage)** :

```Bash
sudo chmod 666 /dev/ttyACM0
```

## Installation de l'espace de travail

```Markdown
# Étape 1  Créer le workspace
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# Étape 2  Placer le code source
cp -r /path/to/SO-ARM101_ROS2 ./

# Étape 3  Installer les dépendances système
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# Étape 4  Compiler tous les packages
colcon build --symlink-install

# Étape 5  Charger l'environnement  ← à exécuter dans chaque nouveau terminal
source install/setup.bash
```

<callout emoji="💡">
**Remarque matériel réel** — le package `so_arm_hardware` est intégré. Aucun pilote supplémentaire n'a besoin d'être installé ;  
il dialogue directement avec les servomoteurs STS3215 via le port série à l'aide du protocole SCS.
</callout>

## Vérification visuelle

Commencez ici — c'est le chemin le plus simple : aucun contrôleur, aucun matériel.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

RViz affiche le modèle complet du robot ; faites glisser les curseurs pour vérifier que chaque articulation bouge correctement.

---

## Test des contrôleurs (matériel virtuel / mode Mock)

Toujours sans robot réel — tout s'exécute en mémoire.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

Lorsque le journal affiche ce qui suit, c'est prêt :

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**Remarque** : le mode simulation ne démarre que deux contrôleurs (`joint_state_broadcaster` et  
`joint_trajectory_controller`). `gripper_controller` a été supprimé ; la pince  
est contrôlée avec les 6 autres articulations par `joint_trajectory_controller`.
</callout>

### Responsabilités des contrôleurs

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## Planification de mouvement MoveIt (matériel Mock)

**Un seul terminal nécessaire** — MoveIt démarre la pile de contrôleurs en interne.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

Une fois la fenêtre RViz ouverte :

1. Dans le panneau **MotionPlanning**, réglez **Planning Group → manipulator**
2. **Start State → `<current>`**, **Goal State → extended**
3. Cliquez sur **Plan** puis sur **Execute**

Poses prédéfinies disponibles : `open`, `zero`, `extended`, `rest`.

### 4.1  Prise en main de l'interface MoveIt

Après le démarrage de RViz, le panneau **MotionPlanning** apparaît à gauche avec les principaux onglets suivants :

#### Onglet Planning

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Paramètres de planification

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **Conseil pour le premier essai** : réglez Velocity et Acceleration à 0.3 pour ralentir le mouvement par sécurité.

#### Onglet Scene Objects

- Ajoutez des obstacles (Box / Sphere / Cylinder) pour la vérification des collisions
- Importez / exportez des scènes
- MoveIt planifie automatiquement en contournant les obstacles

#### Onglet Stored States

- Enregistrez les poses de bras fréquemment utilisées
- Poses par défaut : `open`, `zero`, `extended`, `rest`

### 4.2  Flux de travail de base

#### Méthode A : glisser-déposer interactif (recommandée)

1. Dans la vue 3D, repérez le **marqueur interactif** à l'extrémité du bras (flèches et anneaux colorés)
2. Faites glisser les flèches pour translater la position de l'effecteur, et les anneaux pour faire tourner l'orientation
3. Le système résout automatiquement la cinématique inverse et met à jour les angles d'articulation en temps réel
4. Cliquez sur **Plan** pour visualiser la trajectoire planifiée (orange)
5. Une fois satisfait, cliquez sur **Execute** pour l'exécuter

> Si le glisser-déposer saccade, partez de la pose prédéfinie `rest` avant de faire glisser.

#### Méthode B : poses prédéfinies

1. Liste déroulante **Query Goal State** → sélectionnez `open` / `extended` / `rest`, etc.
2. Cliquez sur **Update**
3. Cliquez sur **Plan**
4. Cliquez sur **Execute**

#### Méthode C : définir les angles d'articulation manuellement

1. **Query Goal State** → onglet **Joints**
2. Faites glisser chaque curseur d'articulation pour définir l'angle cible
3. Référence des plages d'articulation :

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. Cliquez sur **Update**
2. Cliquez sur **Plan**
3. Cliquez sur **Execute**

#### Méthode D : cible valide aléatoire

Cliquez sur **Random Valid** pour générer une pose atteignable aléatoire, puis Plan → Execute.

### 4.3  Consignes de sécurité

1. **Ralentissez à la première utilisation** : réglez Velocity / Acceleration à 0.1–0.3
2. **Arrêt d'urgence** : appuyez sur Ctrl+C à tout moment pour terminer le programme, ou coupez l'alimentation
3. **Limites d'articulation** : MoveIt ne planifiera pas au-delà des plages définies dans `joint_limits.yaml`, mais assurez-vous que celles-ci sont correctement configurées
4. **Matériel réel** : assurez-vous qu'il y a suffisamment d'espace autour du bras avant d'exécuter

### Aperçu de la configuration MoveIt

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Simulation Gazebo

La simulation Gazebo nécessite **4 terminaux exécutés en même temps**. Suivez strictement l'ordre.

### 5.1  Démarrer la simulation Gazebo  (Terminal 1)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Attendez l'apparition de la fenêtre Gazebo ; le robot reste brièvement suspendu dans les airs puis se pose.

### 5.2  Charger le contrôleur de trajectoire  (Terminal 2)

Par défaut, Gazebo n'active que `forward_position_controller` ; vous devez basculer manuellement vers  
`joint_trajectory_controller` :

```Markdown
#  Terminal 2
source ~/so101_ws/install/setup.bash

# Étape A — désactiver forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# Étape B — charger et activer joint_trajectory_controller avec le spawner
ros2 run controller_manager spawner joint_trajectory_controller

# Étape C — vérifier
ros2 control list_controllers
```

Sortie attendue :

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ N'utilisez pas `ros2 control load_controller` d'abord ! Cela place le contrôleur dans l'état  
`unconfigured`, ce qui empêche le spawner de l'activer. Si vous l'avez déjà fait,  
exécutez d'abord `unload_controller` et recommencez.
</callout>

### 5.3  Démarrer move_group  (Terminal 3)

```Bash
#  Terminal 3
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py use_sim_time:=True
```

### 5.4  Démarrer RViz  (Terminal 4)

```Bash
#  Terminal 4
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

Une fois RViz prêt :

1. **Planning Group → manipulator**
2. **Goal State → open** (ou `extended`, `rest`)
3. Cliquez sur **Plan** puis sur **Execute**

Les articulations du bras dans Gazebo suivront le mouvement.

<callout emoji="💡">
**Remarque** : en raison de la limitation des gains PID dans la version Humble de `gz_ros2_control`,  
la pince peut ne pas s'ouvrir physiquement dans Gazebo (le journal d'exécution rapporte quand même un succès).  
Le mode Mock et le matériel réel n'ont pas ce problème.
</callout>

### 5.5  Mode sans interface (headless)

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  Dépannage : échecs de chargement répétés

Si le spawner ne cesse de signaler `Failed to activate controller`, procédez comme suit pour tout réinitialiser :

```Bash
# 1. Décharger le contrôleur bloqué
ros2 control unload_controller joint_trajectory_controller

# 2. Désactiver forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# 3. Relancer le spawn
ros2 run controller_manager spawner joint_trajectory_controller
```

## Matériel réel

Prérequis : le bras SO-ARM101 est assemblé et la carte de pilotage des servomoteurs est connectée au PC via USB.

### 6.1  Démarrer les contrôleurs (facultatif)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

Le plugin `so_arm_hardware` effectue automatiquement :

1. L'ouverture du port série
2. Le scan des 6 ID de servomoteurs (1–6)
3. La vérification que chaque servomoteur répond
4. L'activation du couple et la lecture de la position courante

Une fois les contrôleurs prêts, ouvrez deux terminaux supplémentaires pour démarrer MoveIt :

```Bash
#  Terminal 2 — move_group
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py
```

```Bash
#  Terminal 3 — RViz
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

### 6.2  MoveIt (démarrage en une commande)

> La commande suivante **remplace** 6.1 (ne lancez pas les deux en même temps ; arrêtez les commandes de 6.1) — `demo.launch.py` inclut déjà la pile de contrôleurs en interne.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  Dépannage du port série

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  L'affichage RViz ne correspond pas à la pose réelle

Si la pose du bras dans RViz ne correspond pas au matériel réel (par exemple un décalage d'articulation ou un faux rapport de collision) :

1. Confirmez que les servomoteurs ont été étalonnés au centre
2. Ajustez le `position_offset` de chaque articulation dans `so_arm101.ros2_control.xacro`
3. Formule de conversion : `new offset = current offset + (currently displayed rad / 0.00153398)`
4. Recompilez le package `so_arm101_description` après la modification

---

## FAQ

### Q1 : « package not found » à la compilation

**R** : Assurez-vous que toutes les dépendances système sont correctement installées et que l'environnement ROS 2 est sourcé :

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### Q2 : « Permission denied » en accédant au port série au démarrage

**R** : Vérifiez les permissions du port série :

```Bash
# Correctif temporaire
sudo chmod 666 /dev/ttyACM0

# Correctif permanent (prend effet après déconnexion)
sudo usermod -a -G dialout $USER
```

### Q3 : La planification MoveIt échoue avec « Motion planning start tree could not be initialized »

**R** : Il y a généralement deux causes :

1. **Articulations hors limites** — vérifiez la sortie `FixStartStateBounds` dans le journal. La tolérance actuelle est de  
0.3 rad ; si le dépassement reste dans cette plage, cela passe. Sinon, ajustez `start_state_max_bounds_error`  
ou vérifiez les offsets des servomoteurs.
2. **État de départ en collision** — vérifiez la sortie `FixStartStateCollision` dans le journal. Si  
« Unable to find a valid state nearby » apparaît, la pose courante entre en auto-collision.  
Le bras est peut-être dans une pose repliée (par exemple la pince touche l'épaule), ou les offsets sont incorrects.  
Ajustez `position_offset` et réessayez.

### Q4 : Le bras ne bouge pas après Execute

**R** : Vérifiez les états des contrôleurs :

```Bash
ros2 control list_controllers
```

Assurez-vous que `joint_trajectory_controller` est `active`. Sinon, relancez le spawn :

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### Q5 : RViz démarre lentement ou se bloque

**R** : C'est normal. Au démarrage, MoveIt charge le modèle URDF, les plugins de vérification des collisions,  
les solveurs de cinématique, etc. ; le premier lancement prend environ 10 secondes.

### Q6 : Le chemin planifié n'est pas fluide ou est saccadé

**R** : Essayez ce qui suit :

- Passez à un autre planificateur (choisissez `RRTConnect` dans la liste déroulante Planner de RViz)
- Augmentez Planning Time à 10 secondes
- Assurez-vous que la cible est à l'intérieur de l'espace de travail (testez avec `Random Valid`)

### Q7 : La pince ne bouge pas dans Gazebo

**R** : Il s'agit d'une limitation des gains PID codés en dur dans la version Humble de `gz_ros2_control`  
(fixés à 0.1) qui ne peut pas être modifiée via les paramètres URDF. Execute rapporte un succès dans le journal,  
mais la pince ne s'ouvre pas dans la simulation physique de Gazebo. Le mode Mock et le matériel réel n'ont pas ce problème.

## Annexe : référence rapide des paramètres de lancement

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Arborescence des répertoires

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # bibliothèque utilitaire Python
├── so_arm101_description/          # URDF · contrôleurs · meshes · RViz · MuJoCo
├── so_arm101_moveit_config/        # SRDF MoveIt 2 · planificateurs · fichiers launch
├── so_arm_gz/                      # lancement de la simulation Gazebo
├── so_arm_hardware/                # pilote série SCS intégré (C++)
└── Simulation/                     # URDF CAO d'origine (conservé pour référence)
```
