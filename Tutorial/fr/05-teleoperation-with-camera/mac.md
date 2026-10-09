[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | Français | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Ordinateur Mac

## Connecter la caméra à l'ordinateur

```Shell
lerobot-find-cameras opencv
```

![L'image montre le résultat de la détection après la connexion d'une caméra à un Mac. Elle liste les deux caméras générées automatiquement, la caméra externe et la caméra frontale intégrée du Mac. Le Fps de la caméra externe est de 60.00024 et celui de la caméra intégrée de 30.0. Cette image concerne le contenu sur la connexion d'une caméra à un Mac et présente visuellement le résultat de la détection après la connexion, ce qui aide à comprendre le type, l'ID, l'API backend et la fréquence d'images de chaque caméra.](../../en/images/d31-01.png)

## Une caméra, téléopération avec affichage du flux de la caméra

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

Après l'exécution, la téléopération démarre

La fenêtre rerun.io s'ouvre, affichant en temps réel la trajectoire de chaque articulation de servomoteur, ainsi que le flux vidéo de la caméra en direct

et enregistre les images dans le répertoire `~/username/outputs/captured_images`

![L'image montre la fenêtre rerun.io qui s'ouvre au démarrage de la téléopération après l'exécution. À gauche figurent des graphiques des trajectoires de plusieurs articulations de servomoteur, présentés sous forme de courbes montrant le mouvement des différentes articulations. À droite, le flux vidéo de la caméra montre en temps réel la scène intérieure, où l'on peut voir une table, des chaises et quelques objets. On trouve également des informations en forme de barres en bas. Cette image est étroitement liée au contexte et présente visuellement les trajectoires des articulations de servomoteur et le flux vidéo de la caméra en direct pendant la téléopération ; elle illustre aussi que les images sont enregistrées dans le répertoire indiqué.](../../en/images/d31-02.png)

## Plusieurs caméras, téléopération avec affichage des flux des caméras

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 1920, height: 1080, fps: 30, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

![L'image montre la fenêtre rerun.io utilisée pour la téléopération avec plusieurs flux de caméra. À gauche se trouve le flux vidéo en direct de la caméra, montrant des objets sur un bureau ; à droite, des graphiques de données montrant les trajectoires de différentes articulations, telles que observation_wip. En bas figure une zone Streams listant les données de plusieurs articulations. En haut à droite se trouvent des informations de données telles que Application ID et Source IP. Cette image correspond au contenu « Plusieurs caméras, téléopération avec les flux des caméras » et présente visuellement les flux et les données pendant la téléopération.](../../en/images/d31-03.png)
