[English](../../en/09-inference/common-bugs.md) | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | Español | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# Errores comunes y soluciones

## Falla la captura de la cámara

![Esta imagen muestra la salida del terminal cuando se ejecuta el código del robot de LeRobot. Los registros `INFO` muestran la apertura de la cámara de OpenCV y la desconexión del Follower; el registro `ERROR` señala que en el archivo `camera_opencv.py` la función `read` lanzó un `RuntimeError` por `OpenCVCamera(0) read failed`. La imagen se relaciona con el problema "Falla la captura de la cámara" y muestra visualmente el problema que aparece al ejecutar el código, ayudando a explicar la causa concreta del fallo de captura.](../../en/images/d65-01.png)

Comprueba si el cable de la cámara de muñeca está flojo, sobre todo el extremo junto a la cámara: ese conector es muy propenso a hacer mal contacto

## La cámara se desconecta

![Esta imagen muestra la interfaz de ejecución del código /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py. Arriba muestra la hora, el ID de proceso y otra información; debajo hay rutas de código y mensajes de error como /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py y "INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.". La parte clave es "raise TimeoutError" y "TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.", lo que indica que falló la captura de la cámara. La imagen se relaciona con el problema "Falla la captura de la cámara" y muestra visualmente el error.](../../en/images/d65-02.png)

Reinicia la línea de comandos

## Problema de comunicación con el servo 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![Esta imagen muestra lo siguiente.](../../en/images/d65-03.png)

La solución: cambia todos los `num_retry` del código en `lerobot/src/lerobot/motors/motors_bus.py` a 99, especialmente el de la línea que da el error

![Esta imagen muestra el contenido del archivo de código `motors_bus.py` del proyecto LeRobot. Está resaltado el método `write` de la clase `MotorsBusABC`, con la variable `num_retry` cambiada a `99`. La imagen se relaciona con la sección "Problema de comunicación con el servo 1" y corresponde a la solución de cambiar todos los `num_retry` del código en `lerobot/src/lerobot/motors/motors_bus.py` a 99, especialmente el de la línea que da el error.](../../en/images/d65-04.png)

## Problema de comunicación con el servo 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![Esta imagen muestra una sesión de línea de comandos en el terminal zsh de macOS. El terminal muestra varias rutas de archivo y números de línea, como `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`. La línea 587 del archivo `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` lanza un `ConnectionError`, informando de un fallo al escribir `Torque_Enable` en id=1 sin paquete de estado. La imagen se relaciona con el contenido "Problema de comunicación con el servo 2" y muestra visualmente la ejecución del código en el momento del error.](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![Esta imagen muestra una sesión de línea de comandos en el terminal zsh de macOS. El terminal muestra varias rutas de archivo y números de línea, como `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`. Aquí, `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

Solución: recalibra el brazo robótico
