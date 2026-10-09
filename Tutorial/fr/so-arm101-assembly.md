[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | Français | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>Tutoriel d'assemblage du kit de bras robotique SO-ARM101</title>

<callout emoji="💡">
Remarque : passez ce tutoriel si vous avez un bras pré-assemblé
</callout>

## Pièces imprimées en 3D du bras Follower

![Cette image montre les pièces imprimées en 3D du bras Follower nécessaires pour assembler le bras robotique SO-ARM101, toutes les pièces en plastique PLA blanc disposées sur une surface à veinage de bois clair. Les pièces comprennent des connecteurs de formes diverses, une structure fourchue avec une grille, une pièce de type base percée, un bras de support fourchu de forme particulière, etc., ce qui correspond au point du tutoriel selon lequel l'extrémité du bras Follower est une pince. Ces pièces sont les éléments moulés de base du bras Follower et sont les objets manipulés lors de l'étape de retrait des supports, correspondant directement aux pièces imprimées en 3D du bras Follower présentées dans le tutoriel.](../en/images/d09-01.jpg)

## Pièces imprimées en 3D du bras Leader

![L'image montre les pièces imprimées en 3D du bras robotique SO-ARM101. Diverses pièces imprimées en 3D noires sont soigneusement disposées dans le cadre, avec des lignes bleues sur les bords de certaines pièces. Ces pièces comprennent des éléments structurels des bras Leader et Follower, tels que la pince, la poignée et la gâchette, ainsi que des connecteurs. L'image correspond à la section « Pièces imprimées en 3D du bras Leader » du document et présente visuellement l'aspect des pièces imprimées en 3D, fournissant une référence pour les étapes ultérieures de retrait des supports résiduels et de distinction des servomoteurs.](../en/images/d09-02.jpg)

Les bras Leader et Follower sont très similaires ; seule l'extrémité diffère

Le Leader possède une poignée et une gâchette ; le Follower possède une pince

## Retirer les supports résiduels des pièces imprimées en 3D

Vérifiez chaque trou, ouverture, fente et grille, en particulier les cinq trous qui ressemblent à la tuile « cinq points » du mahjong

Cette étape est très importante ; sinon, vous ne pourrez pas visser les vis par la suite

## Distinguer les quatre servomoteurs

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">Grande taille</td><td vertical-align="middle">Petite taille</td><td vertical-align="middle">Tension (V)</td><td vertical-align="middle">Rapport de réduction</td><td vertical-align="middle">Articulation du bras</td><td vertical-align="middle">Quantité</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Toutes les articulations du Follower</td><td vertical-align="middle">6</td></tr></tbody></table>

> Le rapport de réduction est le rapport « vitesse du moteur : vitesse de l'arbre de sortie du servomoteur » ; par exemple, 1:345 signifie que le moteur tourne 345 fois pour que l'arbre de sortie tourne une fois.
> 
> Un rapport de réduction élevé multiplie le couple par le train d'engrenages, ce qui permet d'entraîner une charge plus lourde (comme le bras Follower)
> 
> Mais en même temps, l'arbre de sortie tourne plus lentement (car il est « démultiplié »)
> 
> Déplacer l'articulation à la main demande aussi plus d'effort

Voici les modèles et rapports de réduction de tous les servomoteurs de ce projet ; les parties soulignées correspondent à leurs numéros

![L'image montre les modèles, tensions et rapports de réduction des servomoteurs utilisés dans le bras. À gauche se trouve le bras Leader, avec deux modèles, C046 (7.4 V, 1:147) et C044 (7.4 V, 1:191) ; à droite se trouve le bras Follower, avec deux modèles, C001 (7.4 V, 1:345) et C047 (12 V, 1:345). L'image est étroitement liée au contexte, qui présente en détail les modèles, tensions et rapports de réduction des servomoteurs des bras Leader et Follower ; cette image illustre visuellement ces chiffres clés pour aider les lecteurs à mieux comprendre la configuration des servomoteurs.](../en/images/d09-03.png)

![L'image montre quatre boîtes de servomoteurs étiquetées « STS3215 ». Chaque boîte est imprimée avec le mot « SPECIFICATION » et comporte des paramètres tels que le couple, la vitesse et les dimensions, par exemple un couple de 9.2kg·cm/127.98oz·in(6V). Le STS3215-C001 a un couple de 12.5kg·cm/173.88oz·in(6V), et le STS3215-C046 a un couple de 16kg·cm/220.58oz·in(7V). Ces servomoteurs sont le modèle utilisé pour toutes les articulations du bras Follower, correspondant au bras Follower présenté dans le document, et servent à l'installation des servomoteurs dans les étapes d'assemblage ultérieures.](../en/images/d09-04.jpg)

## Distinguer les deux adaptateurs d'alimentation

Adaptateur d'alimentation 5 V 6 A 30 W : alimente les servomoteurs 7.4 V (bras Leader), noir

Adaptateur d'alimentation 12 V 5 A 60 W : alimente les servomoteurs 12 V (bras Follower), blanc

## Télécharger l'outil de débogage des servomoteurs Feetech

### PC Windows

https://gitee.com/ftservo/fddebug

Téléchargez [`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z), décompressez-le, et lancez le programme exe contenu à l'intérieur

### Ubuntu et Mac (l'archive inclut un tutoriel)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![Cette image est une illustration auxiliaire du tutoriel d'assemblage du kit de bras robotique SO-ARM101, correspondant à la section sur la distinction des adaptateurs d'alimentation. Elle montre deux modèles de servomoteurs et leurs positions de montage, STS3215-C001 et STS3215-C018, et étiquette également des servomoteurs tels que STS3215-C004, correspondant aux différentes articulations du bras. La figure liste aussi les paramètres de ces deux servomoteurs, y compris la vitesse de rotation, le couple de décrochage, la précision du servomoteur, les fonctions de protection et le retour de paramètres, fournissant une référence pour le choix et l'installation des servomoteurs lors de l'assemblage du bras.](../en/images/d09-05.jpg)

**Version Pro : le bras Leader utilise un adaptateur d'alimentation 5V6A, et le bras Follower un adaptateur 12V5A**

La configuration des ID des servomoteurs, l'étalonnage d'angle des servomoteurs et l'assemblage doivent être faits au préalable ; reportez-vous au [tutoriel d'assemblage officiel](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# Étape 1 : définir les ID des servomoteurs et installer les palonniers (sauf le servomoteur 5)

<grid>
<column width-ratio="0.500000">
![L'image montre l'interface de l'outil de débogage hôte Feetech. L'interface comporte trois onglets, « Debug », « Program » et « Upgrade », avec « Program » sélectionné. Informations clés : 1. Dans les paramètres de communication, le numéro de port est COM6 et le débit en bauds est 1000000 ; 2. Dans les opérations sur les servomoteurs, l'écriture synchrone, l'écriture asynchrone et la sortie de couple sont toutes cochées ; 3. Dans le retour des servomoteurs, des paramètres tels que la tension, le courant, la température et la position affichent tous 0 ; 4. Dans la recherche de servomoteurs, l'id 1 est sélectionné, modèle ST53215. Cette image se rapporte aux opérations de débogage décrites ci-dessus, telles que la définition des ID de servomoteurs et l'installation des palonniers, et présente l'interface de l'outil de débogage.](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![L'image montre l'interface de l'outil de débogage hôte Feetech, utilisée pour définir les ID des servomoteurs. L'interface comporte trois onglets, « Debug », « Program » et « Upgrade », avec « Program » sélectionné. Dans la zone « Center calibration », le numéro d'ID est 4, avec un bouton « Save » à droite. Le côté gauche de l'interface affiche l'ID du servomoteur, le modèle et d'autres informations. Cette image se rapporte au contenu « Étape 1 : définir les ID des servomoteurs et installer les palonniers (sauf le servomoteur 5) » du document et présente l'interface de l'opération de configuration des ID, montrant visuellement où le numéro d'ID est défini.](../en/images/d09-07.png)
</column>
</grid>

1. Ouvrez l'outil de débogage hôte Feetech, sélectionnez le port COM, réglez le débit en bauds à un million, et cliquez sur « Open »
2. Cliquez sur « Search » ; une fois « STS3215 » apparu, cliquez sur « Stop » puis sur « STS3215 »
3. Sélectionnez « Debug » en haut ; vous pouvez faire glisser le curseur pour faire tourner le servomoteur, ou cliquer sur « Scan » pour le faire aller et venir. Confirmez que le servomoteur fonctionne normalement
4. Sélectionnez « Program » en haut
5. Cliquez sur « Center calibration » pour définir la position actuelle de l'arbre de rotation du servomoteur comme centre (0-4095)
6. Cliquez sur « ID », définissez le numéro d'ID du servomoteur correspondant dans le coin inférieur droit, et cliquez sur « Save ». Notez que le numéro est en chiffres arabes simples, sans lettres.
7. Débranchez le câble reliant le servomoteur à la carte de contrôle
8. Branchez le câble du servomoteur sur le servomoteur

Le servomoteur 1 reçoit deux câbles ; les autres servomoteurs n'en reçoivent qu'un seul pour l'instant

![L'image montre l'installation des servomoteurs lors de l'assemblage du kit de bras SO-ARM101. Le cadre contient le bras Follower et le bras Leader, le bras Follower numéroté 123456 et le bras Leader numéroté 123456. Les servomoteurs sont étiquetés avec des rapports de réduction de 1:345, 1:191 et 1:147. En dessous se trouve la carte de contrôle, reliée à deux câbles, un blanc et un noir. Cette image se rapporte aux étapes d'assemblage ci-dessus et présente visuellement les positions de montage et les numéros des servomoteurs, aidant l'opérateur à associer précisément les servomoteurs à la carte de contrôle.](../en/images/d09-08.png)

<callout emoji="💡">
Encore une fois : assurez-vous que l'ID d'articulation et le rapport de réduction de chaque servomoteur correspondent exactement au **SO-ARM101**.
</callout>

Chaque moteur du bus possède un ID unique. Les moteurs neufs ont généralement un ID par défaut de `1`. Pour garantir la communication entre les moteurs et le contrôleur, nous devons d'abord définir un ID unique pour chaque moteur. En outre, la vitesse de transmission des données sur le bus est déterminée par le débit en bauds. Pour communiquer entre eux, le contrôleur et tous les moteurs doivent être configurés avec le même débit en bauds ; les servomoteurs de ce bras utilisent un débit en bauds de 100000.

Pour ce faire, nous devons d'abord connecter le contrôleur à chaque moteur l'un après l'autre afin de les configurer. Comme nous écrivons ces paramètres dans la zone non volatile de la mémoire interne du moteur (EEPROM), cela ne doit être fait qu'une seule fois.

Si vous réutilisez des moteurs provenant d'un autre robot, vous devrez peut-être aussi effectuer cette étape, car les ID et les débits en bauds peuvent ne pas correspondre.

La vidéo ci-dessous montre la séquence d'étapes pour définir les ID des moteurs.

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Utilisez l'outil hôte des servomoteurs Feetech pour définir les ID et étalonner le centre. Les ID vont de 1 à 6 !

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu et Mac

<callout emoji="💡">
Si vous avez besoin de l'outil hôte des servomoteurs Feetech, reportez-vous à l'[outil de débogage des servomoteurs Feetech](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb) ci-dessus
</callout>

Commencez par réaliser la configuration de l'environnement en suivant la page [installation officielle de LeRobot](https://huggingface.co/docs/lerobot/installation)

<callout emoji="💡">
N'oubliez pas d'activer l'environnement virtuel et d'entrer dans le répertoire src/lerobot correspondant
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. Trouvez le port USB du bras. Pour trouver le bon port de chaque bras, exécutez deux fois le script utilitaire ::

```Plain Text
lerobot-find-port
```

Exemple de sortie lors de l'identification du port du bras Leader (par exemple `/dev/tty.usbmodem575E0031751` sur un Mac, ou éventuellement `/dev/ttyACM0` sous Linux) :

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

Exemple de sortie lors de l'identification du port du bras Follower (par exemple `/dev/tty.usbmodem575E0032081`, ou éventuellement `/dev/ttyACM1` sous Linux) :

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
N'oubliez pas de débrancher le connecteur USB, sinon le port ne peut pas être détecté.
</callout>

2. Connectez le PC à la carte de pilotage des servomoteurs du bras Follower avec un câble USB et mettez-le sous tension. Puis exécutez la commande suivante. Remplacez --robot.port=/dev/ttyACM0 dans la commande par le port que vous avez trouvé. Par exemple, si le port que vous avez trouvé est /dev/ttyACM1, remplacez-le par --robot.port=/dev/ttyACM1

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

Vous verrez la sortie suivante.

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

En suivant les instructions, connectez le servomoteur de la pince. Assurez-vous qu'il est le seul servomoteur connecté à la carte de pilotage et que ce servomoteur n'est pas encore connecté à un autre servomoteur. Après avoir appuyé sur **[Entrée]**, le script définit automatiquement l'ID et le débit en bauds de ce servomoteur. Les ID vont de 6 à 1 !

Ensuite, vous devriez voir ce qui suit :

```Python
'gripper' motor id set to 6
```

Puis la sortie suivante est :

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**Remarque** Répétez ce qui précède pour chaque servomoteur, en suivant les instructions.
Comme pour les servomoteurs précédents, assurez-vous qu'il est le seul servomoteur connecté à la carte de pilotage et que le servomoteur lui-même n'est connecté à aucun autre servomoteur.
</callout>

Avant d'appuyer sur **Entrée** chaque fois, vérifiez bien vos connexions de câbles. Par exemple, le câble d'alimentation peut se débrancher lors de la manipulation de la carte de circuit imprimé.

Lorsque vous avez terminé toutes les étapes, le script se termine automatiquement et les servomoteurs sont prêts à l'emploi. Vous pouvez maintenant connecter tour à tour le connecteur 3 broches de chaque servomoteur, et connecter le câble du premier servomoteur (le servomoteur « shoulder pan » d'ID 1) à la carte de pilotage. La carte de pilotage peut maintenant être montée sur la base du bras.

Répétez les mêmes étapes pour le bras Leader.

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# Étape 2 : assemblage

<callout emoji="💡">
- Les étapes d'assemblage du bras Follower sont essentiellement les mêmes que pour le bras Leader. La seule différence est qu'après l'étape 12, l'effecteur terminal (pince et poignée) est installé différemment.
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
Installer la carte de pilotage des servomoteurs : montez d'abord les 4 entretoises en laiton, puis fixez la carte de pilotage avec quatre vis M2.5\*8
</callout>

<grid>
<column width-ratio="0.525947">
![Installer les quatre entretoises en laiton](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![Fixer la carte de pilotage des servomoteurs avec les vis M2.5*8](../en/images/d09-10.webp)
</column>
</grid>

![Monter sur le bras et câbler l'ensemble](../en/images/d09-11.png)

**Version Pro : le bras Leader noir utilise un adaptateur d'alimentation 5V6A, et le bras Follower blanc un adaptateur 12V5A**







# Configurer les ID de servomoteurs et l'étalonnage du centre dans l'interface web

https://bambot.org/feetech.js?lang=zh

1. Saisissez 0 ou 1 selon le modèle du servomoteur, puis cliquez sur « Connect »

![L'image montre l'interface « Connect » du tutoriel d'assemblage du kit de bras. À gauche de l'interface se trouve le mot « Connect », et à droite une liste déroulante « Baud rate » réglée sur 1,000,000 bps (Index 0), et une zone de saisie « Protocol end (0=STS/SMS, 1=SCS) » réglée sur 0, avec un encadré rouge autour du nombre « 1 » à côté de la zone de saisie. En dessous se trouve un bouton vert « Connect », avec un encadré rouge autour du nombre « 2 » à côté. Le bas affiche « Status: Disconnected ». Cette image correspond au contenu ci-dessus, « Saisissez 0 ou 1 selon le modèle du servomoteur, puis cliquez sur "Connect" », et présente visuellement les réglages de l'opération de connexion.](../en/images/d09-12.png)

2. Scannez les servomoteurs d'ID 1\~6 ; utilisez FOUND dans les résultats du scan pour confirmer le servomoteur d'ID correspondant. Par exemple, dans l'image, le servomoteur d'ID 1 a été trouvé

![L'image montre l'interface de l'étape « Scan servos » du tutoriel d'assemblage du kit de bras SO-ARM101. En haut de l'interface se trouvent les zones de saisie « Start ID » et « End ID », actuellement avec l'ID de début 1 et l'ID de fin 6. En dessous se trouve un bouton « Start scan ». Dans les résultats du scan, le scan des ID 1 à 6 ne trouve aucun servomoteur, signalant « Exception: No status packet! Error code: 0 ». Cette image est étroitement liée au contexte et présente visuellement l'interface et les résultats lors du scan des servomoteurs, aidant les utilisateurs à comprendre l'état du scan.](../en/images/d09-13.png)

3. Configuration des ID et étalonnage du centre

① Réglez la saisie de l'ID du servomoteur courant sur l'ID du servomoteur scanné

② Saisissez un nombre dans « ID management » et cliquez sur « Change ID » pour définir l'ID

③ Étalonnage du centre (le centre du servomoteur STS3215 est 2047, celui du servomoteur SCS0009 est 511)

Servomoteur STS : saisissez 2047 dans « Position control » et cliquez sur « Set »

Servomoteur SCS : saisissez 511 dans « Position control » et cliquez sur « Set »

![L'image montre une interface de contrôle d'un servomoteur unique. L'ID du servomoteur courant est 1 ; après avoir saisi le nombre 1 sous ID management et cliqué sur « Change ID », le message « Success: ID changed to 1 » apparaît. Sous Position Control, la valeur est 2047, et cliquer sur le bouton « Set » l'applique. Cette image se rapporte au contexte « configuration des ID et étalonnage du centre » et présente visuellement l'interface de l'opération de configuration des ID, aidant les utilisateurs à comprendre comment saisir un nombre sous « ID management » pour définir l'ID et comment saisir la valeur du centre sous « Position control » puis cliquer sur « Set » pour terminer.](../en/images/d09-14.png)
