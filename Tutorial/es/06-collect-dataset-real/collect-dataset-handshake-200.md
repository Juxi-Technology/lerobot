[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | Español | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# Recopilar un conjunto de datos por demostración — Handshake 200

## Crear un repositorio de conjunto de datos en HuggingFace

https://huggingface.co/new-dataset

![La imagen muestra la interfaz para crear un nuevo repositorio de conjunto de datos en HuggingFace. "Owner" aparece como TommyZihao, el nombre del conjunto de datos es "lerobot_zihao_dataset_shake200", "License" está establecida en mit y el tipo de conjunto de datos es "Public", visible para cualquiera, mientras que solo el propietario del conjunto de datos o los miembros de la organización pueden hacer commits. Debajo se indica que, tras crear el conjunto de datos, se pueden subir archivos a través de la interfaz web o de git, y hay un botón "Create dataset" en la parte inferior. Esta imagen se relaciona con el contenido sobre crear un repositorio de conjunto de datos en HuggingFace y muestra la interfaz de la operación de creación.](../../en/images/d37-01.png)

## Eliminar cualquier conjunto de datos existente con el mismo nombre (si lo hay)

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Recopilación del conjunto de datos Shake200

Una cámara, recopilar un conjunto de datos - computadora con Mac

```Shell
lerobot-record \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true \
    --dataset.repo_id=Tommymy/lerobot_my_dataset_shake200 \
    --dataset.num_episodes=200 \
    --dataset.single_task="Shanke Hands" \
    --dataset.push_to_hub=false \
    --dataset.episode_time_s=12 \
    --dataset.reset_time_s=1
```

## Durante la recopilación

<grid>
<column width-ratio="0.508765">
![La imagen muestra la interfaz del terminal mientras se recopila un conjunto de datos en un Mac. Muestra la salida de SvtInfo() y SvtInfo(), incluidos el número de versión, el compilador y la arquitectura. También presenta los parámetros de configuración de SvtConfig(), como width, height, velocidad de fotogramas y preset. Debajo hay una salida marcada como "INFO" e "INFO 0", como "Starting second pass: moving the moving atom to the beginning of the file". Esta imagen se relaciona con el contenido "Durante la recopilación" y presenta visualmente la configuración y la información que se muestran en el terminal durante la recopilación.](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![La imagen muestra la salida del terminal mientras se recopila un conjunto de datos con el script Open_Duck_Mini_Runtime_2 en un Mac. Muestra parámetros de configuración de vídeo como los de SVT y otros, como el tamaño de gop y el tipo de key - frame, y presenta la versión del codificador de vídeo y la fecha de compilación. Debajo hay registros de archivos MP4, como "Starting second pass: moving the moov atom to the beginning of the file". Esta imagen se relaciona con el flujo de trabajo de recopilación del conjunto de datos y presenta visualmente la respuesta del terminal durante la recopilación.](../../en/images/d37-03.png)
</column>
</grid>

Controles con las teclas de flecha del teclado:  
→ (flecha derecha) Termina el episodio actual antes de tiempo; pasa al siguiente episodio.  
← (flecha izquierda) Cancela el episodio actual; vuelve a grabarlo.  
ESC, detiene de inmediato, codifica el vídeo y sube el conjunto de datos.

## Recopilación finalizada — directorio de guardado del conjunto de datos

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
