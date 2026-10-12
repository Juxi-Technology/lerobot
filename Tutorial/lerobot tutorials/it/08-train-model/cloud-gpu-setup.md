[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | [Español](../../es/08-train-model/cloud-gpu-setup.md) | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | Italiano | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# Configurare un ambiente di addestramento su cloud GPU

## Disattivare il proxy di rete del computer

Altrimenti potresti non riuscire ad aprire la riga di comando di Jupyter

## Accedere alla piattaforma cloud GPU Featurize

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## Avviare un'istanza cloud GPU

<grid>
<column width-ratio="0.597692">
![Questa immagine mostra la schermata di selezione delle istanze cloud GPU sulla piattaforma Featurize, con le varie opzioni di istanza cloud GPU dalle configurazioni diverse. L'opzione evidenziata dal riquadro rosso è un'istanza cloud GPU RTX 5090, indicata come disponibile in 2.0 unità a un prezzo a consumo di 3 CNY/ora, con 32.0 GB di memoria GPU, un processore AMD EPYC 9354 a 38 core e 128 GB di RAM. Sotto compaiono i pulsanti "Start Using" e "Reserve", con una freccia rossa che punta a "Start Using", in coerenza con l'indicazione "Avviare un'istanza cloud GPU" riportata nel documento.](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![Questa immagine mostra la schermata di selezione dell'immagine sulla piattaforma Featurize. È visibile la scheda "Select Image", con tre sotto-schede al di sotto: "Official Images", "My Images" e "Popular Images". Nella scheda "Official Images", l'immagine PyTorch 2 è evidenziata da un riquadro e da una freccia rossi; è di 14.5 GB, è stata usata 19.001 volte ed è contrassegnata come "Official". L'immagine è strettamente legata al contesto, che descrive come, dopo aver avviato un'istanza cloud GPU, si faccia clic su "JupyterLab" e si carichino codice e dataset; questo screenshot mostra l'opzione dell'immagine ufficiale nella fase di selezione dell'immagine, usata per la successiva configurazione dell'ambiente.](../../en/images/d45-02.png)
</column>
</grid>

![Questa immagine mostra la console di un'istanza cloud GPU, corrispondente al passaggio "Avviare un'istanza cloud GPU" del documento, e illustra le operazioni disponibili dopo l'avvio dell'istanza. Sono visualizzate la configurazione di un'istanza RTX 5090, con i parametri di GPU, CPU, memoria e disco, nonché la durata del noleggio, il metodo di fatturazione e il costo. Una freccia e un riquadro rossi evidenziano il pulsante "Open Workspace", invitando l'utente a farvi clic per passare alle operazioni in JupyterLab e caricare codice e dataset.](../../en/images/d45-03.png)

![Questa immagine mostra l'interfaccia di JupyterLab. A sinistra si trova l'area di gestione dei file, con le schede "Instances", "Files" e "Terminal", e la scheda "Files" attualmente selezionata. A destra si trova l'area Launcher, che offre opzioni come Notebook, Console e Python 3 (ipykernel). Una freccia rossa punta alla scheda "Files" nell'area di gestione file a sinistra, evidenziando quella posizione e riecheggiando il contesto — "fai clic su JupyterLab qui sotto; nell'angolo in alto a sinistra c'è un pulsante di caricamento con cui puoi caricare codice e dataset" — per guidare l'utente nelle operazioni sui file in JupyterLab.](../../en/images/d45-04.png)

> Fai clic su "JupyterLab" qui sotto; nell'angolo in alto a sinistra c'è un pulsante di caricamento con cui puoi caricare codice e dataset

## Installare e configurare l'ambiente

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

# Salta l'installazione se non carichi su HuggingFace e non ti serve wandb
```

> Se al momento dell'installazione del modello mancava `training`, devi installarlo a parte
> 
> `pip install -e ".[training]"`

## Accedere a wandb

```Shell
wandb login
Copy and paste the API Key, then press Enter
```

![Questa immagine mostra la schermata di accesso a wandb per il progetto LeRobot, documentando i dettagli della procedura di login. Inizia avviando il login di wandb, invitando l'utente a visitare un determinato URL per trovare la API key e a incollarla premendo Invio per inviarla. Mostra inoltre che non è stato trovato alcun file netrc e che la API key viene aggiunta al percorso del file netrc corrispondente; al termine il login si completa e l'utente connesso risulta tommyzihao, insieme a un comando per forzare un nuovo login. Questa immagine corrisponde al passaggio "Accedere a wandb" e presenta lo svolgimento e il risultato del login.](../../en/images/d45-05.png)

## Montare il dataset

```Shell
Copy the instance download command, something like:
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

Il dataset compare nella directory `~`

## Regolare la frequenza di salvataggio dei pesi (facoltativo)

Apri `lerobot/src/lerobot/configs/train.py`

Cambia save_freq da 20_000 a 5_000

In questo modo ottieni prima i file dei pesi del modello durante l'addestramento
