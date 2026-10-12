[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | Français | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# Configurer un environnement d'entraînement sur GPU cloud

## Désactiver le proxy réseau de votre ordinateur

Sinon, vous ne pourrez peut-être pas ouvrir la ligne de commande Jupyter

## Se connecter à la plateforme de GPU cloud Featurize

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## Démarrer une instance GPU cloud

<grid>
<column width-ratio="0.597692">
![Cette image est l'écran de sélection des instances GPU cloud sur la plateforme Featurize ; elle présente principalement les options d'instances GPU cloud aux configurations différentes. L'option encadrée en rouge est une instance GPU cloud RTX 5090, indiquée comme 2.0 disponibles au tarif à la demande de 3 CNY/heure, avec 32.0 GB de mémoire GPU, un processeur AMD EPYC 9354 à 38 cœurs et 128 GB de RAM. En dessous se trouvent les boutons « Start Using » et « Reserve », avec une flèche rouge pointant vers « Start Using », ce qui correspond aux indications « Démarrer une instance GPU cloud » du document.](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![Cette image montre l'écran de sélection de l'image sur la plateforme Featurize. On y voit un onglet « Select Image », avec trois sous-onglets en dessous : « Official Images », « My Images » et « Popular Images ». Sous l'onglet « Official Images », l'image PyTorch 2 est mise en évidence par un cadre et une flèche rouges ; elle pèse 14.5 GB, a été utilisée 19,001 fois et porte le libellé « Official ». L'image est étroitement liée au contexte, qui décrit le fait de cliquer sur « JupyterLab » et de téléverser le code et les jeux de données après le démarrage d'une instance GPU cloud ; cette capture d'écran illustre l'option d'image officielle lors de l'étape de sélection de l'image, utilisée pour la configuration ultérieure de l'environnement.](../../en/images/d45-02.png)
</column>
</grid>

![Cette image montre la console d'une instance GPU cloud, correspondant à l'étape « Démarrer une instance GPU cloud » du document et présentant les opérations disponibles une fois l'instance démarrée. Elle affiche la configuration d'une instance RTX 5090, incluant les paramètres de GPU, de CPU, de mémoire et de disque, ainsi que la durée de location, le mode de facturation et le coût de l'instance. Une flèche rouge et un cadre rouge mettent en évidence le bouton « Open Workspace », invitant l'utilisateur à cliquer dessus afin de passer aux opérations JupyterLab et au téléversement du code et du jeu de données.](../../en/images/d45-03.png)

![Cette image montre l'interface JupyterLab. À gauche se trouve la zone de gestion des fichiers, avec les onglets « Instances », « Files » et « Terminal », l'onglet « Files » actuellement sélectionné. À droite se trouve la zone Launcher, qui propose des options telles que Notebook, Console et Python 3 (ipykernel). Une flèche rouge sur l'image pointe vers l'onglet « Files » dans la zone de gestion des fichiers à gauche, soulignant cet emplacement et faisant écho au contexte — « cliquez sur JupyterLab ci-dessous ; il y a un bouton de téléversement dans le coin supérieur gauche où vous pouvez téléverser du code et des jeux de données » — pour guider l'utilisateur dans les opérations liées aux fichiers au sein de JupyterLab.](../../en/images/d45-04.png)

> Cliquez sur « JupyterLab » ci-dessous ; il y a un bouton de téléversement dans le coin supérieur gauche où vous pouvez téléverser du code et des jeux de données

## Installer et configurer l'environnement

```Shell
conda create -y -n lerobot python=3.12
conda activate lerobot
conda install ffmpeg=7.1.1 -c conda-forge -y
# git clone https://github.com/Seeed-Projects/lerobot.git ~/work/Lerobot
git clone https://github.com/huggingface/lerobot.git
cd lerobot
pip install -e ".[pi]"
pip install wandb --upgrade
# export HF_ENDPOINT=https://hf-mirror.com
hf auth login

# Pas besoin d'installer si vous ne téléversez pas vers HuggingFace et n'avez pas besoin de wandb
```

> Si `training` manquait lors de l'installation du modèle, vous devez l'installer en plus
> 
> `pip install -e ".[training]"`

## Se connecter à wandb

```Shell
wandb login
Copiez-collez la clé API, puis appuyez sur Entrée
```

![Cette image montre l'écran de connexion à wandb pour le projet LeRobot, enregistrant les détails du processus de connexion. Elle débute par le lancement de la connexion wandb, qui invite l'utilisateur à consulter une adresse donnée pour trouver la clé API, puis à coller la clé et appuyer sur Entrée pour la soumettre. Elle montre aussi qu'aucun fichier netrc n'a été trouvé et que la clé API est ajoutée au chemin netrc correspondant, après quoi la connexion se termine et l'utilisateur connecté apparaît comme tommyzihao, accompagné d'une commande pour forcer une nouvelle connexion. Cette image correspond à l'étape « Se connecter à wandb » et présente le processus et le résultat de la connexion.](../../en/images/d45-05.png)

## Monter le jeu de données

```Shell
Copiez la commande de téléchargement de l'instance, quelque chose comme :
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

Le jeu de données apparaît dans le répertoire `~`

## Ajuster la fréquence de sauvegarde des poids (facultatif)

Ouvrez `lerobot/src/lerobot/configs/train.py`

Passez save_freq de 20_000 à 5_000

Ainsi, vous obtenez les fichiers de poids du modèle plus tôt dans l'entraînement
