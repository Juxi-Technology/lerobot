[English](../en/servo-calibration-tool.md) | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | [Deutsch](../de/servo-calibration-tool.md) | Español | [Français](../fr/servo-calibration-tool.md) | [Italiano](../it/servo-calibration-tool.md) | [日本語](../ja/servo-calibration-tool.md) | [한국어](../ko/servo-calibration-tool.md) | [Português (BR)](../pt-br/servo-calibration-tool.md) | [Português (PT)](../pt-pt/servo-calibration-tool.md)

# Herramienta de calibración de servos STS3215 para la serie So-ARM (opcional)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**Un conjunto de herramientas de calibración de fábrica de servos FTServo y de calibración de LeRobot diseñado para los brazos de la serie So-ARM 10X**

> ⚠️ **Nota de compatibilidad: este sistema actualmente solo admite servos Feetech (serie STS3215)**. La tabla de registros, el formato de parámetros xdat y la tabla de velocidades en baudios están todos diseñados para la serie STS3215 de Feetech.

> 📜 **Origen y créditos: esta herramienta está adaptada y mejorada a partir del** [**Seeed_RoboController de Seeed Studio**](https://github.com/Seeed-Studio) **proyecto**, publicado originalmente bajo la licencia MIT. Manteniendo la funcionalidad principal original, este proyecto refactoriza la GUI y añade el depurador FT, la copia de seguridad/restauración de parámetros xdat, compatibilidad multiplataforma, el cambio chino/inglés y otras mejoras.

---

## ✨ Características

| Característica | Descripción |
|-|-|
| Detección automática de puertos | Detecta de forma inteligente los puertos serie USB y filtra los dispositivos virtuales |
| Compatibilidad multiplataforma | Compatible con Windows / Ubuntu / macOS |
| Sincronización de doble puerto | Los puertos serie izquierdo y derecho funcionan de forma independiente, con soporte para el control remoto sincronizado de doble puerto leader/follower |
| Cambio chino/inglés | Cambio de chino/inglés con un clic en la interfaz, y la elección se recuerda automáticamente |
| Calibración del centro | Graba la posición actual del servo como el centro 2048 (persistido en la EEPROM) |
| Prueba de centro | Activa el par y mueve el servo al centro para verificar el resultado de la calibración |
| Desactivar motores | Desactiva el par de todos los servos con un clic para facilitar el ajuste manual |
| Escaneo automático | Detecta automáticamente todos los servos en línea con ID 1–20 |
| Control de un solo servo | Un deslizador controla en tiempo real la posición de un servo y la activación/desactivación del par |
| Depurador FT | Conexión serie, escaneo, lectura/escritura de parámetros, control de posición, cambio de velocidad en baudios, restablecimiento de fábrica, copia de seguridad de parámetros xdat |
| Parámetros xdat | Guarda los parámetros de la EEPROM del servo actual / abre una copia de seguridad para restaurar |
| Calibración de LeRobot | Genera archivos de calibración JSON en formato LeRobot |
| Ir al centro desde un archivo de calibración | Mueve el brazo al centro basándose en un archivo de calibración |

---

## 📚 Tutoriales detallados

### Chino

| SO | Tutorial |
|-|-|
| Windows | \[Tutorial de Windows\](docs/zh/Windows教程.md) |
| Linux | \[Tutorial de Linux\](docs/zh/Linux教程.md) |
| macOS | \[Tutorial de macOS\](docs/zh/macOS教程.md) |

### Inglés

| SO | Guía |
|-|-|
| Windows | \[Guía de Windows\](docs/en/Windows.md) |
| Linux | \[Guía de Linux\](docs/en/Linux.md) |
| macOS | \[Guía de macOS\](docs/en/macOS.md) |

---

## 🖥️ Descripción general de la interfaz

El programa principal tiene tres pestañas:

```Plain Text
┌─────────────────────────────────────────────────────────────┐
│  SoARM Series Calibration Tool  [Port1▾] [Port2▾] [🔄]  [🎮Remote][EN]│  ← Top bar
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────┬──────────────────────────────┐ │
│  │ Port1 - Servo Calib.    │ Port2 - Servo Calib.         │ │
│  │  [🔴Disconnected] Cur:… │  [🔴Disconnected] Cur:…      │ │
│  │  Servo1~6 status table  │  Servo1~6 status table       │ │
│  │  [CenterCal][CenterTest]│  [CenterCal][CenterTest]…    │ │
│  └─────────────────────────┴──────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

- **Barra superior**: título de la aplicación, desplegables de selección de puerto, botón de actualización, botón de control remoto, botón de cambio de idioma.
- **🦾 Tab1 Servo Calibration**: acciones rápidas para los paneles izquierdo y derecho (calibración del centro, prueba de centro, desactivar motores) más el estado en vivo.
- **🎚️ Tab2 Single-Servo Control**: ajusta con precisión la posición de cada servo en línea con un deslizador y activa o desactiva su par.
- **🔬 Tab3 FT Debugger**: conexión serie, escaneo, lectura/escritura de parámetros, control de posición, velocidad en baudios/restablecimiento de fábrica, copia de seguridad y restauración de parámetros xdat.

---

## 🚀 Inicio rápido

> Para los tutoriales completos de cada sistema, consulta \[📚 Tutoriales detallados\](#-详细教程). A continuación se indican los puntos clave de cada sistema.

### Windows

1. Instala [Python 3.10+](https://www.python.org/downloads/) (marca **Add to PATH**)
2. Crea un entorno virtual e instala las dependencias:

```Bash
cd Juxi_ServoController
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

1. Comprueba el entorno y lanza:

```Bash
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Confirma el número de puerto en el Administrador de dispositivos (por ejemplo, `COM3`) y selecciónalo en la barra superior. Para especificar los puertos manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux (Ubuntu / Debian)

1. Instala las fuentes CJK y las dependencias:

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ Añade permisos del puerto serie (grupo dialout)** [obligatorio]:

```Bash
sudo usermod -a -G dialout $USER
# Surte efecto después de cerrar sesión y volver a iniciarla
```

1. Crea un entorno virtual, instala las dependencias y lanza:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Los dispositivos serie son `/dev/ttyUSB0` / `/dev/ttyACM0`. Para especificar manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/ttyUSB0 --port2 /dev/ttyUSB1
```

### macOS

1. Instala `Python` con `Homebrew `:

```Bash
brew install python
```

1. Crea un entorno virtual, instala las dependencias y lanza:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. **⚠️ Nomenclatura de los puertos serie**: en macOS usa `/dev/cu.usbserial-*` (**recomendado, no bloqueante**) en lugar de `/dev/tty.*`. Para listarlos:

```Bash
ls /dev/cu.*
```

Para especificar manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### Herramientas generales de línea de comandos (sin necesidad de GUI)

```Bash
# Escanear servos
python -m src.tools.scan_id

# Calibración rápida del centro del servo
python -m src.tools.servo_quick_calibration

# Prueba de centro del servo
python -m src.tools.servo_center_test

# Desactivar todos los servos
python -m src.tools.servo_disable

# Calibración al estilo LeRobot
python -m src.tools.lerobot_calibrate

# Control remoto sincronizado de doble puerto
python -m src.tools.servo_remote_control
```

---

## 📖 Pasos de uso

### 1. Conectar y detectar servos

1. Conecta la placa controladora del brazo mediante un adaptador USB a serie y alimenta los servos.
2. Abre la GUI y selecciona el puerto en el desplegable de la barra superior (o haz clic en `🔄` para actualizar).
3. En la parte superior del panel se muestra `🟢 Connected` y se escanean automáticamente los servos en línea con ID 1–20 (normalmente 1–6).

> Si informa de que el puerto está ocupado, asegúrate de que ningún otro programa (un monitor serie, una herramienta abierta antes que no se cerró) lo esté usando.

### 2. Calibración del centro (establecer la posición actual en 2048)

> Antes de calibrar, coloca físicamente el brazo de modo que cada articulación esté en la posición de "cero / centro" que desees.

1. Haz clic en el botón **PortX Center Calibration** del panel.
2. El programa primero desactiva los servos y te pide que los muevas manualmente hasta el centro deseado.
3. Después de que confirmes, el programa realiza, para cada servo: desbloquear la EEPROM → escribir el comando de calibración (valor 128 en la dirección 40) → volver a bloquear la EEPROM.
4. Tras la calibración, usa "Center test" para verificar: el servo debería quedarse en su sitio (muy poco movimiento), lo que significa que la calibración se realizó correctamente.

### 3. Prueba de centro

1. Haz clic en **PortX Center Test**.
2. El programa activa el par y mueve todos los servos a 2048.
3. Si los servos apenas se mueven de su posición actual, la calibración es correcta; si se mueven mucho, el valor de calibración no es fiable y hay que rehacerlo.

### 4. Desactivar motores (ajuste manual)

- Haz clic en **PortX Disable Motors** para desactivar el par de todos los servos de ese puerto, de modo que puedan girarse libremente a mano.
- Para un solo servo, activa o desactiva su par individualmente en la página **Single-Servo Control** usando el interruptor de par situado debajo del deslizador.

### 5. Cambiar el ID de un servo

1. Ve a la página **🔬 FT Debugger**, conecta el puerto serie y escanea los servos.
2. Selecciona el servo objetivo, cambia el valor de "Servo ID" (dirección 0x05) en la tabla de parámetros y haz clic en escribir.
3. El programa realiza: desbloquear → escribir en la dirección 5 → verificar el nuevo ID → volver a bloquear.

> ⚠️ Antes de cambiar un ID, asegúrate de que este sea el único servo en el bus para evitar conflictos de ID.

### 6. Cambiar la velocidad en baudios / restablecimiento de fábrica

- **Cambiar la velocidad en baudios**: en el área "Baud rate / factory reset" de la página FT Debugger, selecciona la nueva velocidad en baudios (38400 – 1000000 bps) y aplícala. Tras escribirla, la velocidad en baudios del puerto serie se cambia automáticamente y se verifica mediante ping; si falla, se revierte automáticamente.
- **Restablecimiento de fábrica**: el servo vuelve a los valores predeterminados de fábrica (ID=1, velocidad en baudios=1000000); vuelve a escanear después.

### 7. Copia de seguridad y restauración de parámetros xdat

En el área "xdat parameters (EEPROM only)" de la página FT Debugger:

1. **💾 Save current servo**: guarda los parámetros de la EEPROM del servo seleccionado actualmente en un archivo xdat (copia de seguridad).
2. Después de cambiar los parámetros del servo libremente, si quieres restaurar:
3. **📂 Open xdat**: carga el archivo de copia de seguridad.
4. **📤 Restore parameters to servo**: vuelve a escribir la copia de seguridad en la EEPROM del servo actual.

### 8. Control remoto sincronizado de doble puerto

> ⚠️ **Dirección: el puerto 1 controla el puerto 2**. El puerto 1 (leader) solo lee los ángulos de los servos; el puerto 2 (follower) se controla de forma sincronizada.

1. Haz clic en **🎮 Remote** en la barra superior (el puerto 1 lee los ángulos → el puerto 2 controla de forma sincronizada los servos con los mismos IDs).
2. Ambos puertos deben tener IDs de servo coincidentes; solo se sincronizan los servos de la intersección.
3. Vuelve a hacer clic en el mismo botón para detenerte; después, los hilos de escaneo de los paneles izquierdo y derecho se reanudan automáticamente.

### 9. Calibración de LeRobot (línea de comandos)

```Bash
# Calibrar el brazo follower (se guarda en ~/.cache/huggingface/lerobot/calibration/robots/so_follower/)
python -m src.tools.lerobot_calibrate --arm-type follower

# Calibrar el brazo leader
python -m src.tools.lerobot_calibrate --arm-type leader
```

Flujo: desactivar servos → mover cada articulación al centro y registrar `homing_offset` → recorrer lentamente todo el recorrido y registrar `range_min/max` (`wrist_roll` es una articulación de rotación continua con un rango fijo de `[0,4095]`) → guardar el JSON.

Ir al centro usando un archivo de calibración:

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ Notas



1. **Primero la seguridad**: la calibración del centro se guarda en la EEPROM. Antes de calibrar, asegúrate de que la fuente de alimentación sea estable y de que el brazo no vaya a chocar con personas u objetos.
2. **Alimentación**: para el SoARM 101 estándar se recomienda 5 V 5 A CC; para la versión Pro, 12 V 5 A CC. Una alimentación insuficiente provoca pérdida de pasos de los servos o fallos de comunicación.
3. **Exclusividad del puerto serie**: en Windows el puerto se bloquea de forma exclusiva, por lo que el mismo puerto no puede ser usado a la vez por el hilo de escaneo de la GUI y el subproceso de calibración. La herramienta detiene automáticamente el hilo de escaneo y termina el proceso antiguo antes de operar; no hagas clics repetidos a mano.
4. **Permisos serie en Linux**: para acceder a `/dev/ttyUSB*` / `/dev/ttyACM*` hay que añadir el usuario al grupo `dialout` (consulta el \[Tutorial de Linux\](docs/zh/Linux教程.md)).
5. **Nomenclatura serie en macOS**: usa `/dev/cu.*` (no bloqueante) en lugar de `/dev/tty.*` (bloqueante, puede colgarse); consulta el \[Tutorial de macOS\](docs/zh/macOS教程.md).
6. **Conexión en caliente**: después de desenchufar el USB, el programa intenta reconectarse automáticamente; después de volver a enchufarlo, haz clic en `🔄` para actualizar la lista de puertos.
7. **Protección contra sobretemperatura / sobretensión**: el programa monitoriza el voltaje y la temperatura (alarma por encima de 60 °C). Si los servos siguen calientes, detente y deja que se enfríen.
8. **La calibración del centro es irreversible**: tras escribir, el desfase original se sobrescribe y no se puede deshacer. Registra primero la posición original antes de calibrar.
9. **Riesgo al cambiar el ID**: si la escritura o la verificación fallan, el programa informa de un error y reanuda el escaneo, pero en casos extremos el servo puede "perderse". Si eso ocurre, prueba "Factory reset" (tras el restablecimiento, el ID vuelve a 1).
10. **Problema de codificación**: si los emojis aparecen ilegibles en la consola de Windows, configura `PYTHONIOENCODING=utf-8` antes de ejecutar las herramientas de línea de comandos. Linux/macOS con UTF-8 nativo normalmente no tienen este problema.

---

## 🛠️ Solución de problemas

| Síntoma | Posible causa | Solución |
|-|-|-|
| No se puede abrir el puerto serie / puerto ocupado | Otro programa lo está usando | Cierra programas como los monitores serie, o cambia de puerto y reinicia la herramienta |
| No se encuentran servos en el escaneo | Alimentación insuficiente / cableado incorrecto / discrepancia en la velocidad en baudios | Comprueba la alimentación y el cableado, y confirma que los servos estén a 1M de velocidad en baudios |
| Los servos se descontrolan tras la calibración del centro | La pose no se configuró correctamente antes de calibrar | Repite "desactivar → colocar manualmente → calibración del centro" |
| La temperatura sube demasiado rápido | Carga excesiva o bloqueo | Comprueba si el mecanismo se agarrota; reduce la velocidad/aceleración |
| No se encuentra el servo tras cambiar su ID | Conflicto de ID o fallo de escritura | Restablece de fábrica y vuelve a escanear |
| Control remoto desincronizado | Los dos puertos tienen IDs que no coinciden | Confirma que los servos con el mismo ID estén en línea tanto en el puerto leader como en el follower |

---

## 📁 Estructura de directorios

```Plain Text
Juxi_ServoController/
├── docs/                    # Tutoriales por sistema (chino/inglés)
│   ├── zh/                  # Tutoriales en chino
│   │   ├── Windows教程.md
│   │   ├── Linux教程.md
│   │   └── macOS教程.md
│   └── en/                  # Tutoriales en inglés
│       ├── Windows.md
│       ├── Linux.md
│       └── macOS.md
├── src/
│   ├── gui/                  # GUI de PySide6
│   │   ├── factory_calibration_tool.py   # Herramienta principal (calibración de doble puerto + control remoto + cambio de idioma)
│   │   ├── ft_debugger.py                # Depurador FT (lectura/escritura de parámetros / copia de seguridad xdat)
│   │   ├── calibration_wizard.py         # Asistente de calibración de LeRobot
│   │   ├── theme_utils.py                # Tema claro
│   │   └── language_dialog.py            # Diálogo de selección de idioma
│   ├── tools/                # Herramientas de línea de comandos
│   ├── xdat_utils.py         # Lectura/escritura de archivos de parámetros xdat
│   ├── i18n*.py / i18n_translations/     # Internacionalización chino/inglés
│   ├── port_utils.py         # Detección de puerto serie
│   └── calibration_manager.py# Gestión de archivos de calibración de LeRobot
├── scservo_sdk/              # SDK de comunicación de servos FTServo
├── requirements.txt
└── setup.py                  # Script de comprobación del entorno
```
