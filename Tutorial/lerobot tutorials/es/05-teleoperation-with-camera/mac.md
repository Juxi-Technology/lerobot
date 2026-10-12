[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | Español | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Computadora con Mac

## Conectar la cámara a la computadora

```Shell
lerobot-find-cameras opencv
```

![La imagen muestra el resultado de detección después de conectar una cámara a un Mac. Enumera las dos cámaras generadas automáticamente, la cámara externa y la cámara frontal integrada del Mac. La Fps de la cámara externa es 60.00024 y la Fps de la cámara integrada es 30.0. Esta imagen se relaciona con el contenido sobre conectar una cámara a un Mac y presenta visualmente el resultado de la detección tras la conexión, lo que ayuda al usuario a comprender el tipo, el ID, el backend API y la velocidad de fotogramas de cada cámara.](../../en/images/d31-01.png)

## Una cámara, teleoperación con la imagen de la cámara mostrada

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

Tras la ejecución, comienza la teleoperación

Se abre la ventana de rerun.io, que muestra en tiempo real la trayectoria de cada articulación del servo, junto con la imagen en vivo de la cámara

y guarda las imágenes en el directorio `~/username/outputs/captured_images`

![La imagen muestra la ventana de rerun.io que se abre al iniciar la teleoperación tras la ejecución. A la izquierda hay gráficos de las trayectorias de varias articulaciones del servo, presentados como curvas que muestran el movimiento de distintas articulaciones. A la derecha, la imagen de la cámara de la escena interior se muestra en tiempo real, donde se ven una mesa, sillas y algunos objetos. También hay cierta información en forma de barras en la parte inferior. Esta imagen está estrechamente relacionada con el contexto y presenta visualmente las trayectorias de las articulaciones del servo y la imagen en vivo de la cámara durante la teleoperación, y también ilustra que las imágenes se guardan en el directorio especificado.](../../en/images/d31-02.png)

## Varias cámaras, teleoperación con las imágenes de las cámaras mostradas

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 1920, height: 1080, fps: 30, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

![La imagen muestra la ventana de rerun.io utilizada para la teleoperación con varias imágenes de cámara. A la izquierda está la imagen en vivo de la cámara, que muestra objetos sobre un escritorio; a la derecha hay gráficos de datos que muestran las trayectorias de distintas articulaciones, como observation_wip. En la parte inferior hay un área Streams que enumera datos de varias articulaciones. En la parte superior derecha hay información de datos como Application ID y Source IP. Esta imagen corresponde al contenido "Varias cámaras, teleoperación con las imágenes de las cámaras" y presenta visualmente las imágenes y los datos durante la teleoperación.](../../en/images/d31-03.png)
