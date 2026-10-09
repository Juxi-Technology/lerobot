[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | Français | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# Créer un compte Hugging Face (facultatif)

## Configurer un miroir HuggingFace basé en Chine

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Ajouter ceci à la fin du fichier
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# Sortie
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# Ajouter ceci à la fin du fichier
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Sortie
# https://hf-mirror.com
```



## Créer un jeton

https://huggingface.co/settings/tokens

![L'image montre l'interface de la plateforme Hugging Face, avec l'avatar et la zone d'informations de profil de l'utilisateur à gauche et le contenu des modèles et jeux de données à droite. À droite, une flèche rouge pointe vers l'option « Access Tokens », située sous « Settings ». Le contexte mentionne qu'après avoir créé un jeton, vous devez utiliser les touches haut/bas pour sélectionner et coller la clé ; cette image présente visuellement l'emplacement de « Access Tokens » sur la plateforme, concerne l'étape consistant à noter le jeton après l'avoir créé, et constitue l'interface pour définir les autorisations pertinentes après la création d'un jeton.](../../en/images/d34-01.png)

![L'image montre la page Access Tokens de la plateforme Hugging Face. Dans la barre de navigation de gauche, l'option « Access Tokens » est sélectionnée. À droite figurent les informations User Access Tokens, notamment le nom, la valeur, la date de dernière actualisation, la date de dernière utilisation et les autorisations. En haut à droite se trouve un bouton « Create new token » mis en évidence par une flèche rouge. Cette image concerne la section « Créer un jeton » et présente visuellement l'endroit où créer un nouveau jeton, ce qui aide à comprendre la page concrète de création d'un jeton sur Hugging Face.](../../en/images/d34-02.png)

![Cette image montre l'interface de création d'un nouveau jeton d'accès sur la plateforme Hugging Face, avec le titre de page « Create new Access Token ». Trois éléments doivent être définis : sélectionner le type de jeton nommé « Write », définir le nom sur « so-arm101 », puis cliquer sur le bouton « Create token ». Ces opérations sont marquées par des cadres rouges et les chiffres 1, 2 et 3 pour guider l'utilisateur dans la création d'un jeton avec droit d'écriture. Cela correspond aux étapes de création d'un jeton, une étape clé pour obtenir la clé nécessaire à l'association de Hugging Face.](../../en/images/d34-03.png)

![Cette image est la page d'enregistrement du jeton d'accès d'un compte Hugging Face ; son contenu central est un rappel d'enregistrer soigneusement la valeur du jeton, car après la fermeture de la fenêtre contextuelle, elle ne peut plus être consultée et, en cas de perte, doit être recréée. La page affiche la clé d'accès générée hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx, avec le nom so-arm101 et le droit d'écriture. Un bouton « Copy » est pointé par une flèche rouge et mis en évidence par un cadre rouge, utilisé pour copier le jeton, et un bouton « Done » figure en bas à droite pour terminer l'opération en cours. Cette image correspond à l'étape consistant à noter ou associer le jeton du compte Hugging Face.](../../en/images/d34-04.png)

## Noter le jeton

Par exemple, le mien est :

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## Associer le jeton

```Shell
hf auth login

hf auth whoami
```

![L'image montre la connexion avec un jeton Hugging Face en ligne de commande. Après avoir saisi la commande « hf auth login », l'invite « ? How would you like to log in? » apparaît et l'option « Paste an access token » est affichée. Cela concerne l'étape « Associer le jeton » et indique qu'après avoir sélectionné et collé la clé avec les touches haut/bas, l'écran de connexion demande comment vous souhaitez vous connecter, auquel cas vous pouvez choisir de coller un jeton d'accès pour vous connecter et terminer l'association du jeton Hugging Face.](../../en/images/d34-05.png)

> Utilisez les touches haut/bas pour sélectionner et coller la clé

![Cette image montre l'utilisation d'un compte Hugging Face en ligne de commande, avec un cadre rouge mettant en évidence que le jeton actuellement actif est « so-arm101-upload », qui a été enregistré dans le chemin indiqué. La ligne de commande s'est déconnectée puis reconnectée ; le système a indiqué que la connexion à Hugging Face nécessite un jeton, et après avoir collé le jeton avec succès, il a affiché l'autorisation du jeton comme write, puis a terminé l'enregistrement, et a finalement affiché les informations du jeton actuellement actif. Ce contenu correspond à l'étape « Associer le jeton ».](../../en/images/d34-06.png)

> Écran de réussite

## Créer un dépôt de jeu de données

<grid>
<column width-ratio="0.434605">
![Cette image montre un menu déroulant dans l'interface Hugging Face ; en haut, l'utilisateur connecté est affiché comme « juxi-admin », et le menu liste plusieurs options de fonction, dont new model, new space et new bucket. L'option mise en évidence par un cadre rouge est « New Dataset », correspondant à l'étape « Créer un dépôt de jeu de données ». Cette option est le point d'entrée pour créer un dépôt de jeu de données, par lequel les utilisateurs peuvent mener à bien la création d'un dépôt de jeu de données.](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![L'image montre l'interface de création d'un dépôt de jeu de données sur Hugging Face. Sous « Dataset name », la valeur « so-arm101 » est saisie, « License » est définie sur « apache-2.0 », et l'option « Public » est sélectionnée, ce qui signifie que tout le monde peut voir ce jeu de données et que vous seul pouvez committer. Cette image concerne l'étape « Créer un dépôt de jeu de données », montre l'un des écrans de configuration et aide à comprendre les informations clés à saisir lors de la création.](../../en/images/d34-08.png)
</column>
</grid>

![L'image montre la page du jeu de données « so - arm101 » sur la plateforme Hugging Face. En haut figurent une barre de recherche et une barre de navigation donnant accès à des sections telles que Models et Datasets. Au milieu sont affichées les informations du jeu de données, notamment License apache - 2.0 et une taille de fichier de 2.53 kB. En dessous se trouve une section « Getting started with your dataset » qui vous invite à ajouter des métadonnées et à compléter la fiche du jeu de données pour améliorer sa visibilité, et propose l'option de modifier la fiche du jeu de données. À droite figurent les boutons « Copy to bucket » et « Edit dataset card », ainsi qu'un historique de téléchargement des fichiers du jeu de données. Cette image concerne la création d'un dépôt de jeu de données et montre l'interface de gestion du jeu de données.](../../en/images/d34-09.png)
