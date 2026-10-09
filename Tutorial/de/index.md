[English](../en/index.md) | [简体中文](../zh-hans/index.md) | [繁體中文](../zh-hant/index.md) | Deutsch | [Español](../es/index.md) | [Français](../fr/index.md) | [Italiano](../it/index.md) | [日本語](../ja/index.md) | [한국어](../ko/index.md) | [Português (BR)](../pt-br/index.md) | [Português (PT)](../pt-pt/index.md)

# Inhalt

## **Klicken Sie auf die beiden Symbole oben links, um die vollständige Kapitelliste einzublenden**

![Das Bild zeigt ein Symbol aus einem Punkt und drei parallelen Linien. Dieses Symbol erscheint in einem Dokument, das LeRobot vorstellt; im Kontext wird LeRobot als HuggingFaces quelloffenes Software-Framework für verkörperte intelligente Roboter beschrieben, das die Hürden für Datenerfassung, Algorithmustraining und Inferenz-Deployment für bestärkendes Lernen und Imitationslernen (VLA) senkt, wobei der Schwerpunkt auf dem Imitationslernen (VLA) liegt. Das Symbol steht möglicherweise für das LeRobot-Software-Framework oder eine verwandte Funktion.](../en/images/d02-01.png)

![Das Bild zeigt ein Play-Button-Symbol, ein weißes Dreieck, in der unteren linken Ecke des Bildausschnitts. Dieses Symbol gehört zur LeRobot-Vorstellung des Dokuments; LeRobot ist HuggingFaces quelloffenes Software-Framework für verkörperte intelligente Roboter, das die Hürden für Datenerfassung, Algorithmustraining und Inferenz-Deployment für bestärkendes Lernen und Imitationslernen (VLA) senkt, wobei der Schwerpunkt auf dem Imitationslernen (VLA) liegt. Das Symbol weist möglicherweise auf Video- oder Demo-Inhalte hin, die Nutzern das LeRobot-Material näherbringen.](../en/images/d02-02.png)

![Das Bild zeigt den Text „Speedrunning Embodied Intelligence VLA“ vor einem hellen Farbverlauf-Hintergrund. Im Bildausschnitt hält eine Hand einen weißen Gegenstand, während eine andere Hand einen Roboterarm mit roter Verkabelung bedient. In der unteren rechten Ecke erscheint eine Sprechblase mit der Aufschrift „Grab!“. Das Bild gehört zur LeRobot-Vorstellung des Dokuments, eines Software-Frameworks für verkörperte intelligente Roboter, das die Hürden für das Imitationslernen (VLA) senkt; es soll vermutlich den Einsatz von VLA in der Robotermanipulation und seine Rolle beim Imitationslernen veranschaulichen.](../en/images/d02-03.png)

## Was ist verkörperte Intelligenz?

Intelligenz mit einem Körper. Sie verbindet KI mit verschiedenen physischen Hardware-Einheiten, wie zum Beispiel:

Vierbeinige Roboterhunde, zweibeinige humanoide Roboter, radgetriebene Roboter, Drohnen, selbstfahrende Autos

## Was ist LeRobot?

LeRobot ist HuggingFaces quelloffenes `Software-Framework für verkörperte intelligente Roboter`

GitHub-Adresse: https://github.com/huggingface/lerobot

Es senkt die Hürden für **Datenerfassung, Algorithmustraining und Inferenz-Deployment** für bestärkendes Lernen und **Imitationslernen (VLA)**, wobei **Imitationslernen (VLA)** im Mittelpunkt steht

- Welche Roboter lassen sich mit LeRobot entwickeln?

Vom Roboterarm SO-ARM 101 in der Tausende-Yuan-Klasse und dem LeKiwi-Wagen über den AgileX-Piper-Arm in der Zehntausende-Yuan-Klasse, den StarAI-Arm von Huaxinjing und die Hope-JR-Fingerhand bis hin zum humanoiden Unitree-G1-Roboter in der Hunderttausende-Yuan-Klasse. LeRobot hat sich zum Standard für Datenerfassung und Algorithmustraining in der Branche der verkörperten Intelligenz entwickelt.

Sie können auch Ihren eigenen Roboter an das LeRobot-Framework anpassen.

- LeRobot-Datensätze und -Modelle

LeRobot definiert ein eigenes Datensatzformat für das Imitationslernen. Sie können alle öffentlichen Datensätze und Modelle auf HuggingFace ansehen, verwenden, herunterladen und damit trainieren; außerdem können Sie Ihre eigenen Datensätze auf HuggingFace hochladen.

## Was ist der Roboterarm SO-ARM 101?

Dieses Tutorial verwendet den Roboterarm SO-ARM 101 als Beispiel; er nutzt 3D-gedruckte Strukturteile und Feetech-Servos und ist damit sehr kostengünstig.

Das ist ein Körper für verkörperte Intelligenz, den sich selbst ein armer Student leisten kann, und einer der von LeRobot offiziell empfohlenen Körper.

Der Arm besteht aus zwei Armen: einem Leader-Arm und einem Follower-Arm. Jeder Arm hat 5 Freiheitsgrade plus 1 Freiheitsgrad für den Greifer.

## Welche Computer-Konfiguration brauche ich

Ein gewöhnlicher Windows-Laptop bewältigt alles bis zum Training.

Ein gewöhnlicher Mac bewältigt alles.

Ein Ubuntu-Rechner mit einer NVIDIA-GPU bewältigt alles.

In diesem Tutorial nutzen wir eine [Cloud-GPU-Plattform](https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1) zum Trainieren der Modelle, sodass Ihr eigener Computer keine High-End-Konfiguration benötigt.

## Was ist **Imitationslernen und VLA**?

Menschen führen den Roboter, um etwas vorzumachen, und erfassen dabei einen Datensatz. Dieser Datensatz wird dann zum Trainieren eines Imitationslern-Algorithmus verwendet, der schließlich auf dem Roboter eingesetzt wird und ihn menschliche Aktionen autonom nachahmen und auf die reale Umgebung übertragen lässt. Teleoperation oder Fernsteuerung ist dafür nicht nötig.

Im obigen Video zieht beispielsweise ein Mensch den SO-ARM-Roboterarm, um einen Flusskrebs zu greifen, ihn in Gewürz zu tauchen und in heißes Öl fallen zu lassen; am Ende führt der Arm diese Aktion selbstständig aus. Selbst mit einem neuen Flusskrebs kann er jederzeit reagieren und die Aktion abschließen.

Imitationslernen hat auch einen hochmodernen, modischen Namen: VLA (Vision-Language-Action-Großmodell). Das ist zugleich das Forschungsfeld der verkörperten Intelligenz, das sich derzeit am schnellsten entwickelt, die heißesten Investitionen anzieht, den schärfsten Wettbewerb zwischen China und den USA erlebt, das blühendste Open-Source-Ökosystem genießt, starke Medienaufmerksamkeit erregt und unzählige Master- und Doktoranden anzieht.

Die Algorithmen, die LeRobot hauptsächlich adaptiert, sind solche des Imitationslernens, darunter ACT, Diffusion Policy, SmolVLA, Pi0, Pi0.5, Wall-OSS und weitere.

Das Imitationslernen in diesem Tutorial ist ausschließlich VLA.
