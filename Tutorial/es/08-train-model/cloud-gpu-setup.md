[English](../../en/08-train-model/cloud-gpu-setup.md) | [简体中文](../../zh-hans/08-train-model/cloud-gpu-setup.md) | [繁體中文](../../zh-hant/08-train-model/cloud-gpu-setup.md) | [Deutsch](../../de/08-train-model/cloud-gpu-setup.md) | Español | [Français](../../fr/08-train-model/cloud-gpu-setup.md) | [Italiano](../../it/08-train-model/cloud-gpu-setup.md) | [日本語](../../ja/08-train-model/cloud-gpu-setup.md) | [한국어](../../ko/08-train-model/cloud-gpu-setup.md) | [Português (BR)](../../pt-br/08-train-model/cloud-gpu-setup.md) | [Português (PT)](../../pt-pt/08-train-model/cloud-gpu-setup.md)

# Configuración de un entorno de entrenamiento con GPU en la nube

## Desactiva el proxy de red del ordenador

De lo contrario, es posible que no puedas abrir la línea de comandos de Jupyter

## Inicia sesión en la plataforma de GPU en la nube Featurize

https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1

## Arranca una instancia de GPU en la nube

<grid>
<column width-ratio="0.597692">
![Esta imagen es la pantalla de selección de instancias de GPU en la nube de la plataforma Featurize; muestra principalmente opciones de instancias de GPU en la nube con distintas configuraciones. La opción marcada con un recuadro rojo es una instancia de GPU en la nube RTX 5090, listada como 2.0 disponible a una tarifa de pago por uso de 3 CNY/hora, con 32.0 GB de memoria de GPU, un procesador AMD EPYC 9354 de 38 núcleos y 128 GB de RAM. Debajo aparecen los botones «Start Using» y «Reserve», con una flecha roja que señala «Start Using», en consonancia con la indicación «Arranca una instancia de GPU en la nube» del documento.](../../en/images/d45-01.png)
</column>
<column width-ratio="0.402308">
![Esta imagen muestra la pantalla de selección de imágenes de la plataforma Featurize. Aparece una pestaña «Select Image», con tres subpestañas debajo: «Official Images», «My Images» y «Popular Images». Dentro de la pestaña «Official Images», la imagen de PyTorch 2 está resaltada con un recuadro y una flecha rojos; ocupa 14.5 GB, se ha usado 19.001 veces y está etiquetada como «Official». La imagen guarda una relación estrecha con el contexto, que describe hacer clic en «JupyterLab» y subir código y conjuntos de datos tras arrancar una instancia de GPU en la nube; esta captura muestra la opción de imagen oficial dentro del paso de selección de imagen, empleada para la posterior configuración del entorno.](../../en/images/d45-02.png)
</column>
</grid>

![Esta imagen muestra la consola de una instancia de GPU en la nube, correspondiente al paso «Arranca una instancia de GPU en la nube» del documento, y presenta las operaciones disponibles una vez arrancada la instancia. Se muestra la configuración de una instancia RTX 5090, con los parámetros de GPU, CPU, memoria y disco, así como la duración del alquiler, la modalidad de facturación y el coste de la instancia. Una flecha y un recuadro rojos resaltan el botón «Open Workspace», invitando al usuario a pulsarlo para pasar a las operaciones de JupyterLab y subir el código y el conjunto de datos.](../../en/images/d45-03.png)

![Esta imagen muestra la interfaz de JupyterLab. A la izquierda está el área de gestión de archivos, con las pestañas «Instances», «Files» y «Terminal», y la pestaña «Files» seleccionada en ese momento. A la derecha está el área del Launcher, con opciones como Notebook, Console y Python 3 (ipykernel). Una flecha roja señala la pestaña «Files» del área de gestión de archivos de la izquierda, destacando esa ubicación y haciéndose eco del contexto —«haz clic en JupyterLab que aparece abajo; en la esquina superior izquierda hay un botón de carga con el que puedes subir código y conjuntos de datos»—, guiando al usuario en las operaciones con archivos dentro de JupyterLab.](../../en/images/d45-04.png)

> Haz clic en «JupyterLab» que aparece abajo; en la esquina superior izquierda hay un botón de carga con el que puedes subir código y conjuntos de datos

## Instala y configura el entorno

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

# Skip the install if you are not uploading to HuggingFace and do not need wandb
```

> Si faltaba `training` al instalar el modelo, debes instalarlo aparte
> 
> `pip install -e ".[training]"`

## Inicia sesión en wandb

```Shell
wandb login
Copy and paste the API Key, then press Enter
```

![Esta imagen muestra la pantalla de inicio de sesión de wandb para el proyecto LeRobot y recoge los detalles del proceso de inicio de sesión. Comienza iniciando la sesión de wandb, pidiendo al usuario que visite una URL indicada para encontrar la API key y que pegue la clave y pulse Enter para enviarla. También muestra que no se encontró ningún archivo netrc y que la API key se está añadiendo a la ruta correspondiente del archivo netrc, tras lo cual el inicio de sesión se completa y el usuario registrado aparece como tommyzihao, junto con un comando para forzar un nuevo inicio de sesión. Esta imagen corresponde al paso «Inicia sesión en wandb» y presenta el proceso y el resultado del inicio de sesión.](../../en/images/d45-05.png)

## Monta el conjunto de datos

```Shell
Copy the instance download command, something like:
featurize dataset download 7f40bdaa-b1a4-4c00-9652-ff26fd079109

unzip lerobot_zihao_dataset_shake_hands.zip
```

El conjunto de datos aparece bajo el directorio `~`

## Ajusta la frecuencia de guardado de pesos (opcional)

Abre `lerobot/src/lerobot/configs/train.py`

Cambia save_freq de 20_000 a 5_000

Así obtendrás los archivos de pesos del modelo antes durante el entrenamiento
