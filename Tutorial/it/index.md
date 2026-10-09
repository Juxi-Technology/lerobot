[English](../en/index.md) | [简体中文](../zh-hans/index.md) | [繁體中文](../zh-hant/index.md) | [Deutsch](../de/index.md) | [Español](../es/index.md) | [Français](../fr/index.md) | Italiano | [日本語](../ja/index.md) | [한국어](../ko/index.md) | [Português (BR)](../pt-br/index.md) | [Português (PT)](../pt-pt/index.md)

# Contenuti

## **Fai clic sulle due icone nell'angolo in alto a sinistra per espandere l'elenco completo dei capitoli**

![L'immagine mostra un'icona composta da un punto e tre linee parallele. Questa icona compare in un documento che presenta LeRobot, il cui contesto descrive LeRobot come il framework software open source di HuggingFace per robot intelligenti embodied che abbassa la barriera per la raccolta dati, l'addestramento degli algoritmi e il deployment dell'inferenza nel reinforcement learning e nell'imitation learning (VLA), con l'imitation learning (VLA) come focus principale. Questa icona potrebbe rappresentare il framework software LeRobot o una funzionalità correlata.](../en/images/d02-01.png)

![L'immagine mostra un'icona a forma di pulsante di riproduzione, un triangolo bianco, situata nell'angolo in basso a sinistra della cornice. Questa icona è legata alla presentazione di LeRobot nel documento, che è il framework software open source di HuggingFace per robot intelligenti embodied che abbassa la barriera per la raccolta dati, l'addestramento degli algoritmi e il deployment dell'inferenza nel reinforcement learning e nell'imitation learning (VLALA), con l'imitation learning (VLA) come focus principale. Questa icona potrebbe indicare contenuti video o dimostrativi per aiutare gli utenti a comprendere il materiale su LeRobot.](../en/images/d02-02.png)

![L'immagine mostra il testo "Speedrunning Embodied Intelligence VLA" su uno sfondo chiaro a gradiente. Nella cornice, una mano tiene un oggetto bianco mentre un'altra mano aziona un braccio robotico con cablaggi rossi. Un fumetto con la scritta "Grab!" compare nell'angolo in basso a destra. L'immagine è legata alla presentazione di LeRobot nel documento, un framework software open source per robot intelligenti embodied che abbassa la barriera dell'imitation learning (VLA)); questa figura potrebbe essere pensata per presentare visivamente l'uso del VLA nella manipolazione robotica e il suo ruolo nell'imitation learning.](../en/images/d02-03.png)

## Che cos'è l'intelligenza embodied?

Intelligenza dotata di un corpo. Collega l'IA a diverse entità hardware fisiche, come:

Robot quadrupedi simili a cani, robot umanoidi bipedi, robot a ruote e zampe, droni, auto a guida autonoma

## Che cos'è LeRobot?

LeRobot è il `framework software open source per robot intelligenti embodied` di HuggingFace

Indirizzo GitHub: https://github.com/huggingface/lerobot

Abbassa la barriera per la **raccolta dati, l'addestramento degli algoritmi e il deployment dell'inferenza** nel reinforcement learning e nell'**imitation learning (VLA)**, con l'**imitation learning (VLA)** come focus principale

- Quali robot si possono sviluppare con LeRobot?

Dal braccio robotico SO-ARM 101 e dal carrello LeKiwi nella fascia dei mille yuan, fino al braccio AgileX piper nella fascia delle decine di migliaia di yuan, al braccio StarAI di Huaxinjing e alla mano dexterous Hope-JR, e ancora al robot umanoide Unitree G1 nella fascia delle centinaia di migliaia di yuan. LeRobot è diventato lo standard per la raccolta dati e l'addestramento degli algoritmi nel settore dell'intelligenza embodied.

Puoi anche adattare il tuo robot al framework LeRobot.

- Dataset e modelli LeRobot

LeRobot definisce un proprio formato di dataset per l'imitation learning. Puoi visualizzare, usare, scaricare e addestrare tutti i dataset e i modelli pubblici su HuggingFace, e puoi anche caricare i tuoi dataset su HuggingFace.

## Che cos'è il braccio robotico SO-ARM 101?

Questo tutorial prende come esempio il braccio robotico SO-ARM 101; utilizza parti strutturali stampate in 3D e servo Feetech, a un costo molto basso.

È un corpo per l'intelligenza embodied che anche uno studente senza grandi mezzi può permettersi, ed è uno dei corpi ufficialmente consigliati da LeRobot.

Il braccio è composto da due bracci: un braccio Leader e un braccio Follower. Ogni braccio ha 5 gradi di libertà più 1 grado di libertà del gripper.

## Quale configurazione del computer mi serve

Un normale portatile Windows gestisce tutto fino all'addestramento.

Un normale Mac gestisce tutto.

Una macchina Ubuntu con una GPU NVIDIA gestisce tutto.

In questo tutorial usiamo una [piattaforma GPU cloud](https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1) per addestrare i modelli, quindi il tuo computer non ha bisogno di una configurazione di fascia alta.

## Che cos'è l'**Imitation Learning e il VLA**?

Gli esseri umani trascinano il robot per dimostrare le azioni e raccogliere un dataset. Quel dataset viene poi usato per addestrare un algoritmo di imitation learning, che infine viene distribuito sul robot, permettendogli di imitare autonomamente le azioni umane e di generalizzare all'ambiente reale. Non servono teleoperazione né controllo remoto.

Ad esempio, nel video qui sopra, una persona trascina il braccio robotico SO-ARM per afferrare un gambero di fiume, intingerlo nel condimento e lasciarlo cadere nell'olio bollente, e alla fine il braccio esegue quest'azione da solo. Anche con un gambero nuovo, è in grado di reagire e completare l'azione in qualsiasi momento.

L'imitation learning ha anche un nome all'avanguardia e alla moda: VLA (modello di grandi dimensioni Vision-Language-Action). È anche il campo di ricerca sull'intelligenza embodied che oggi si sviluppa più rapidamente, che attira gli investimenti più caldi, che vede la competizione Cina-USA più accesa, che gode dell'ecosistema open source più florido, che richiama un'intensa attenzione mediatica e che attrae innumerevoli studenti di laurea magistrale e dottorato.

Gli algoritmi che LeRobot adatta principalmente sono quelli di imitation learning, come ACT, Diffusion Policy, SmolVLA, Pi0, Pi0.5, Wall-OSS e altri.

L'imitation learning di questo tutorial è esclusivamente VLA.
