[English](../en/so-arm101-tutorial.md) | [简体中文](../zh-hans/so-arm101-tutorial.md) | [繁體中文](../zh-hant/so-arm101-tutorial.md) | [Deutsch](../de/so-arm101-tutorial.md) | [Español](../es/so-arm101-tutorial.md) | Français | [Italiano](../it/so-arm101-tutorial.md) | [日本語](../ja/so-arm101-tutorial.md) | [한국어](../ko/so-arm101-tutorial.md) | [Português (BR)](../pt-br/so-arm101-tutorial.md) | [Português (PT)](../pt-pt/so-arm101-tutorial.md)

<title>Tutoriel du bras robotique SO-ARM101</title>

# Présentation du produit

Le SO-ARM101 est un **bras robotique 6 degrés de liberté à faible coût et entièrement open source** conçu par l'équipe LeRobot de Hugging Face, destiné à l'initiation pédagogique, à la validation de recherche et au prototypage industriel léger. Grâce à sa grande flexibilité et à un écosystème open source complet, il abaisse la barrière d'accès à l'intelligence incarnée et à la robotique.

### 1. Conception matérielle : performante, modulaire, facile à assembler et à personnaliser

- **Matériau structurel** : la structure centrale combine des pièces imprimées en 3D et des composants porteurs renforcés, avec un acheminement des câbles et une conception des articulations optimisés pour éviter les interférences de mouvement, équilibrant légèreté et durabilité ; les utilisateurs peuvent imprimer eux-mêmes des pièces de rechange ou d'extension.
- **Configuration d'entraînement** : le bras Follower embarque **6 servomoteurs 12 V 30 KG à couple élevé et encodeur magnétique**, associés à un retour d'encodeur magnétique 360° et à un algorithme de contrôle PID — un mouvement fluide, sans saccades, une grande précision de répétabilité, une forte puissance et des déplacements précis.
- **Système de vision** : livré en standard avec un **système de vision intelligent à double caméra** ; la caméra de l'effecteur capture les détails de préhension de près tandis que la caméra globale couvre l'environnement de travail. La fusion des données des deux caméras construit un modèle 3D et fournit un riche support de données pour l'apprentissage par imitation.
- **Connexion de commande** : équipé d'une carte de pilotage de servomoteurs qui se connecte directement à un PC ou à un Raspberry Pi via une interface USB-C — plug and play, ce qui simplifie le processus de connexion matérielle et permet de construire rapidement l'environnement de commande.

### 2. Écosystème logiciel : profondément intégré à LeRobot, développement IA sans barrière

- **Compatibilité avec le framework central** : profondément adapté au **framework open source d'apprentissage automatique pour robots LeRobot** de Hugging Face, construit sur PyTorch, avec des modèles pré-entraînés intégrés, des jeux de données multi-scénarios et un environnement de simulation, et compatible avec des jeux de données open source réputés tels que Stanford ALOHA.
- **Communication à faible latence** : utilise le **moteur de flux de données distribué DORA** pour une interaction à faible latence entre le matériel et les algorithmes ; Python s'exécute 17 fois plus vite que ROS2, et le rechargement à chaud du code est pris en charge, ce qui permet d'ajuster les politiques en temps réel sans redémarrer.
- **Open source de bout en bout** : les fichiers d'impression 3D du matériel, le code de commande logiciel, les scripts d'entraînement IA et l'ensemble des tutoriels sont **entièrement open source** ; les utilisateurs peuvent les modifier et les développer librement pour mettre en œuvre rapidement des extensions de fonctionnalités personnalisées.

### 3. Scénarios d'application principaux : adaptés à tous les cas d'usage, de l'initiation au déploiement

