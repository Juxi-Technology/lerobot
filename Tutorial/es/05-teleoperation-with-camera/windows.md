[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | Español | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Computadora con Windows

## Conectar la cámara a la computadora

```Shell
lerobot-find-cameras opencv
```

![Esta imagen es la ventana de la línea de comandos de Windows y muestra errores de conexión de cámara y resultados de detección de dispositivos. En la parte superior hay un error: "ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range". Debajo enumera las cámaras detectadas, incluidas Camera #0 y Camera #1, con su nombre, tipo, backend API, configuración de flujo predeterminada, formato, origen, ancho, alto y velocidad de fotogramas; en la parte inferior hay errores como "lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0". Esto corresponde al escenario de error mencionado en el documento, "la cámara no se puede conectar, pero al cambiar de cámara en Tencent Meeting sí se abre normalmente", y es la respuesta de error real en tiempo de ejecución antes de modificar el código del backend de OpenCV.](../../en/images/d32-01.png)

## Teleoperación con la imagen de la cámara mostrada

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

Se abre la ventana de rerun.io, que muestra en tiempo real la trayectoria de cada articulación del servo, junto con la imagen en vivo de la cámara

y guarda las imágenes en el directorio `C:\Users\username\outputs\captured_images`

![La imagen muestra la ventana de rerun.io, que muestra en tiempo real las trayectorias de las articulaciones del servo y la imagen en vivo de la cámara. A la izquierda está la interfaz de blueprint con opciones como "teleoperation". En el centro está el gráfico de trayectorias, que muestra datos de posición de articulaciones como "observation_wrist_rot.pos". A la derecha está la imagen de la cámara, que muestra la escena desde la perspectiva del robot. En la parte superior derecha muestra "Waiting for data on rerun: http://127.0.0.1:9876/remote...", con la información del origen de datos debajo. Esta imagen se relaciona con el contenido que describe la ventana de rerun.io mostrando la imagen de la cámara en tiempo real y presenta visualmente el efecto.](../../en/images/d32-02.png)

## Si te encuentras con el siguiente error

La cámara no se puede conectar, pero al cambiar de cámara en Tencent Meeting sí se abre normalmente

![La imagen muestra la interfaz de línea de comandos de Windows con resultados de detección de cámara. En la parte superior muestra "Detected Cameras" e información relacionada con la cámara, como nombre, tipo, ID y backend API. Debajo hay un error que indica que, al ejecutar lerobot_find_cameras_openpyc, la cámara OpenCV no se pudo conectar ni configurar, y te sugiere ejecutar lerobot_find_cameras_opencv para encontrar una cámara disponible, y que al no poder conectarse ninguna cámara se abortará el guardado de imágenes. Esta imagen corresponde al contexto del problema de conexión de la cámara y presenta visualmente el error.](../../en/images/d32-03.png)

Modifica el archivo `lerobot\src\lerobot\cameras\utils.py` para cambiar el backend de OpenCV a `cv2.CAP_SHOW`

![La imagen muestra el código de la función `get_cv2_backend()` del archivo `lerobot\\src\\lerobot\\cameras\\utils.py`. Cuando el sistema es Windows, la función devuelve `int(cv2.CAP_DSHOW)`, que se usa para emplear MSMF en lugar de AVFOUNDATION en Windows. El código también contiene un comentario sobre `cv2.CAP_MSMF` y cómo se manejan otros sistemas como Darwin (macOS) y Linux. Esta imagen se relaciona con la operación de modificar el archivo `lerobot\\src\\lerobot\\cameras\\utils.py` para cambiar el backend de OpenCV a `cv2.CAP_SHOW`, y es un ejemplo de modificación de código.](../../en/images/d32-04.png)

> Este es un error que ni Doubao puede resolver; se debe a que la biblioteca lerobot está encapsulada en exceso y a los principiantes les cuesta mucho depurarlo

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## Conectar varias cámaras, teleoperación con las imágenes de las cámaras mostradas

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![La imagen muestra la ventana de rerun.io utilizada para la teleoperación con imágenes de cámara. A la izquierda hay un gráfico de trayectorias que muestra datos de varias articulaciones, como observation_wrist_l_pos y observation_wrist_r_pos. A la derecha, arriba está la imagen en vivo de la cámara y abajo la ventana de Tencent Meeting. En la parte superior derecha muestra "Waiting for data on rerun: http://127.0.0.1:9678/remote...". Esta imagen se relaciona con el contenido sobre conectar varias cámaras y mostrar las imágenes de las cámaras durante la teleoperación, y presenta visualmente el efecto.](../../en/images/d32-05.png)
