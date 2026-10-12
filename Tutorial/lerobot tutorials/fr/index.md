[English](../en/index.md) | [简体中文](../zh-hans/index.md) | [繁體中文](../zh-hant/index.md) | [Deutsch](../de/index.md) | [Español](../es/index.md) | Français | [Italiano](../it/index.md) | [日本語](../ja/index.md) | [한국어](../ko/index.md) | [Português (BR)](../pt-br/index.md) | [Português (PT)](../pt-pt/index.md)

# Sommaire

## **Cliquez sur les deux icônes dans le coin supérieur gauche pour déplier la liste complète des chapitres**

![L'image montre une icône composée d'un point et de trois lignes parallèles. Cette icône apparaît dans un document qui présente LeRobot, dont le contexte décrit LeRobot comme le framework logiciel open source de robots intelligents incarnés de HuggingFace, qui abaisse la barrière de la collecte de données, de l'entraînement d'algorithmes et du déploiement d'inférences pour l'apprentissage par renforcement et l'apprentissage par imitation (VLA), l'apprentissage par imitation (VLA) étant l'aspect principal. Cette icône peut représenter le framework logiciel LeRobot ou une fonctionnalité associée.](../en/images/d02-01.png)

![L'image montre une icône en forme de bouton lecture, un triangle blanc, située dans le coin inférieur gauche du cadre. Cette icône se rapporte à la présentation de LeRobot dans le document, qui est le framework logiciel open source de robots intelligents incarnés de HuggingFace, abaissant la barrière de la collecte de données, de l'entraînement d'algorithmes et du déploiement d'inférences pour l'apprentissage par renforcement et l'apprentissage par imitation (VLA), l'apprentissage par imitation (VLA) étant l'aspect principal. Cette icône peut indiquer du contenu vidéo ou de démonstration pour aider les utilisateurs à comprendre le contenu LeRobot.](../en/images/d02-02.png)

![L'image montre le texte « Speedrunning Embodied Intelligence VLA » sur un fond dégradé clair. Dans le cadre, une main tient un objet blanc tandis qu'une autre main actionne un bras robotique avec un câblage rouge. Une bulle de dialogue affichant « Grab! » apparaît dans le coin inférieur droit. L'image se rapporte à la présentation de LeRobot dans le document, un framework logiciel de robots intelligents incarnés qui abaisse la barrière de l'apprentissage par imitation (VLA) ; cette image vise probablement à illustrer visuellement l'utilisation du VLA dans la manipulation robotique et son rôle dans l'apprentissage par imitation.](../en/images/d02-03.png)

## Qu'est-ce que l'intelligence incarnée ?

L'intelligence dotée d'un corps. Elle relie l'IA à diverses entités matérielles physiques, telles que :

Les robots quadrupèdes, les robots humanoïdes bipèdes, les robots à roues et jambes, les drones, les voitures autonomes

## Qu'est-ce que LeRobot ?

LeRobot est le `framework logiciel open source de robots intelligents incarnés` de HuggingFace

Adresse GitHub : https://github.com/huggingface/lerobot

Il abaisse la barrière de la **collecte de données, de l'entraînement d'algorithmes et du déploiement d'inférences** pour l'apprentissage par renforcement et l'**apprentissage par imitation (VLA)**, l'**apprentissage par imitation (VLA)** étant l'aspect principal

- Quels robots peut-on développer avec LeRobot ?

Du bras robotique SO-ARM 101 à quelques milliers de yuans, au chariot LeKiwi, jusqu'au bras AgileX piper à plusieurs dizaines de milliers de yuans, au bras Huaxinjing StarAI et à la main dextre Hope-JR, et jusqu'au robot humanoïde Unitree G1 à plusieurs centaines de milliers de yuans. LeRobot est devenu la référence pour la collecte de données et l'entraînement d'algorithmes dans l'industrie de l'intelligence incarnée.

Vous pouvez également adapter votre propre robot au framework LeRobot.

- Jeux de données et modèles LeRobot

LeRobot définit son propre format de jeu de données d'apprentissage par imitation. Vous pouvez consulter, utiliser, télécharger et entraîner tous les jeux de données et modèles publics sur HuggingFace, et vous pouvez aussi téléverser vos propres jeux de données sur HuggingFace.

## Qu'est-ce que le bras robotique SO-ARM 101 ?

Ce tutoriel prend pour exemple le bras robotique SO-ARM 101 ; il utilise des pièces structurelles imprimées en 3D et des servomoteurs Feetech, à un coût très faible.

C'est un corps d'intelligence incarnée même un étudiant sans moyens peut s'offrir, et c'est l'un des corps officiellement recommandés par LeRobot.

Le bras se compose de deux bras : un bras Leader et un bras Follower. Chaque bras possède 5 degrés de liberté plus 1 degré de liberté pour la pince.

## Quelle configuration informatique me faut-il

Un ordinateur portable Windows ordinaire peut tout gérer jusqu'à l'entraînement.

Un Mac ordinaire peut tout gérer.

Une machine Ubuntu dotée d'un GPU NVIDIA peut tout gérer.

Dans ce tutoriel, nous utilisons une [plateforme GPU dans le cloud](https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1) pour entraîner les modèles, votre propre ordinateur n'a donc pas besoin d'une configuration haut de gamme.

## Qu'est-ce que l'**apprentissage par imitation et le VLA** ?

Un humain fait bouger le robot pour montrer la tâche et collecter un jeu de données. Ce jeu de données sert ensuite à entraîner un algorithme d'apprentissage par imitation, qui est finalement déployé sur le robot, lui permettant de reproduire les actions humaines de façon autonome et de généraliser à l'environnement réel. Aucune téléopération ni commande à distance n'est nécessaire.

Par exemple, dans la vidéo ci-dessus, un humain fait bouger le bras robotique SO-ARM pour attraper une écrevisse, la tremper dans l'assaisonnement et la déposer dans l'huile chaude, et le bras finit par exécuter cette action tout seul. Même avec une nouvelle écrevisse, il peut réagir et accomplir l'action à tout moment.

L'apprentissage par imitation porte aussi un nom à la pointe de la mode : VLA (grand modèle Vision-Langage-Action). C'est également le domaine de recherche en intelligence incarnée qui se développe le plus vite aujourd'hui, qui attire les investissements les plus enthousiastes, qui connaît la concurrence Chine-États-Unis la plus féroce, qui bénéficie de l'écosystème open source le plus florissant, qui suscite l'attention médiatique la plus intense et qui attire d'innombrables étudiants de master et de doctorat.

Les algorithmes que LeRobot adapte principalement sont ceux d'apprentissage par imitation, comme ACT, Diffusion Policy, SmolVLA, Pi0, Pi0.5, Wall-OSS et d'autres.

L'apprentissage par imitation de ce tutoriel est exclusivement du VLA.
