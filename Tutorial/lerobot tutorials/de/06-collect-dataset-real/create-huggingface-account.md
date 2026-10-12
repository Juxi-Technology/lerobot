[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | Deutsch | [Español](../../es/06-collect-dataset-real/create-huggingface-account.md) | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# Ein Hugging-Face-Konto registrieren (optional)

## Einen in China gehosteten HuggingFace-Mirror einrichten

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Dies am Ende der Datei hinzufügen
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# Ausgabe
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# Dies am Ende der Datei hinzufügen
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Ausgabe
# https://hf-mirror.com
```



## Einen Token erstellen

https://huggingface.co/settings/tokens

![Das Bild zeigt die Oberfläche der Hugging Face-Plattform, mit dem Avatar und dem Profilinformationsbereich des Nutzers links und Modell- und Datensatzinhalten rechts. Rechts weist ein roter Pfeil auf die Option „Access Tokens" hin, die sich unter „Settings" befindet. Im Kontext wird erwähnt, dass Sie nach dem Erstellen eines Tokens mit den Pfeiltasten nach oben/unten den Schlüssel auswählen und einfügen müssen; dieses Bild zeigt, wo sich „Access Tokens" auf der Plattform befindet, gehört zum Schritt des Notierens des Tokens nach dem Erstellen und ist die Oberfläche zum Festlegen der relevanten Berechtigungen nach dem Erstellen eines Tokens.](../../en/images/d34-01.png)

![Das Bild zeigt die Seite „Access Tokens" der Hugging Face-Plattform. In der linken Navigationsleiste ist die Option „Access Tokens" ausgewählt. Auf der rechten Seite werden Informationen zu User Access Tokens angezeigt, einschließlich Name, Wert, Datum der letzten Aktualisierung, Datum der letzten Verwendung und Berechtigungen. Oben rechts befindet sich eine Schaltfläche „Create new token", die mit einem roten Pfeil hervorgehoben ist. Dieses Bild gehört zum Abschnitt „Einen Token erstellen" und zeigt, wo ein neuer Token erstellt wird, und hilft Anwendern, die konkrete Seite zum Erstellen eines Tokens auf Hugging Face zu verstehen.](../../en/images/d34-02.png)

![Dieses Bild zeigt die Oberfläche zum Erstellen eines neuen Access Tokens auf der Hugging Face-Plattform, mit dem Seitentitel „Create new Access Token". Drei Punkte müssen festgelegt werden: den Tokentyp mit dem Namen „Write" auswählen, den Namen auf „so-arm101" setzen und dann auf die Schaltfläche „Create token" klicken. Diese Vorgänge sind mit roten Rahmen und den Zahlen 1, 2 und 3 markiert, um Anwender beim Erstellen eines Tokens mit Schreibberechtigung anzuleiten. Dies entspricht den Schritten zum Erstellen eines Tokens, einem entscheidenden Schritt zum Erhalt des Schlüssels, der für die Bindung an Hugging Face benötigt wird.](../../en/images/d34-03.png)

![Dieses Bild ist die Seite zum Speichern des Access Tokens eines Hugging Face-Kontos; ihr Kerninhalt ist die Erinnerung, den Tokenwert sorgfältig zu sichern, da er nach dem Schließen des Popups nicht mehr angezeigt werden kann und bei Verlust neu erstellt werden muss. Die Seite zeigt den erzeugten Zugriffsschlüssel hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx, mit dem Namen so-arm101 und Schreibberechtigung. Es gibt eine Schaltfläche „Copy", auf die ein roter Pfeil zeigt und die rot umrandet ist, zum Kopieren des Tokens, sowie unten rechts eine Schaltfläche „Done", um den aktuellen Vorgang abzuschließen. Dieses Bild entspricht dem Schritt des Notierens oder Bindens des Hugging Face-Konto-Tokens.](../../en/images/d34-04.png)

## Den Token notieren

Meiner lautet zum Beispiel:

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## Den Token binden

```Shell
hf auth login

hf auth whoami
```

![Das Bild zeigt die Anmeldung mit einem Hugging Face-Token auf der Kommandozeile. Nach Eingabe des Befehls „hf auth login" erscheint die Aufforderung „? How would you like to log in?" und die Option „Paste an access token" wird angezeigt. Dies bezieht sich auf den Schritt „Den Token binden" und zeigt, dass nach dem Auswählen und Einfügen des Schlüssels mit den Pfeiltasten nach oben/unten der Anmeldebildschirm fragt, wie Sie sich anmelden möchten, woraufhin Sie ein Access Token zum Anmelden einfügen und die Bindung des Hugging Face-Tokens abschließen können.](../../en/images/d34-05.png)

> Mit den Pfeiltasten nach oben/unten den Schlüssel auswählen und einfügen

![Dieses Bild zeigt die Bedienung eines Hugging Face-Kontos auf der Kommandozeile, wobei ein roter Rahmen hervorhebt, dass der aktuell aktive Token „so-arm101-upload" ist, der im angegebenen Pfad gespeichert wurde. Die Kommandozeile meldete sich ab und dann wieder an; das System wies darauf hin, dass für die Anmeldung bei Hugging Face ein Token erforderlich ist, und nach dem erfolgreichen Einfügen des Tokens zeigte es die Tokenberechtigung als write an, schloss dann das Speichern ab und zeigte schließlich die Informationen zum aktuell aktiven Token. Dieser Inhalt entspricht dem Schritt „Den Token binden".](../../en/images/d34-06.png)

> Erfolgsbildschirm

## Ein Dataset-Repo erstellen

<grid>
<column width-ratio="0.434605">
![Dieses Bild zeigt ein Dropdown-Menü in der Hugging Face-Oberfläche; oben wird der angemeldete Nutzer als „juxi-admin" angezeigt, und das Menü listet mehrere Funktionsoptionen auf, darunter neues Modell, neuer Space und neuer Bucket. Die mit einem roten Rahmen hervorgehobene Option ist „New Dataset", entsprechend dem Schritt „Ein Dataset-Repo erstellen". Diese Option ist der Einstiegspunkt zum Erstellen eines Datensatz-Repositories, über den Anwender die Erstellung eines Datensatz-Repositories abschließen können.](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![Das Bild zeigt die Oberfläche zum Erstellen eines Dataset-Repos auf Hugging Face. Unter „Dataset name" ist der Wert „so-arm101" eingegeben, „License" ist auf „apache-2.0" gesetzt und die Option „Public" ist ausgewählt, was bedeutet, dass jeder diesen Datensatz sehen kann, aber nur Sie committen können. Dieses Bild gehört zum Schritt „Ein Dataset-Repo erstellen", zeigt einen der Einrichtungsbildschirme und hilft Anwendern, die wichtigsten auszufüllenden Informationen beim Erstellen zu verstehen.](../../en/images/d34-08.png)
</column>
</grid>

![Das Bild zeigt die Seite des Datensatzes „so - arm101" auf der Hugging Face-Plattform. Oben befinden sich eine Suchleiste und eine Navigationsleiste, die Zugang zu Bereichen wie Models und Datasets bieten. In der Mitte werden Datensatzinformationen angezeigt, darunter License apache - 2.0 und eine Dateigröße von 2.53 kB. Darunter gibt es einen Abschnitt „Getting started with your dataset", der Sie auffordert, Metadaten hinzuzufügen und die Datensatzkarte zu vervollständigen, um die Auffindbarkeit zu verbessern, und die Option bietet, die Datensatzkarte zu bearbeiten. Rechts befinden sich die Schaltflächen „Copy to bucket" und „Edit dataset card" sowie eine Aufzeichnung des Herunterladens von Datensatzdateien. Dieses Bild gehört zum Erstellen eines Dataset-Repos und zeigt die Datensatzverwaltungsoberfläche.](../../en/images/d34-09.png)
