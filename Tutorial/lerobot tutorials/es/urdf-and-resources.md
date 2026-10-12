[English](../en/urdf-and-resources.md) | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | Español | [Français](../fr/urdf-and-resources.md) | [Italiano](../it/urdf-and-resources.md) | [日本語](../ja/urdf-and-resources.md) | [한국어](../ko/urdf-and-resources.md) | [Português (BR)](../pt-br/urdf-and-resources.md) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>Archivos URDF y recursos de referencia</title>

# El [archivo URDF](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf) oficial de Lerbot



## URDF Studio

https://urdf.d-robotics.cc/



## Control de simulación ROS2 (impleméntalo tú mismo)

https://github.com/holmsslk/so-arm-moveit-hardware



## Interfaz gráfica oficial de LeRobot

https://github.com/huggingface/leLab

LeLab es una aplicación web que reúne todo el flujo de trabajo de LeRobot —calibración, teleoperación, grabación, entrenamiento, reproducción— en una única interfaz de navegador. Solo tienes que conectar el brazo robótico, abrir la aplicación y ponerte a trabajar. Sin engorrosos comandos de línea de comandos ni entrada de teclado.

🤗 El punto de entrada web nativo de LeRobot, diseñado para que los nuevos usuarios pasen de "recién sacado de la caja" a "entrenar su primera política" en cuestión de minutos.

🤗 Instala y ejecuta todo con un solo comando.



# Controlar el brazo Follower desde un teléfono

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## Desarrollo de robótica en la nube: dispositivos ROS 2 y simulación LeRobot con Isaac Sim y transmisión de datos en AWS

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## Configurar los IDs de los servos y la calibración del centro en la interfaz web

https://bambot.org/feetech.js?lang=zh

1. Introduce 0 o 1 según el modelo del servo y, a continuación, haz clic en "Connect"

![La imagen muestra la interfaz de conexión para configurar los IDs de los servos y la calibración del centro en la interfaz web. La interfaz tiene una sección "Connect" que contiene un desplegable de velocidad en baudios, configurado actualmente en "1,000,000 bps (Index 0)"; un desplegable de extremo de protocolo, configurado actualmente en "0=STS/SMS"; y un botón "Connect". En la parte inferior de la interfaz se muestra "Status: Disconnected". La imagen está estrechamente ligada al contexto: tras introducir 0 o 1 según el modelo del servo y hacer clic en "Connect", se escanean los servos con IDs 1~6 para confirmar el servo con el ID correspondiente; esta es una interfaz clave de ese flujo.](../en/images/d68-01.png)

2. Escanea los servos con IDs 1\~6; usa FOUND en los resultados del escaneo para confirmar el servo con el ID correspondiente. Por ejemplo, en la imagen se encontró el servo con ID 1

![La imagen muestra la interfaz de escaneo de servos del URDF Studio oficial de Lerbot. La interfaz muestra un ID inicial de 1 y un ID final de 6, con un botón "Start scan" debajo. En los resultados del escaneo, al escanear el ID1 se encontró el ID1239, mientras que al escanear del ID2 al ID6 se informa en cada caso "ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0". Esta imagen se relaciona con la operación de escaneo de servos del URDF Studio oficial de Lerbot descrita en el contexto y presenta visualmente el proceso de escaneo y sus resultados.](../en/images/fix-01.png)

3. Configuración de ID y calibración del centro

① Configura la entrada del ID del servo actual con el ID del servo escaneado

② Introduce un número en "ID management" y haz clic en "Change ID" para configurar el ID

③ Calibración del centro (el centro del servo STS3215 es 2047, el centro del servo SCS0009 es 511)

Servo STS: introduce 2047 en "Position control" y haz clic en "Set"

Servo SCS: introduce 511 en "Position control" y haz clic en "Set"

![La imagen muestra la interfaz de control de un solo servo de Lerbot. El "Current servo ID" se muestra como 1; debajo, en "ID management", aparecen el número 1 y un botón "Change ID", con el mensaje "Success: ID changed to 1" debajo. En el área Position Control hay un botón "Read position" que muestra la posición 2047, junto a un botón "Set". Esta imagen se relaciona con la sección "Configuración de ID y calibración del centro" del documento y presenta visualmente la interfaz para configurar los IDs de los servos y calibrar el centro, ayudando a los usuarios a entender cómo realizar estos ajustes en Lerbot.](../en/images/d68-02.png)
