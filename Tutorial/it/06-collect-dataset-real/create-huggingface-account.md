[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | Italiano | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# Registrare un account Hugging Face (opzionale)

## Configurare un mirror HuggingFace basato in Cina

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Add this at the end of the file
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# Output
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# Add this at the end of the file
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Output
# https://hf-mirror.com
```



## Creare un token

https://huggingface.co/settings/tokens

![L'immagine mostra l'interfaccia della piattaforma Hugging Face, con l'avatar dell'utente e l'area delle informazioni del profilo a sinistra e i contenuti di modelli e dataset a destra. A destra, una freccia rossa punta all'opzione "Access Tokens", situata sotto "Settings". Il contesto menziona che dopo aver creato un token è necessario usare i tasti su/giù per selezionare e incollare la chiave; questa immagine presenta dove si trova "Access Tokens" sulla piattaforma, è collegata al passaggio di annotazione del token dopo averlo creato ed è l'interfaccia per impostare le autorizzazioni pertinenti dopo aver creato un token.](../../en/images/d34-01.png)

![L'immagine mostra la pagina Access Tokens della piattaforma Hugging Face. Nella barra di navigazione sinistra, l'opzione "Access Tokens" è selezionata. A destra sono mostrate le informazioni sui User Access Tokens, tra cui nome, valore, data dell'ultimo aggiornamento, data dell'ultimo utilizzo e autorizzazioni. In alto a destra c'è un pulsante "Create new token" evidenziato con una freccia rossa. Questa immagine è collegata alla sezione "Creare un token", presenta dove creare un nuovo token e aiuta gli utenti a comprendere la pagina specifica per creare un token su Hugging Face.](../../en/images/d34-02.png)

![Questa immagine mostra l'interfaccia per creare un nuovo token di accesso sulla piattaforma Hugging Face, con il titolo della pagina "Create new Access Token". Occorre impostare tre voci: selezionare il tipo di token denominato "Write", impostare il nome su "so-arm101" e poi fare clic sul pulsante "Create token". Queste operazioni sono contrassegnate con riquadri rossi e i numeri 1, 2 e 3 per guidare gli utenti nella creazione di un token con permesso di scrittura. Questo corrisponde ai passaggi per creare un token, un passaggio chiave per ottenere la chiave necessaria a collegare Hugging Face.](../../en/images/d34-03.png)

![Questa immagine è la pagina di salvataggio dell'Access Token di un account Hugging Face; il suo contenuto principale è un promemoria a salvare adeguatamente il valore del token, perché dopo aver chiuso il popup non sarà più visibile e, se perso, dovrà essere ricreato. La pagina mostra la chiave di accesso generata hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx, con il nome so-arm101 e permesso di scrittura. C'è un pulsante "Copy" puntato da una freccia rossa ed evidenziato con un riquadro rosso, usato per copiare il token, e un pulsante "Done" in basso a destra per terminare l'operazione corrente. Questa immagine corrisponde al passaggio di annotazione o collegamento del token dell'account Hugging Face.](../../en/images/d34-04.png)

## Annotare il token

Ad esempio, il mio è:

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## Collegare il token

```Shell
hf auth login

hf auth whoami
```

![L'immagine mostra l'accesso con un token Hugging Face dalla riga di comando. Dopo aver inserito il comando "hf auth login", appare il prompt "? How would you like to log in?" e viene mostrata l'opzione "Paste an access token". Questo è collegato al passaggio "Collegare il token" e indica che dopo aver selezionato e incollato la chiave con i tasti su/giù, la schermata di accesso chiede come desideri effettuare l'accesso, momento in cui puoi scegliere di incollare un token di accesso per accedere e completare il collegamento del token Hugging Face.](../../en/images/d34-05.png)

> Usa i tasti su/giù per selezionare e incollare la chiave

![Questa immagine mostra l'operazione su un account Hugging Face dalla riga di comando, con un riquadro rosso che evidenzia che il token attualmente attivo è "so-arm101-upload", che è stato salvato nel percorso specificato. La riga di comando ha effettuato la disconnessione e poi nuovamente l'accesso; il sistema ha segnalato che per accedere a Hugging Face è necessario un token, e dopo aver incollato correttamente il token ha mostrato il permesso del token come write, quindi ha completato il salvataggio e infine ha visualizzato le informazioni sul token attualmente attivo. Questo contenuto corrisponde al passaggio "Collegare il token".](../../en/images/d34-06.png)

> Schermata di successo

## Creare un repository di dataset

<grid>
<column width-ratio="0.434605">
![Questa immagine mostra un menu a tendina nell'interfaccia di Hugging Face; in alto l'utente connesso è mostrato come "juxi-admin", e il menu elenca diverse opzioni di funzione, tra cui new model, new space e new bucket. L'opzione evidenziata con un riquadro rosso è "New Dataset", che corrisponde al passaggio "Creare un repository di dataset". Questa opzione è il punto di accesso per creare un repository di dataset, attraverso cui gli utenti possono completare la creazione di un repository di dataset.](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![L'immagine mostra l'interfaccia per creare un repository di dataset su Hugging Face. Sotto "Dataset name" è inserito il valore "so-arm101", "License" è impostata su "apache-2.0" ed è selezionata l'opzione "Public", che significa che chiunque può visualizzare questo Dataset e solo tu puoi fare commit. Questa immagine è collegata al passaggio "Creare un repository di dataset", mostra una delle schermate di configurazione e aiuta gli utenti a comprendere le informazioni chiave da inserire durante la creazione.](../../en/images/d34-08.png)
</column>
</grid>

![L'immagine mostra la pagina del dataset "so - arm101" sulla piattaforma Hugging Face. In alto c'è una barra di ricerca e una barra di navigazione che dà accesso a sezioni come Models e Datasets. Al centro mostra le informazioni sul dataset, tra cui License apache - 2.0 e una dimensione del file di 2.53 kB. In basso c'è una sezione "Getting started with your dataset" che invita ad aggiungere metadati e a completare la scheda del dataset per migliorarne la reperibilità, e offre l'opzione di modificare la scheda del dataset. A destra ci sono i pulsanti "Copy to bucket" e "Edit dataset card", e un registro dei download dei file del dataset. Questa immagine è collegata alla creazione di un repository di dataset e mostra l'interfaccia di gestione del dataset.](../../en/images/d34-09.png)
