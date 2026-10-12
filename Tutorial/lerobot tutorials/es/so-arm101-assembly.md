[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | Español | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>Tutorial de montaje del kit del brazo robótico SO-ARM101</title>

<callout emoji="💡">
Nota: omite este tutorial si tienes un brazo premontado
</callout>

## Piezas impresas en 3D para el brazo follower

![Esta imagen muestra las piezas impresas en 3D para el brazo follower necesarias para montar el brazo robótico SO-ARM101, todas ellas piezas de plástico PLA blancas dispuestas sobre una superficie clara con veta de madera. Las piezas incluyen conectores de diversas formas, una estructura bifurcada con rejilla, una pieza tipo base con orificios, un brazo de soporte bifurcado de forma especial, etc., en consonancia con la idea del tutorial de que el extremo del brazo follower es una pinza. Estas piezas son las piezas moldeadas básicas del brazo follower y son los objetos que se manipulan en el paso de retirada de soportes, y corresponden directamente a las piezas impresas en 3D del brazo follower presentadas en el tutorial.](../en/images/d09-01.jpg)

## Piezas impresas en 3D para el brazo leader

![La imagen muestra piezas impresas en 3D para el brazo robótico SO-ARM101. En el marco se disponen ordenadamente diversas piezas impresas en 3D de color negro, con líneas azules en los bordes de algunas piezas. Estas piezas incluyen componentes estructurales para los brazos leader y follower, como la pinza, el mango y el gatillo, además de conectores. La imagen corresponde a la sección "Piezas impresas en 3D para el brazo leader" del documento y presenta visualmente el aspecto de las piezas impresas en 3D, ofreciendo una referencia para los pasos posteriores de retirada de soportes sobrantes y de distinción de los servos.](../en/images/d09-02.jpg)

Los brazos leader y follower son muy similares; solo difiere el extremo

El leader tiene un mango y un gatillo; el follower tiene una pinza

## Retirar los soportes sobrantes de las piezas impresas en 3D

Revisa cada agujero, abertura, ranura y rejilla, especialmente los cinco agujeros que se parecen a la ficha de "cinco puntos" del mahjong

Este paso es muy importante; de lo contrario, no podrás atornillar los tornillos más adelante

## Distinguir los cuatro servos

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">Tamaño grande</td><td vertical-align="middle">Tamaño pequeño</td><td vertical-align="middle">Voltaje (V)</td><td vertical-align="middle">Relación de engranajes</td><td vertical-align="middle">Articulación del brazo</td><td vertical-align="middle">Cantidad</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7,4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7,4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7,4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Todas las articulaciones del follower</td><td vertical-align="middle">6</td></tr></tbody></table>

> La relación de engranajes es la relación entre la "velocidad del motor : velocidad del eje de salida del servo"; por ejemplo, 1:345 significa que el motor gira 345 veces para que el eje de salida gire una vez.
> 
> Una relación de engranajes alta multiplica el par a través del tren de engranajes, por lo que puede accionar una carga más pesada (como el brazo follower)
> 
> Pero, al mismo tiempo, el eje de salida gira más despacio (porque va "reducido")
> 
> Arrastrar la articulación también requiere más esfuerzo

A continuación se muestran los modelos y las relaciones de engranajes de todos los servos de este proyecto; las partes subrayadas son sus números

![La imagen muestra los modelos, las tensiones y las relaciones de engranajes de los servos utilizados en el brazo. A la izquierda está el brazo leader, con dos modelos, C046 (7,4 V, 1:147) y C044 (7,4 V, 1:191); a la derecha está el brazo follower, con dos modelos, C001 (7,4 V, 1:345) y C047 (12 V, 1:345). La imagen está estrechamente ligada al contexto, que presenta en detalle los modelos, las tensiones y las relaciones de engranajes de los servos de los brazos leader y follower; esta imagen presenta visualmente estas cifras clave para ayudar a los lectores a comprender mejor la configuración de los servos.](../en/images/d09-03.png)

![La imagen muestra cuatro cajas de servos etiquetadas "STS3215". En cada caja está impresa la palabra "SPECIFICATION" e incluye parámetros como el par, la velocidad y las dimensiones, por ejemplo un par de 9,2 kg·cm/127,98 oz·in(6 V). El STS3215-C001 tiene un par de 12,5 kg·cm/173,88 oz·in(6 V), y el STS3215-C046 tiene un par de 16 kg·cm/220,58 oz·in(7 V). Estos servos son el modelo utilizado para todas las articulaciones del brazo follower, correspondiente al brazo follower presentado en el documento, y se emplean para la instalación de los servos en los pasos de montaje posteriores.](../en/images/d09-04.jpg)

## Distinguir los dos adaptadores de corriente

Adaptador de corriente de 5 V 6 A 30 W: alimenta los servos de 7,4 V (brazo leader), negro

Adaptador de corriente de 12 V 5 A 60 W, alimenta los servos de 12 V (brazo follower), blanco

## Descargar la herramienta de depuración de servos Feetech

### Windows PC

https://gitee.com/ftservo/fddebug

Descarga [`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z), extráelo y ejecuta el programa exe que contiene

### Ubuntu y Mac (el archivo incluye un tutorial)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![Esta imagen es una ilustración auxiliar del tutorial de montaje del kit del brazo robótico SO-ARM101, correspondiente a la sección sobre cómo distinguir los adaptadores de corriente. Muestra dos modelos de servo y sus posiciones de montaje, STS3215-C001 y STS3215-C018, y también etiqueta servos como STS3215-C004, correspondientes a las distintas articulaciones del brazo. La figura también enumera los parámetros de estos dos servos, incluidos la velocidad de rotación, el par de bloqueo, la precisión del servo, las funciones de protección y la realimentación de parámetros, lo que constituye una referencia para la selección e instalación de los servos durante el montaje del brazo.](../en/images/d09-05.jpg)

**Versión Pro: el brazo leader utiliza un adaptador de corriente de 5V6A, y el brazo follower utiliza un adaptador de corriente de 12V5A**

La configuración del ID del servo, la calibración del ángulo del servo y el montaje deben hacerse de antemano; consulta el [tutorial de montaje oficial](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# Paso 1: Configurar los IDs de los servos e instalar los cuernos de servo (excepto el servo 5)

<grid>
<column width-ratio="0.500000">
![La imagen muestra la interfaz de la herramienta de depuración de host de Feetech. La interfaz tiene tres pestañas, "Debug", "Program" y "Upgrade", con "Program" seleccionada actualmente. Información clave: 1. En la configuración de comunicación, el número de puerto es COM6 y la velocidad en baudios es 1000000; 2. En las operaciones de servo, la escritura síncrona, la escritura asíncrona y la salida de par están todas marcadas; 3. En la realimentación del servo, parámetros como el voltaje, la corriente, la temperatura y la posición muestran todos 0; 4. En la búsqueda de servos, el id 1 está seleccionado, modelo ST53215. Esta imagen se relaciona con las operaciones de depuración descritas anteriormente, como configurar los IDs de los servos e instalar el cuerno del servo, y presenta la interfaz de la herramienta de depuración.](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![La imagen muestra la interfaz de la herramienta de depuración de host de Feetech, utilizada para configurar los IDs de los servos. La interfaz tiene tres pestañas, "Debug", "Program" y "Upgrade", con "Program" seleccionada actualmente. En el área "Center calibration", el número de ID es 4, con un botón "Save" a la derecha. En el lado izquierdo de la interfaz se muestra el ID del servo, el modelo y otra información. Esta imagen se relaciona con el contenido "Paso 1: Configurar los IDs de los servos e instalar los cuernos de servo (excepto el servo 5)" del documento y presenta la interfaz de la operación de configuración del ID del servo, mostrando visualmente dónde se introduce el número de ID.](../en/images/d09-07.png)
</column>
</grid>

1. Abre la herramienta de depuración de host de Feetech, selecciona el puerto COM, configura la velocidad en baudios a un millón y haz clic en "Open"
2. Haz clic en "Search"; cuando aparezca "STS3215", haz clic en "Stop" y luego en "STS3215"
3. Selecciona "Debug" en la parte superior; puedes arrastrar el deslizador para girar el servo, o hacer clic en "Scan" para hacerlo mover de un lado a otro. Confirma que el servo funciona con normalidad
4. Selecciona "Program" en la parte superior
5. Haz clic en "Center calibration" para establecer la posición actual del eje de rotación del servo como el centro (0-4095)
6. Haz clic en "ID", configura el número de ID del servo correspondiente en la esquina inferior derecha y haz clic en "Save". Ten en cuenta que el número son cifras arábigas simples, sin letras.
7. Desenchufa el cable que conecta el servo a la placa controladora
8. Conecta el cable del servo al servo

El servo 1 lleva dos cables; los demás servos llevan solo un cable por ahora

![La imagen muestra la instalación de los servos durante el montaje del kit del brazo SO-ARM101. El marco contiene el brazo follower y el brazo leader, con el brazo follower numerado 123456 y el brazo leader numerado 123456. Los servos están etiquetados con relaciones de engranajes de 1:345, 1:191 y 1:147. Debajo está la placa controladora, conectada a dos cables, uno blanco y otro negro. Esta imagen se relaciona con los pasos de montaje anteriores y presenta visualmente las posiciones de montaje y los números de los servos, ayudando a quien monta a hacer coincidir los servos con la placa controladora con precisión.](../en/images/d09-08.png)

<callout emoji="💡">
De nuevo: asegúrate de que el ID de articulación y la relación de engranajes de cada servo coincidan exactamente con **SO-ARM101**.
</callout>

Cada motor del bus tiene un ID único. Los motores nuevos suelen venir con un ID predeterminado de `1`. Para garantizar que funcione la comunicación entre los motores y el controlador, primero debemos asignar un ID único a cada motor. Además, la velocidad de transmisión de datos en el bus viene determinada por la velocidad en baudios. Para poder comunicarse entre sí, el controlador y todos los motores deben estar configurados con la misma velocidad en baudios; los servos de este brazo utilizan una velocidad en baudios de 100000.

Para ello, primero debemos conectar el controlador a cada motor por turnos para poder configurarlos. Como escribimos estos parámetros en el área no volátil de la memoria interna del motor (EEPROM), esto solo hay que hacerlo una vez.

Si reutilizas motores de otro robot, es posible que también tengas que hacer este paso, porque los IDs y las velocidades en baudios pueden no coincidir.

El vídeo de abajo muestra la secuencia de pasos para configurar los IDs de los motores.

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Usa la herramienta de host de servos de Feetech para configurar los IDs de los servos y calibrar el centro. Los IDs se configuran del 1 al 6!

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu y Mac

<callout emoji="💡">
Si necesitas la herramienta de host de servos de Feetech, consulta la [herramienta de depuración de servos Feetech](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb) de arriba
</callout>

Primero completa la configuración del entorno siguiendo la página de la [instalación oficial de LeRobot](https://huggingface.co/docs/lerobot/installation)

<callout emoji="💡">
Recuerda activar el entorno virtual y entrar en el directorio src/lerobot correspondiente
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. Encuentra el puerto USB del brazo. Para encontrar el puerto correcto de cada brazo, ejecuta el script de utilidad dos veces:

```Plain Text
lerobot-find-port
```

Salida de ejemplo al identificar el puerto del brazo Leader (por ejemplo `/dev/tty.usbmodem575E0031751` en un Mac, o posiblemente `/dev/ttyACM0` en Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

Salida de ejemplo al identificar el puerto del brazo Follower (por ejemplo `/dev/tty.usbmodem575E0032081`, o posiblemente `/dev/ttyACM1` en Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
Recuerda desenchufar el conector USB, de lo contrario no se podrá detectar el puerto.
</callout>

2. Conecta el PC a la placa controladora de servos del brazo follower con un cable USB y enciéndelo. Luego ejecuta el siguiente comando. Cambia --robot.port=/dev/ttyACM0 del comando por el puerto que hayas encontrado. Por ejemplo, si el puerto que encontraste es /dev/ttyACM1, cámbialo a --robot.port=/dev/ttyACM1

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

Verás la siguiente salida.

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

Siguiendo las instrucciones, conecta el servo de la pinza. Asegúrate de que sea el único servo conectado a la placa controladora de servos y de que este servo aún no esté conectado a ningún otro servo. Después de pulsar **[Enter]**, el script configura automáticamente el ID y la velocidad en baudios de ese servo. Los IDs se configuran del 6 al 1!

Después de eso, deberías ver lo siguiente:

```Python
'gripper' motor id set to 6
```

Luego la siguiente salida es:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**Nota** Repite lo anterior para cada servo, siguiendo las instrucciones.
Al igual que con los servos anteriores, asegúrate de que sea el único servo conectado a la placa controladora y de que el propio servo no esté conectado a ningún otro servo.
</callout>

Antes de pulsar **Enter** cada vez, asegúrate de comprobar las conexiones de los cables. Por ejemplo, el cable de alimentación puede aflojarse al manipular la placa de circuito.

Cuando hayas completado todos los pasos, el script termina automáticamente y los servos quedan listos para usar. Ahora puedes conectar por turnos el conector de 3 pines de cada servo, y conectar el cable del primer servo (el servo de "shoulder pan" con ID 1) a la placa controladora. La placa controladora ya se puede montar en la base del brazo.

Repite los mismos pasos para el brazo leader.

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# Paso 2: Montaje

<callout emoji="💡">
- Los pasos de montaje del brazo follower son esencialmente los mismos que los del brazo leader. La única diferencia es que, tras el paso 12, el efector final (pinza y mango) se instala de forma diferente.
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
Instalación de la placa controladora de servos: primero monta los 4 separadores de latón y luego fija la placa controladora con cuatro tornillos M2.5\*8
</callout>

<grid>
<column width-ratio="0.525947">
![Instala los cuatro separadores de latón](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![Fija la placa controladora de servos con tornillos M2.5*8](../en/images/d09-10.webp)
</column>
</grid>

![Monta sobre el brazo y cablea](../en/images/d09-11.png)

**Versión Pro: el brazo leader negro utiliza un adaptador de corriente de 5V6A, y el brazo follower blanco utiliza un adaptador de corriente de 12V5A**







# Configurar los IDs de los servos y la calibración del centro en la interfaz web

https://bambot.org/feetech.js?lang=zh

1. Introduce 0 o 1 según el modelo del servo y, a continuación, haz clic en "Connect"

![La imagen muestra la interfaz "Connect" en el tutorial de montaje del kit del brazo. A la izquierda de la interfaz está la palabra "Connect", y a la derecha hay un desplegable "Baud rate" configurado en 1,000,000 bps (Index 0), y una caja de entrada para "Protocol end (0=STS/SMS, 1=SCS)" configurada en 0, con un recuadro rojo alrededor del número "1" junto a la caja de entrada. Debajo hay un botón verde "Connect", con un recuadro rojo alrededor del número "2" junto a él. En la parte inferior se muestra "Status: Disconnected". Esta imagen corresponde al contenido anterior, "Introduce 0 o 1 según el modelo del servo y, a continuación, haz clic en 'Connect'", y presenta visualmente la configuración de la operación de conexión.](../en/images/d09-12.png)

2. Escanea los servos con IDs 1\~6; usa FOUND en los resultados del escaneo para confirmar el servo con el ID correspondiente. Por ejemplo, en la imagen se encontró el servo con ID 1

![La imagen muestra la interfaz del paso "Scan servos" en el tutorial de montaje del kit del brazo SO-ARM101. En la parte superior de la interfaz están las cajas de entrada "Start ID" y "End ID", actualmente con ID inicial 1 e ID final 6. Debajo hay un botón "Start scan". En los resultados del escaneo, al escanear los IDs 1-6 no se encuentra ningún servo, informando "Exception: No status packet! Error code: 0". Esta imagen está estrechamente ligada al contexto y presenta visualmente la interfaz y los resultados al escanear servos, ayudando a los usuarios a comprender el estado del escaneo de servos.](../en/images/d09-13.png)

3. Configuración de ID y calibración del centro

① Configura la entrada del ID del servo actual con el ID del servo escaneado

② Introduce un número en "ID management" y haz clic en "Change ID" para configurar el ID

③ Calibración del centro (el centro del servo STS3215 es 2047, el centro del servo SCS0009 es 511)

Servo STS: introduce 2047 en "Position control" y haz clic en "Set"

Servo SCS: introduce 511 en "Position control" y haz clic en "Set"

![La imagen muestra una interfaz de control de un solo servo. El ID del servo actual es 1; tras introducir el número 1 en ID management y hacer clic en "Change ID", aparece el mensaje "Success: ID changed to 1". En Position Control el valor es 2047, y al hacer clic en el botón "Set" se aplica. Esta imagen se relaciona con el contexto "Configuración de ID y calibración del centro" y presenta visualmente la interfaz de la operación de configuración del ID, ayudando a los usuarios a comprender cómo introducir un número en "ID management" para configurar el ID y cómo introducir el valor del centro en "Position control" y hacer clic en "Set" para finalizar.](../en/images/d09-14.png)