1. **Initiation à la robotique éducative** : propose un tutoriel de bout en bout, de l'assemblage du bras et de la programmation de base au déploiement de politiques IA, avec une interface d'opération visuelle et du code d'exemple, afin que les débutants maîtrisent rapidement le contrôle robotique et les compétences en application d'IA.
2. **Validation d'algorithmes de recherche** : axé sur la recherche en **apprentissage par imitation et par renforcement**, avec prise en charge de l'enregistrement des données d'opération humaine via la VR pour entraîner le robot ; cas typique : à partir de 50 séquences de vidéos d'opération de 15 secondes, 2 heures d'entraînement suffisent pour maîtriser des tâches telles que plier des vêtements, insérer une clé et trier des matériaux.
3. **Prototypage industriel léger** : validation à faible coût de solutions d'automatisation, adaptée à des scénarios tels que la **manutention de matériaux, l'assemblage de précision et le tri de pièces**, offrant les fonctions essentielles d'un bras robotique de qualité industrielle à un coût de l'ordre du millier de yuans pour une validation rapide de prototype.

### 4. Atouts du produit

- **Rapport qualité-prix exceptionnel** : la version de base démarre à environ 100 $, et la conception open source réduit les coûts d'acquisition et de développement secondaire, ce qui la rend adaptée à un déploiement en série par des particuliers, des laboratoires et des PME.
- **Open source sur toute la chaîne** : matériel, logiciel et tutoriels sont entièrement ouverts, sans barrière technique, avec une personnalisation et une extension de fonctionnalités libres pour s'adapter rapidement à de nombreux scénarios.
- **Propice au développement IA** : adossé à l'écosystème LeRobot, il appelle les modèles pré-entraînés et les jeux de données en un clic, simplifiant tout le processus, de la collecte de données et de l'entraînement de politiques au déploiement, et accélérant la mise sur le marché des algorithmes d'intelligence incarnée.

### 5. Fiche technique du produit

