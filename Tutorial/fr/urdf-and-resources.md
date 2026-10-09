[English](../en/urdf-and-resources.md) | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | [Español](../es/urdf-and-resources.md) | Français | [Italiano](../it/urdf-and-resources.md) | [日本語](../ja/urdf-and-resources.md) | [한국어](../ko/urdf-and-resources.md) | [Português (BR)](../pt-br/urdf-and-resources.md) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>Fichiers URDF et ressources de référence</title>

# [Fichier URDF](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf) officiel de LeRobot



## URDF Studio

https://urdf.d-robotics.cc/



## Contrôle en simulation ROS2 (à implémenter soi-même)

https://github.com/holmsslk/so-arm-moveit-hardware



## Interface graphique officielle de LeRobot

https://github.com/huggingface/leLab

LeLab est une application web qui réunit tout le flux de travail de LeRobot — étalonnage, téléopération, enregistrement, entraînement, relecture — dans une seule interface de navigateur. Il suffit de connecter le bras robotique, d'ouvrir l'application et de commencer à travailler. Aucun travail laborieux en ligne de commande et aucune saisie au clavier ne sont nécessaires.

🤗 Le point d'entrée web natif de LeRobot, conçu pour permettre aux nouveaux utilisateurs de passer de la « sortie du carton » à « l'entraînement de leur première politique » en quelques minutes.

🤗 Installation et exécution de l'ensemble avec une seule commande.



# Piloter le bras Follower depuis un téléphone

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## Développement robotique dans le cloud : appareils ROS 2 et simulation LeRobot Isaac Sim et streaming de données sur AWS

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## Configuration des ID de servomoteurs et étalonnage du centre dans l'interface web

https://bambot.org/feetech.js?lang=zh

1. Saisissez 0 ou 1 selon le modèle du servomoteur, puis cliquez sur « Connect »

![L'image montre l'interface de connexion pour la configuration des ID de servomoteurs et l'étalonnage du centre dans l'interface web. L'interface comporte une section « Connect » contenant une liste déroulante de débit en bauds, actuellement réglée sur « 1,000,000 bps (Index 0) » ; une liste déroulante de fin de protocole, actuellement réglée sur « 0=STS/SMS » ; et un bouton « Connect ». Le bas de l'interface affiche « Status: Disconnected ». L'image est étroitement liée au contexte : après avoir saisi 0 ou 1 selon le modèle du servomoteur et cliqué sur « Connect », les servomoteurs d'ID 1~6 sont scannés pour confirmer le servomoteur d'ID correspondant — c'est une interface clé de ce flux.](../en/images/d68-01.png)

2. Scannez les servomoteurs d'ID 1\~6 ; utilisez FOUND dans les résultats du scan pour confirmer le servomoteur d'ID correspondant. Par exemple, dans l'image, le servomoteur d'ID 1 a été trouvé

![L'image montre l'interface de scan des servomoteurs dans URDF Studio, l'outil officiel de LeRobot. L'interface indique un ID de début 1 et un ID de fin 6, avec un bouton « Start scan » en dessous. Dans les résultats du scan, le scan de l'ID 1 a trouvé l'ID1239, tandis que le scan des ID 2 à 6 signale chacun « ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0 ». Cette image se rapporte à l'opération de scan des servomoteurs dans URDF Studio, l'outil officiel de LeRobot, décrite dans le contexte, et présente visuellement le processus de scan et ses résultats.](../en/images/fix-01.png)

3. Configuration des ID et étalonnage du centre

① Réglez la saisie de l'ID du servomoteur courant sur l'ID du servomoteur scanné

② Saisissez un nombre dans « ID management » et cliquez sur « Change ID » pour définir l'ID

③ Étalonnage du centre (le centre du servomoteur STS3215 est 2047, celui du servomoteur SCS0009 est 511)

Servomoteur STS : saisissez 2047 dans « Position control » et cliquez sur « Set »

Servomoteur SCS : saisissez 511 dans « Position control » et cliquez sur « Set »

![L'image montre l'interface de contrôle d'un servomoteur unique de LeRobot. Le « Current servo ID » est affiché comme 1 ; en dessous, sous « ID management », se trouvent le nombre 1 et un bouton « Change ID », avec le message « Success: ID changed to 1 » en dessous. Dans la zone Position Control se trouve un bouton « Read position » affichant la position 2047, à côté d'un bouton « Set ». Cette image se rapporte à la section « Configuration des ID et étalonnage du centre » du document et présente visuellement l'interface permettant de définir les ID de servomoteurs et d'étalonner le centre, aidant les utilisateurs à comprendre comment effectuer ces réglages dans LeRobot.](../en/images/d68-02.png)
