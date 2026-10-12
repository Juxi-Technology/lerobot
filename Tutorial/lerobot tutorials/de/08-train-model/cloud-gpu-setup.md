[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | Deutsch | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# Einrichten einer Cloud-GPU-Trainingsumgebung

## Netzwerk-Proxy des Computers deaktivieren

Andernfalls lässt sich die Jupyter-Kommandozeile möglicherweise nicht öffnen

## Bei der Cloud-GPU-Plattform Featurize anmelden

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## Cloud-GPU-Instanz starten

<grid>
<column width-ratio="0.597692">
![Dieses Bild zeigt die Auswahlmaske für Cloud-GPU-Instanzen auf der Featurize-Plattform, die in erster Linie Cloud-GPU-Instanzoptionen mit unterschiedlichen Konfigurationen zeigt. Die rot umrahmte Option ist eine RTX-5090-Cloud-GPU-Instanz, ausgewiesen als 2.0 verfügbar zum Pay-as-you-go-Tarif von 3 CNY/Stunde, mit 32,0 GB GPU-Speicher, einem 38-Kern-AMD-EPYC-9354-Prozessor und 128 GB RAM. Darunter befinden sich die Schaltflächen „Start Using" und „Reserve", wobei ein roter Pfeil auf „Start Using" zeigt, was der Anleitung „Cloud-GPU-Instanz starten" im Dokument entspricht.](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![Dieses Bild zeigt die Image-Auswahlmaske auf der Featurize-Plattform. Zu sehen ist ein Reiter „Select Image" mit drei Unterreitern darunter: „Official Images", „My Images" und „Popular Images". Unter dem Reiter „Official Images" ist das PyTorch-2-Image mit einem roten Rahmen und Pfeil hervorgehoben; es ist 14,5 GB groß, wurde 19.001 Mal verwendet und trägt die Kennzeichnung „Official". Das Image steht in engem Bezug zum Kontext, der das Anklicken von „JupyterLab" und das Hochladen von Code und Datensätzen nach dem Start einer Cloud-GPU-Instanz beschreibt; dieser Screenshot zeigt die Option des offiziellen Images im Schritt der Image-Auswahl, die für die anschließende Einrichtung und Konfiguration der Umgebung verwendet wird.](../../en/images/d45-02.png)
</column>
</grid>

![Dieses Bild zeigt die Konsole einer Cloud-GPU-Instanz und entspricht dem Schritt „Cloud-GPU-Instanz starten" im Dokument; es zeigt die nach dem Start der Instanz verfügbaren Aktionen. Dargestellt ist die Konfiguration einer RTX-5090-Instanz mit den Parametern für GPU, CPU, Speicher und Festplatte sowie Mietdauer, Abrechnungsmethode und Kosten der Instanz. Ein roter Pfeil und ein roter Rahmen heben die Schaltfläche „Open Workspace" hervor und fordern den Nutzer auf, darauf zu klicken, um zu den JupyterLab-Aktionen überzugehen und den Code sowie den Datensatz hochzuladen.](../../en/images/d45-03.png)

![Dieses Bild zeigt die JupyterLab-Oberfläche. Links befindet sich der Dateiverwaltungsbereich mit den Reitern „Instances", „Files" und „Terminal", wobei der Reiter „Files" derzeit ausgewählt ist. Rechts befindet sich der Launcher-Bereich mit Optionen wie Notebook, Console und Python 3 (ipykernel). Ein roter Pfeil im Bild zeigt auf den Reiter „Files" im linken Dateiverwaltungsbereich und hebt diese Stelle hervor, passend zum Kontext — „klicken Sie unten auf JupyterLab; in der oberen linken Ecke gibt es eine Upload-Schaltfläche, über die Sie Code und Datensätze hochladen können" —, um den Nutzer durch die dateibezogenen Vorgänge in JupyterLab zu führen.](../../en/images/d45-04.png)

> Klicken Sie unten auf „JupyterLab"; in der oberen linken Ecke gibt es eine Upload-Schaltfläche, über die Sie Code und Datensätze hochladen können

## Umgebung installieren und konfigurieren

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

# Überspringen Sie die Installation, wenn Sie nicht zu HuggingFace hochladen und kein wandb benötigen
```

> Falls `training` bei der Installation des Modells gefehlt hat, müssen Sie es zusätzlich installieren
> 
> `pip install -e ".[training]"`

## Bei wandb anmelden

```Shell
wandb login
Copy and paste the API Key, then press Enter
```

![Dieses Bild zeigt die wandb-Anmeldemaske für das LeRobot-Projekt und dokumentiert die Details des Anmeldevorgangs. Zunächst wird die wandb-Anmeldung gestartet, die den Nutzer auffordert, eine angegebene URL aufzurufen, um den API-Key zu finden, und dann den Key einzufügen und mit der Eingabetaste zu bestätigen. Außerdem wird angezeigt, dass keine netrc-Datei gefunden wurde und dass der API-Key in den entsprechenden netrc-Dateipfad eingetragen wird; danach ist die Anmeldung abgeschlossen und der angemeldete Nutzer wird als tommyzihao angezeigt, zusammen mit einem Befehl zum Erzwingen einer erneuten Anmeldung. Dieses Bild entspricht dem Schritt „Bei wandb anmelden" und zeigt den Ablauf und das Ergebnis der Anmeldung.](../../en/images/d45-05.png)

## Datensatz einbinden

```Shell
Copy the instance download command, something like:
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

Der Datensatz erscheint im Verzeichnis `~`

## Häufigkeit des Speicherns der Gewichte anpassen (optional)

Öffnen Sie `lerobot/src/lerobot/configs/train.py`

Ändern Sie save_freq von 20_000 auf 5_000

So erhalten Sie die Modellgewicht-Dateien bereits früher im Training