| **Spécification** | **Détails** |
|-|-|
| Degrés de liberté | 6 axes (rotation / inclinaison de l'épaule, flexion du coude, flexion / rotation du poignet, ouverture/fermeture de la pince) |
| Matériau structurel | Pièces imprimées en 3D (PLA+) |
| Moteurs d'entraînement | 12 \* servomoteurs Feetech STS3215 (alimentation 12 V)  <br/>Rapport de réduction du bras Follower STS3215-C018 : 1/345  <br/>Rapport de réduction du bras Leader STS3215-C001 : 1/345 (épaule), STS3215-C044 1/191 (coude), STS3215-C046 1/147 (poignet) |
| Capacité de charge utile | Charge utile maximale en bout d'effecteur 200 g (pince fermée) |
| Précision de répétabilité | ±1,5 mm (influencée par l'étalonnage et le jeu moteur) |
| Rayon d'action | Portée maximale en bout d'effecteur 350 mm |
| Alimentation requise | Leader : adaptateur 5 V 6 A ; Follower : adaptateur 12 V 5 A (pour les besoins à couple élevé) |
| Interface de communication | Connexion directe USB-C au PC (transfert des commandes de contrôle) |
| Système de vision | Caméra (1080P@30FPS, FOV86° sans distorsion, ou focale fixe 1080P@60FPS FOV100°) |
| Type de pince | Pince PLA+, pince TPU, pince parallèle à deux doigts prise en charge, ouverture 0-50 mm, force de préhension max. 5 N |
| Framework de contrôle | Bibliothèque LeRobot basée sur Python, offrant une API de contrôle moteur (lerobot.control) |
| Modèles pré-entraînés | Prend en charge des algorithmes d'apprentissage par imitation tels qu'ACT (Action Chunking Transformer) et Diffusion Policy |
| Modèle léger | Modèle vision-langage-action SmolVLA (450 M de paramètres) : ・Inférence CPU en temps réel (tourne sur MacBook) ・Réponse asynchrone 30 % plus rapide ・Seulement 64 tokens visuels par image ・Visualisation d'état : suivi en temps réel avec la bibliothèque rerun |
| Poids total | ≈1,2 kg (moteurs et câbles compris) |
| Dimensions assemblées | Diamètre de la base 120 mm, hauteur (entièrement déployé) 650 mm |
| Température de fonctionnement | 0℃–40℃ (limite des servomoteurs) |
| Niveau sonore | <45 dB (fonctionnement à vide) |
| Tutoriel débutant | Oui |
| GITHUB officiel | Oui |

![L'image montre les schémas cotés des bras Leader et Follower du bras robotique SO-ARM101, accompagnés du nom du produit, du matériau, des dimensions et d'autres informations. Les schémas cotés indiquent la taille de chaque pièce, par exemple le bras Leader mesure 525 mm de long et le bras Follower 532 mm. Le matériau du produit est du PLA+ à optimisation topologique et les dimensions du produit sont 111x239x525 mm (Leader) et 111x173x532 mm (Follower). Cette image correspond à la section « Fiche technique du produit » du document et présente visuellement les spécifications dimensionnelles du bras.](../en/images/d01-01.png)

| **Article / nom du package** | **Fonction / description** |
|-|-|
| Bibliothèque LeRobot | Version : ≥0.1.0 Framework de contrôle central : • API Python (lerobot.control) ・Planification de mouvement en temps réel ・Traitement des flux de données capteurs |
| PyTorch | Version : ≥2.0 Moteur d'inférence d'apprentissage profond (prend en charge des modèles tels que SmolVLA) |
| Transformers | Version : ≥4.40.0 Bibliothèque de modèles Hugging Face (charge les modèles pré-entraînés ACT/Diffusion Policy) |
| rerun | Version : ≥0.16.0 Outil de visualisation en temps réel de l'état du robot (rendu 3D des angles d'articulation / trajectoires) |
| ROS 2 | Version : Humble/Foxy En option : interface de pilote ROS2 (package soarm100_ros) |
| ACT | Action Chunking Transformer, prédiction d'actions sur séquences longues (par ex. tâches de préhension continue) |
| Diffusion Policy | Politique de diffusion, contrôle robuste dans les espaces d'action de grande dimension (manipulation résistante aux perturbations) |
| SmolVLA | Modèle vision-langage-action, exécution d'instructions multimodales (par ex. « attrape le bloc rouge ») ・450 M de paramètres, fonctionne sur CPU/GPU |

| **Catégorie de fonction** | **Description de la fonction** |
|-|-|
| Contrôle au niveau des articulations | ・Contrôle indépendant d'angle / de vitesse sur 6 axes (plage ±180°) ・Protection par limites logicielles des articulations ・Retour en temps réel de la température / tension du moteur |
| Contrôle dans l'espace cartésien | ・Positionnement XYZ de l'effecteur (précision ±1,5 mm) ・Réglage d'orientation par angles d'Euler (Roll/Pitch/Yaw) |
| Opération de la pince | ・Réglage d'ouverture continu 0-50 mm ・Réglage dynamique de la force de préhension (0,1-5 N) ・Préhension adaptative à l'épaisseur de l'objet |
| Mode Leader/Follower | ・Apprentissage manuel par le bras Leader → imitation en temps réel par le bras Follower ・Enregistrement / relecture des données d'action |

| **Catégorie de fonction** | **Description de la fonction** |
|-|-|
| Apprentissage par imitation | ・Enregistrement des données de démonstration humaine → entraînement de modèles ACT/Diffusion Policy ・Prise en charge du transfert de politiques multi-tâches (par ex. empilage de blocs → tri d'objets) |
| Interaction multimodale | ・Le modèle SmolVLA interprète les instructions en langage naturel (par ex. « attrape le bloc bleu ») ・Exécution vision-action de bout en bout |
| Interface d'apprentissage par renforcement | ・Environnement compatible Gymnasium ・Fonctions de récompense personnalisées (par ex. temps d'achèvement de tâche / optimisation énergétique) |
| Système d'étalonnage | ・Étalonnage du point zéro Leader/Follower ・Étalonnage main-œil caméra-bras ・Compensation automatique du couple des articulations |
| Gestion des flux de données | ・Enregistrement / relecture de jeux de données au format .h5 ・Synchronisation cloud Hugging Face Hub ・Alignement temporel des données capteurs |
| Suivi en temps réel | ・Visualisation rerun des angles d'articulation / de la trajectoire de l'effecteur ・Alarmes d'anomalie moteur (surchauffe / blocage) ・Diagnostic de latence de communication |
| Intégration ROS 2 | ・Publication des états d'articulation (/joint_states) ・Abonnement aux commandes de contrôle (/arm_controller) ・Transfert de flux de nuages de points (/depth_points) |
| Déploiement multiplateforme | • Linux/Windows/macOS (API Python) ・Conteneurisation Docker ・Contrôle à distance via le Web (interface FastAPI) |
