[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | Français | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Ordinateur Windows

## Connecter la caméra à l'ordinateur

```Shell
lerobot-find-cameras opencv
```

![Cette image est la fenêtre de ligne de commande Windows, montrant des erreurs de connexion de caméra et les résultats de détection des périphériques. En haut figure une erreur : « ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range ». En dessous sont listées les caméras détectées, dont Camera #0 et Camera #1, avec leur nom, leur type, leur API backend, leur configuration de flux par défaut, leur format, leur source, leur largeur, leur hauteur et leur fréquence d'images ; en bas figurent des erreurs telles que « lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0 ». Cela correspond au scénario d'erreur mentionné dans le document, « la caméra ne peut pas se connecter, mais changer de caméra dans Tencent Meeting s'ouvre toujours normalement », et constitue la rétroaction d'erreur réelle à l'exécution avant la modification du code du backend OpenCV.](../../en/images/d32-01.png)

## Téléopération avec affichage du flux de la caméra

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

La fenêtre rerun.io s'ouvre, affichant en temps réel la trajectoire de chaque articulation de servomoteur, ainsi que le flux vidéo de la caméra en direct

et enregistre les images dans le répertoire `C:\Users\username\outputs\captured_images`

![L'image montre la fenêtre rerun.io, affichant en temps réel les trajectoires des articulations de servomoteur et le flux vidéo de la caméra en direct. À gauche se trouve l'interface de blueprint avec des options telles que « teleoperation ». Au milieu se trouve le graphique de trajectoire, affichant des données de position d'articulation telles que « observation_wrist_rot.pos ». À droite se trouve le flux vidéo de la caméra, montrant la scène du point de vue du robot. En haut à droite s'affiche « Waiting for data on rerun: http://127.0.0.1:9876/remote... », avec les informations de source de données en dessous. Cette image concerne le contenu décrivant la fenêtre rerun.io montrant le flux vidéo de la caméra en temps réel, et présente visuellement le résultat.](../../en/images/d32-02.png)

## Si vous rencontrez l'erreur suivante

La caméra ne peut pas se connecter, mais changer de caméra dans Tencent Meeting s'ouvre toujours normalement

![L'image montre l'interface de ligne de commande Windows avec les résultats de détection des caméras. En haut s'affiche « Detected Cameras » et des informations liées aux caméras telles que le nom, le type, l'ID et l'API backend. En dessous figure une erreur indiquant que, lors de l'exécution de lerobot_find_cameras_openpyc, la caméra OpenCV n'a pas pu se connecter ou être configurée, vous invitant à exécuter lerobot_find_cameras_opencv pour trouver une caméra disponible, et qu'aucune caméra ne peut être connectée, de sorte que l'enregistrement des images sera interrompu. Cette image correspond au contexte du problème de connexion de la caméra et présente visuellement l'erreur.](../../en/images/d32-03.png)

Modifiez le fichier `lerobot\src\lerobot\cameras\utils.py` pour changer le backend OpenCV en `cv2.CAP_SHOW`

![L'image montre le code de la fonction `get_cv2_backend()` dans le fichier `lerobot\\src\\lerobot\\cameras\\utils.py`. Lorsque le système est Windows, la fonction renvoie `int(cv2.CAP_DSHOW)`, utilisé pour utiliser MSMF au lieu d'AVFOUNDATION sous Windows. Le code contient aussi un commentaire sur `cv2.CAP_MSMF`, et la façon dont les autres systèmes tels que Darwin (macOS) et Linux sont traités. Cette image concerne l'opération consistant à modifier le fichier `lerobot\\src\\lerobot\\cameras\\utils.py` pour changer le backend OpenCV en `cv2.CAP_SHOW`, et constitue un exemple de modification de code.](../../en/images/d32-04.png)

> C'est un bug que même Doubao ne peut pas résoudre ; c'est uniquement parce que la bibliothèque lerobot est trop profondément encapsulée, et il est très difficile pour les débutants de déboguer

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## Connecter plusieurs caméras, téléopération avec affichage des flux des caméras

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![L'image montre la fenêtre rerun.io utilisée pour la téléopération avec des flux de caméra. À gauche se trouve un graphique de trajectoire montrant les données de trajectoire de plusieurs articulations, telles que observation_wrist_l_pos et observation_wrist_r_pos. À droite, en haut se trouve le flux vidéo de la caméra en direct et en bas la fenêtre de Tencent Meeting. En haut à droite s'affiche « Waiting for data on rerun: http://127.0.0.1:9678/remote... ». Cette image concerne le contenu sur la connexion de plusieurs caméras et l'affichage des flux des caméras pendant la téléopération, et présente visuellement le résultat.](../../en/images/d32-05.png)
