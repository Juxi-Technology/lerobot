[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | Français | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# Collecter un jeu de données par démonstration — Handshake 200

## Créer un dépôt de jeu de données sur HuggingFace

https://huggingface.co/new-dataset

![L'image montre l'interface de création d'un nouveau dépôt de jeu de données sur HuggingFace. « Owner » est affiché comme TommyZihao, le nom du jeu de données est « lerobot_zihao_dataset_shake200 », la « License » est définie sur mit, et le type de jeu de données est « Public », visible par tout le monde alors que seuls le propriétaire du jeu de données ou les membres de l'organisation peuvent committer. En dessous, il est précisé qu'après avoir créé le jeu de données, vous pouvez téléverser des fichiers via l'interface web ou git, et un bouton « Create dataset » figure en bas. Cette image concerne le contenu sur la création d'un dépôt de jeu de données sur HuggingFace et montre l'interface de l'opération de création de jeu de données.](../../en/images/d37-01.png)

## Supprimer tout jeu de données existant portant le même nom (le cas échéant)

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Collecte du jeu de données Shake200

Une caméra, collecte d'un jeu de données - ordinateur Mac

```Shell
lerobot-record \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true \
    --dataset.repo_id=Tommymy/lerobot_my_dataset_shake200 \
    --dataset.num_episodes=200 \
    --dataset.single_task="Shanke Hands" \
    --dataset.push_to_hub=false \
    --dataset.episode_time_s=12 \
    --dataset.reset_time_s=1
```

## Pendant la collecte

<grid>
<column width-ratio="0.508765">
![L'image montre l'interface du terminal pendant la collecte d'un jeu de données sur un Mac. Elle affiche la sortie de SvtInfo() et SvtInfo(), notamment le numéro de version, le compilateur et l'architecture. Elle présente aussi les paramètres de configuration de SvtConfig(), tels que la largeur, la hauteur, la fréquence d'images et le preset. En dessous se trouve une sortie marquée « INFO » et « INFO 0 », comme « Starting second pass: moving the moving atom to the beginning of the file ». Cette image concerne le contenu « Pendant la collecte » et présente visuellement la configuration et les informations affichées dans le terminal pendant la collecte.](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![L'image montre la sortie du terminal pendant la collecte d'un jeu de données avec le script Open_Duck_Mini_Runtime_2 sur un Mac. Elle affiche des paramètres de configuration de l'encodage vidéo SVT et autres, tels que la taille du gop et le type de key - frame, et présente la version de l'encodeur vidéo et la date de compilation. En dessous figurent des journaux de fichiers MP4, tels que « Starting second pass: moving the moov atom to the beginning of the file ». Cette image concerne le flux de travail de collecte de jeux de données et présente visuellement la rétroaction du terminal pendant la collecte.](../../en/images/d37-03.png)
</column>
</grid>

Commandes par les touches fléchées du clavier :  
→ (Flèche droite) Terminer l'épisode en cours de manière anticipée ; passer à l'épisode suivant.  
← (Flèche gauche) Annuler l'épisode en cours ; l'enregistrer à nouveau.  
ESC, arrêter immédiatement, encoder la vidéo et téléverser le jeu de données.

## Collecte terminée — Répertoire d'enregistrement du jeu de données

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
