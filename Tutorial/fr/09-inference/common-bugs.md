[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | Français | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# Bogues courants et correctifs

## La capture de la caméra échoue

![Cette image montre la sortie du terminal lors de l'exécution du code robot LeRobot. Les journaux `INFO` montrent l'ouverture de la caméra OpenCV et la déconnexion du Follower ; le journal `ERROR` signale que dans le fichier `camera_opencv.py` la fonction `read` a levé une `RuntimeError` à cause de `OpenCVCamera(0) read failed`. L'image se rapporte au problème « La capture de la caméra échoue », montrant visuellement le problème qui apparaît à l'exécution du code et aidant à expliquer la cause précise de l'échec de la capture caméra.](../../en/images/d65-01.png)

Vérifiez si le câble de la caméra du poignet est desserré, en particulier l'extrémité proche de la caméra — ce connecteur est très sujet aux mauvais contacts

## La caméra se déconnecte

![Cette image montre l'interface d'exécution du code /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py. En haut, elle affiche l'heure, l'ID de processus et d'autres informations ; en dessous figurent des chemins de code et des messages d'erreur tels que /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py et « INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected. ». L'élément clé est « raise TimeoutError » et « TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True. », indiquant que la capture caméra a échoué. L'image se rapporte au problème « La capture de la caméra échoue », montrant visuellement l'erreur.](../../en/images/d65-02.png)

Redémarrez la ligne de commande

## Problème de communication avec le servo 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![Cette image montre ce qui suit.](../../en/images/d65-03.png)

Le correctif : passez chaque `num_retry` du code situé à `lerobot/src/lerobot/motors/motors_bus.py` à 99, en particulier celui de la ligne qui provoque l'erreur

![Cette image montre le contenu du fichier de code `motors_bus.py` dans le projet LeRobot. La méthode `write` de la classe `MotorsBusABC` est mise en évidence, avec la variable `num_retry` modifiée à `99`. L'image se rapporte à la section « Problème de communication avec le servo 1 », correspondant au correctif consistant à passer chaque `num_retry` du code situé à `lerobot/src/lerobot/motors/motors_bus.py` à 99, en particulier celui de la ligne qui provoque l'erreur.](../../en/images/d65-04.png)

## Problème de communication avec le servo 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![Cette image montre une session en ligne de commande dans le terminal zsh sous macOS. Le terminal affiche plusieurs chemins de fichiers et numéros de lignes de code, tels que `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`. La ligne 587 du fichier `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` lève une `ConnectionError`, signalant un échec d'écriture de `Torque_Enable` sur l'id=1 sans paquet de statut. L'image se rapporte au contenu « Problème de communication avec le servo 2 », montrant visuellement l'exécution du code au moment de l'erreur.](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![Cette image montre une session en ligne de commande dans le terminal zsh sous macOS. Le terminal affiche plusieurs chemins de fichiers et numéros de lignes de code, tels que `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`. Ici, `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

Solution : recalibrez le bras robotisé
