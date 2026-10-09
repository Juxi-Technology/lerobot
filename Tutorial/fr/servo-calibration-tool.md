[English](../en/servo-calibration-tool.md) | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | [Deutsch](../de/servo-calibration-tool.md) | [Español](../es/servo-calibration-tool.md) | Français | [Italiano](../it/servo-calibration-tool.md) | [日本語](../ja/servo-calibration-tool.md) | [한국어](../ko/servo-calibration-tool.md) | [Português (BR)](../pt-br/servo-calibration-tool.md) | [Português (PT)](../pt-pt/servo-calibration-tool.md)

# Outil d'étalonnage des servomoteurs STS3215 pour la série So-ARM (facultatif)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**Une boîte à outils d'étalonnage en usine des servomoteurs FTServo et d'étalonnage LeRobot conçue pour les bras de la série So-ARM 10X**

> ⚠️ **Remarque de compatibilité : ce système ne prend actuellement en charge que les servomoteurs Feetech (série STS3215)**. La table des registres, le format des paramètres xdat et la table des débits en bauds sont tous conçus pour la série Feetech STS3215.

> 📜 **Origine et crédits : cet outil est adapté et amélioré à partir du projet** [**Seeed_RoboController de Seeed Studio**](https://github.com/Seeed-Studio), **initialement publié sous licence MIT**. Tout en conservant les fonctionnalités essentielles d'origine, ce projet refond l'interface graphique et ajoute le débogueur FT, la sauvegarde/restauration des paramètres xdat, la prise en charge multiplateforme, la commutation chinois/anglais et d'autres améliorations.

---

## ✨ Fonctionnalités

| Fonctionnalité | Description |
|-|-|
| Détection automatique des ports | Détecte intelligemment les ports série USB et filtre les périphériques virtuels |
| Prise en charge multiplateforme | Compatible Windows / Ubuntu / macOS |
| Synchronisation double port | Les ports série gauche et droit fonctionnent indépendamment, avec prise en charge du contrôle à distance synchronisé double port Leader/Follower |
| Commutation chinois/anglais | Bascule chinois/anglais en un clic dans l'interface, le choix étant mémorisé automatiquement |
| Étalonnage du centre | Grave la position actuelle du servomoteur comme centre 2048 (persistée dans l'EEPROM) |
| Test du centre | Active le couple et déplace le servomoteur vers le centre pour vérifier le résultat de l'étalonnage |
| Désactiver les moteurs | Désactive en un clic le couple de tous les servomoteurs pour faciliter le réglage manuel |
| Scan automatique | Détecte automatiquement tous les servomoteurs en ligne dans la plage d'ID 1–20 |
| Contrôle d'un servomoteur unique | Un curseur contrôle en temps réel la position et l'activation/désactivation du couple d'un servomoteur |
| Débogueur FT | Connexion série, scan, lecture/écriture de paramètres, contrôle de position, changement de débit en bauds, réinitialisation d'usine, sauvegarde des paramètres xdat |
| Paramètres xdat | Enregistrer les paramètres EEPROM actuels du servomoteur / ouvrir une sauvegarde pour la restaurer |
| Étalonnage LeRobot | Génère des fichiers d'étalonnage JSON au format LeRobot |
| Aller au centre depuis un fichier d'étalonnage | Déplace le bras vers le centre à partir d'un fichier d'étalonnage |

---

## 📚 Tutoriels détaillés

### Chinois

| OS | Tutoriel |
|-|-|
| Windows | \[Tutoriel Windows\](docs/zh/Windows教程.md) |
| Linux | \[Tutoriel Linux\](docs/zh/Linux教程.md) |
| macOS | \[Tutoriel macOS\](docs/zh/macOS教程.md) |

### Anglais

| OS | Guide |
|-|-|
| Windows | \[Guide Windows\](docs/en/Windows.md) |
| Linux | \[Guide Linux\](docs/en/Linux.md) |
| macOS | \[Guide macOS\](docs/en/macOS.md) |

---

## 🖥️ Aperçu de l'interface

Le programme principal comporte trois onglets :

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

- **Barre supérieure** : titre de l'application, listes déroulantes de sélection des ports, bouton d'actualisation, bouton de contrôle à distance, bouton de commutation de langue.
- **🦾 Onglet 1 Étalonnage des servomoteurs** : actions rapides pour les panneaux gauche et droit (étalonnage du centre, test du centre, désactivation des moteurs) plus l'état en direct.
- **🎚️ Onglet 2 Contrôle d'un servomoteur unique** : réglez finement la position de chaque servomoteur en ligne avec un curseur et basculez son couple.
- **🔬 Onglet 3 Débogueur FT** : connexion série, scan, lecture/écriture de paramètres, contrôle de position, débit en bauds/réinitialisation d'usine, sauvegarde et restauration des paramètres xdat.

---

## 🚀 Démarrage rapide

> Pour les tutoriels complets par système, voir \[📚 Tutoriels détaillés\](#-详细教程). Voici les points clés pour chaque système.

### Windows

1. Installez [Python 3.10+](https://www.python.org/downloads/) (cochez **Add to PATH**)
2. Créez un environnement virtuel et installez les dépendances :

```Bash
cd Juxi_ServoController
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

1. Vérifiez l'environnement et lancez :

```Bash
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Confirmez le numéro de port dans le Gestionnaire de périphériques (par ex. `COM3`) et sélectionnez-le dans la barre supérieure. Pour spécifier les ports manuellement :

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux (Ubuntu / Debian)

1. Installez les polices CJK et les dépendances :

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ Ajoutez les permissions du port série (groupe dialout)** [obligatoire] :

```Bash
sudo usermod -a -G dialout $USER
# Prend effet après déconnexion puis reconnexion
```

1. Créez un environnement virtuel, installez les dépendances et lancez :

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Les périphériques série sont `/dev/ttyUSB0` / `/dev/ttyACM0`. Pour spécifier manuellement :

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/ttyUSB0 --port2 /dev/ttyUSB1
```

### macOS

1. Installez `Python` avec `Homebrew ` :

```Bash
brew install python
```

1. Créez un environnement virtuel, installez les dépendances et lancez :

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. **⚠️ Nommage des ports série** : sous macOS, utilisez `/dev/cu.usbserial-*` (**recommandé, non bloquant**) plutôt que `/dev/tty.*`. Pour les lister :

```Bash
ls /dev/cu.*
```

Pour spécifier manuellement :

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### Outils en ligne de commande généraux (sans interface graphique)

```Bash
# Scanner les servomoteurs
python -m src.tools.scan_id

# Étalonnage rapide du centre des servomoteurs
python -m src.tools.servo_quick_calibration

# Test du centre des servomoteurs
python -m src.tools.servo_center_test

# Désactiver tous les servomoteurs
python -m src.tools.servo_disable

# Étalonnage au format LeRobot
python -m src.tools.lerobot_calibrate

# Contrôle à distance synchronisé double port
python -m src.tools.servo_remote_control
```

---

## 📖 Étapes d'utilisation

### 1. Connecter et détecter les servomoteurs

1. Connectez la carte de contrôle du bras via un adaptateur USB-série et alimentez les servomoteurs.
2. Ouvrez l'interface graphique et sélectionnez le port dans la liste déroulante de la barre supérieure (ou cliquez sur `🔄` pour actualiser).
3. Le haut du panneau affiche `🟢 Connected` et scanne automatiquement les servomoteurs en ligne dans la plage d'ID 1–20 (généralement 1–6).

> S'il signale que le port est occupé, assurez-vous qu'aucun autre programme (un moniteur série, un outil précédemment ouvert qui ne s'est pas fermé) ne l'utilise.

### 2. Étalonnage du centre (définir la position actuelle à 2048)

> Avant d'étalonner, placez physiquement le bras de sorte que chaque articulation soit à la position « zéro / centre » souhaitée.

1. Cliquez sur le bouton **PortX Center Calibration** du panneau.
2. Le programme désactive d'abord les servomoteurs et vous invite à les déplacer manuellement vers le centre voulu.
3. Après votre confirmation, le programme effectue, pour chaque servomoteur : déverrouiller l'EEPROM → écrire la commande d'étalonnage (valeur 128 à l'adresse 40) → reverrouiller l'EEPROM.
4. Après l'étalonnage, utilisez « Center test » pour vérifier : le servomoteur doit rester en place (très peu de mouvement), ce qui signifie que l'étalonnage a réussi.

### 3. Test du centre

1. Cliquez sur **PortX Center Test**.
2. Le programme active le couple et déplace tous les servomoteurs vers 2048.
3. Si les servomoteurs bougent à peine depuis leur position actuelle, l'étalonnage est correct ; s'ils bougent beaucoup, la valeur d'étalonnage n'est pas fiable et doit être refaite.

### 4. Désactiver les moteurs (réglage manuel)

- Cliquez sur **PortX Disable Motors** pour désactiver le couple de tous les servomoteurs de ce port afin qu'ils puissent être tournés librement à la main.
- Pour un servomoteur unique, basculez son couple individuellement dans la page **Single-Servo Control** à l'aide de l'interrupteur de couple sous le curseur.

### 5. Changer l'ID d'un servomoteur

1. Allez dans la page **🔬 FT Debugger**, connectez le port série et scannez les servomoteurs.
2. Sélectionnez le servomoteur cible, modifiez la valeur « Servo ID » (adresse 0x05) dans la table des paramètres, et cliquez sur écrire.
3. Le programme effectue : déverrouiller → écrire à l'adresse 5 → vérifier le nouvel ID → reverrouiller.

> ⚠️ Avant de changer un ID, assurez-vous que c'est le seul servomoteur sur le bus pour éviter tout conflit d'ID.

### 6. Changer le débit en bauds / réinitialisation d'usine

- **Changer le débit en bauds** : dans la zone « Baud rate / factory reset » de la page FT Debugger, sélectionnez le nouveau débit en bauds (38400 – 1000000 bps) et appliquez-le. Après l'écriture, le débit en bauds série est commuté automatiquement et vérifié par ping ; en cas d'échec, il revient automatiquement en arrière.
- **Réinitialisation d'usine** : le servomoteur revient aux valeurs d'usine (ID=1, débit en bauds=1000000) ; relancez un scan ensuite.

### 7. Sauvegarde et restauration des paramètres xdat

Dans la zone « xdat parameters (EEPROM only) » de la page FT Debugger :

1. **💾 Save current servo** : enregistre les paramètres EEPROM du servomoteur actuellement sélectionné dans un fichier xdat (sauvegarde).
2. Après avoir modifié librement les paramètres des servomoteurs, si vous voulez restaurer :
3. **📂 Open xdat** : charge le fichier de sauvegarde.
4. **📤 Restore parameters to servo** : réécrit la sauvegarde dans l'EEPROM du servomoteur courant.

### 8. Contrôle à distance synchronisé double port

> ⚠️ **Sens : le port 1 contrôle le port 2**. Le port 1 (leader) ne fait que lire les angles des servomoteurs ; le port 2 (follower) est contrôlé en synchronisation.

1. Cliquez sur **🎮 Remote** dans la barre supérieure (le port 1 lit les angles → le port 2 contrôle en synchronisation les servomoteurs ayant les mêmes ID).
2. Les deux ports doivent avoir des ID de servomoteurs correspondants ; seuls les servomoteurs de l'intersection sont synchronisés.
3. Cliquez à nouveau sur le même bouton pour arrêter ; ensuite les threads de scan des panneaux gauche et droit reprennent automatiquement.

### 9. Étalonnage LeRobot (ligne de commande)

```Bash
# Étalonner le bras Follower (enregistré dans ~/.cache/huggingface/lerobot/calibration/robots/so_follower/)
python -m src.tools.lerobot_calibrate --arm-type follower

# Étalonner le bras Leader
python -m src.tools.lerobot_calibrate --arm-type leader
```

Flux : désactiver les servomoteurs → déplacer chaque articulation vers le centre et enregistrer `homing_offset` → balayer lentement toute la course et enregistrer `range_min/max` (`wrist_roll` est une articulation à rotation continue avec une plage fixe de `[0,4095]`) → enregistrer le JSON.

Aller au centre à l'aide d'un fichier d'étalonnage :

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ Remarques



1. **La sécurité d'abord** : l'étalonnage du centre est persisté dans l'EEPROM. Avant d'étalonner, assurez-vous que l'alimentation est stable et que le bras n'entrera en collision avec personne ni aucun objet.
2. **Alimentation** : pour le SoARM 101 standard, DC 5V 5A est recommandé ; pour la version Pro, DC 12V 5A. Une alimentation insuffisante provoque des pertes de pas des servomoteurs ou des échecs de communication.
3. **Exclusivité du port série** : sous Windows, le port est verrouillé en exclusivité, le même port ne peut donc pas être utilisé en même temps par le thread de scan de l'interface graphique et par le sous-processus d'étalonnage. L'outil arrête automatiquement le thread de scan et termine l'ancien processus avant d'opérer ; ne cliquez pas plusieurs fois à la main.
4. **Permissions série sous Linux** : accéder à `/dev/ttyUSB*` / `/dev/ttyACM*` nécessite d'ajouter l'utilisateur au groupe `dialout` (voir le \[tutoriel Linux\](docs/zh/Linux教程.md)).
5. **Nommage série sous macOS** : utilisez `/dev/cu.*` (non bloquant) plutôt que `/dev/tty.*` (bloquant, peut se figer) ; voir le \[tutoriel macOS\](docs/zh/macOS教程.md).
6. **Branchement à chaud** : après avoir débranché l'USB, le programme tente de se reconnecter automatiquement ; après l'avoir rebranché, cliquez sur `🔄` pour actualiser la liste des ports.
7. **Protection contre la surchauffe / surtension** : le programme surveille la tension et la température (alarme au-dessus de 60 °C). Si les servomoteurs restent chauds, arrêtez et laissez-les refroidir.
8. **L'étalonnage du centre est irréversible** : après l'écriture, l'offset d'origine est écrasé et ne peut pas être annulé. Notez d'abord la position d'origine avant d'étalonner.
9. **Risque lors du changement d'ID** : si l'écriture ou la vérification échoue, le programme signale une erreur et reprend le scan, mais dans des cas extrêmes le servomoteur peut être « perdu ». Si cela se produit, essayez « Factory reset » (après réinitialisation, l'ID revient à 1).
10. **Problème d'encodage** : si les emojis apparaissent de façon illisible dans la console Windows, définissez `PYTHONIOENCODING=utf-8` avant de lancer les outils en ligne de commande. Linux/macOS avec UTF-8 natif n'ont généralement pas ce problème.

---

## 🛠️ Dépannage

| Symptôme | Cause possible | Solution |
|-|-|-|
| Impossible d'ouvrir le port série / port occupé | Un autre programme l'utilise | Fermez les programmes tels que les moniteurs série, ou changez de port et redémarrez l'outil |
| Aucun servomoteur trouvé lors du scan | Alimentation insuffisante / câblage incorrect / débit en bauds incohérent | Vérifiez l'alimentation et le câblage, et confirmez que les servomoteurs sont à 1 M bauds |
| Les servomoteurs s'emballent après l'étalonnage du centre | La pose n'a pas été correctement définie avant l'étalonnage | Refaites « désactiver → placer manuellement → étalonnage du centre » |
| La température monte trop vite | Charge excessive ou blocage | Vérifiez que le mécanisme ne grippe pas ; réduisez la vitesse/l'accélération |
| Servomoteur introuvable après changement de son ID | Conflit d'ID ou échec d'écriture | Réinitialisation d'usine et nouveau scan |
| Contrôle à distance désynchronisé | Les deux ports ont des ID incohérents | Confirmez que les servomoteurs ayant le même ID sont en ligne sur les ports leader et follower |

---

## 📁 Structure des répertoires

```Plain Text
Juxi_ServoController/
├── docs/                    # Tutoriels par système (chinois/anglais)
│   ├── zh/                  # Tutoriels en chinois
│   │   ├── Windows教程.md
│   │   ├── Linux教程.md
│   │   └── macOS教程.md
│   └── en/                  # Tutoriels en anglais
│       ├── Windows.md
│       ├── Linux.md
│       └── macOS.md
├── src/
│   ├── gui/                  # Interface graphique PySide6
│   │   ├── factory_calibration_tool.py   # Outil principal (étalonnage double port + contrôle à distance + commutation de langue)
│   │   ├── ft_debugger.py                # Débogueur FT (lecture/écriture de paramètres / sauvegarde xdat)
│   │   ├── calibration_wizard.py         # Assistant d'étalonnage LeRobot
│   │   ├── theme_utils.py                # Thème clair
│   │   └── language_dialog.py            # Boîte de dialogue de sélection de langue
│   ├── tools/                # Outils en ligne de commande
│   ├── xdat_utils.py         # Lecture/écriture des fichiers de paramètres xdat
│   ├── i18n*.py / i18n_translations/     # Internationalisation chinois/anglais
│   ├── port_utils.py         # Détection des ports série
│   └── calibration_manager.py# Gestion des fichiers d'étalonnage LeRobot
├── scservo_sdk/              # SDK de communication des servomoteurs FTServo
├── requirements.txt
└── setup.py                  # Script de vérification de l'environnement
```
