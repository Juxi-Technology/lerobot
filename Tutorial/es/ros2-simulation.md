[English](../en/ros2-simulation.md) | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | [Deutsch](../de/ros2-simulation.md) | Español | [Français](../fr/ros2-simulation.md) | [Italiano](../it/ros2-simulation.md) | [日本語](../ja/ros2-simulation.md) | [한국어](../ko/ros2-simulation.md) | [Português (BR)](../pt-br/ros2-simulation.md) | [Português (PT)](../pt-pt/ros2-simulation.md)

# Control de simulación ROS2

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

Un espacio de trabajo completo de ROS 2 para el brazo robótico SO-ARM101 de 6 grados de libertad, que abarca la descripción del robot, un controlador de hardware integrado, la simulación en Gazebo y la planificación de movimiento con MoveIt 2.

El SO-ARM101 es el brazo follower de código abierto de segunda generación codiseñado por [TheRobotStudio](https://www.therobotstudio.com/) y la comunidad de [LeRobot](https://huggingface.co/lerobot), que utiliza seis servos STS3215, una placa controladora de servos y piezas de PLA+ impresas en 3D.

<callout emoji="📌">
**Nota: el brazo requiere calibración del centro; realiza la calibración del centro con todas las articulaciones en el centro de su rango de movimiento**
</callout>

## Estructura de paquetes

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

Plataforma de destino: **ROS 2 Humble / Jazzy**.

---

## Preparar el entorno de ROS 2

Antes de compilar este proyecto, asegúrate de que ROS 2 y los componentes relevantes estén instalados en tu sistema.

### Requisitos del sistema

- Ubuntu 22.04 (recomendado) o 24.04
- Al menos 4 GB de RAM
- Se requiere un puerto serie USB para el modo de hardware real

### 0.1  Instalar ROS 2 Humble

```Bash
# Establecer la configuración regional
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# Añadir el repositorio de software de ROS 2
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Instalar ROS 2 Humble Desktop
sudo apt update
sudo apt install ros-humble-desktop
```

### 0.2  Instalar herramientas de compilación y dependencias

```Bash
# herramienta de compilación colcon
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  Establecer variables de entorno

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  Establecer los permisos del puerto serie (necesario para hardware real)

**Configuración permanente (recomendada)**:

```Bash
sudo usermod -a -G dialout $USER
# Surte efecto después de cerrar sesión y volver a iniciarla
```

**Configuración temporal (hay que rehacerla después de cada reinicio)**:

```Bash
sudo chmod 666 /dev/ttyACM0
```

## Instalar el espacio de trabajo

```Markdown
# Paso 1  Crear el espacio de trabajo
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# Paso 2  Colocar el código fuente
cp -r /path/to/SO-ARM101_ROS2 ./

# Paso 3  Instalar las dependencias del sistema
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# Paso 4  Compilar todos los paquetes
colcon build --symlink-install

# Paso 5  Cargar el entorno  ← ejecuta esto en cada terminal nueva
source install/setup.bash
```

<callout emoji="💡">
**Nota sobre hardware real**: el paquete `so_arm_hardware` viene integrado. No hace falta instalar ningún controlador adicional;  
se comunica directamente con los servos STS3215 a través del puerto serie usando el protocolo SCS.
</callout>

## Verificación visual

Empieza por aquí: es la ruta más sencilla, sin controladores y sin hardware.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

RViz muestra el modelo completo del robot; arrastra los deslizadores para verificar que cada articulación se mueve correctamente.

---

## Prueba del controlador (hardware virtual / modo Mock)

Tampoco se necesita un robot real: todo se ejecuta en memoria.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

Cuando el registro muestre lo siguiente, estará listo:

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**Nota**: el modo de simulación inicia solo dos controladores (`joint_state_broadcaster` y  
`joint_trajectory_controller`). Se ha eliminado `gripper_controller`; la pinza  
se controla junto con las 6 articulaciones mediante `joint_trajectory_controller`.
</callout>

### Responsabilidades de los controladores

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## Planificación de movimiento con MoveIt (hardware Mock)

**Solo se necesita una terminal**: MoveIt inicia internamente la pila de controladores.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

Cuando se abra la ventana de RViz:

1. En el panel **MotionPlanning**, configura **Planning Group → manipulator**
2. **Start State → `<current>`**, **Goal State → extended**
3. Haz clic en **Plan** y luego en **Execute**

Poses predefinidas disponibles: `open`, `zero`, `extended`, `rest`.

### 4.1  Recorrido por la interfaz de MoveIt

Después de que arranque RViz, el panel **MotionPlanning** aparece a la izquierda con las siguientes pestañas principales:

#### Pestaña Planning

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Parámetros de planificación

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **Consejo para la primera prueba**: configura Velocity y Acceleration en 0,3 para ralentizar el movimiento por seguridad.

#### Pestaña Scene Objects

- Añade obstáculos (Box / Sphere / Cylinder) para la comprobación de colisiones
- Importa / exporta escenas
- MoveIt planifica automáticamente esquivando los obstáculos

#### Pestaña Stored States

- Guarda poses del brazo de uso frecuente
- Poses predeterminadas: `open`, `zero`, `extended`, `rest`

### 4.2  Flujo de trabajo básico

#### Método A: Arrastre interactivo (recomendado)

1. En la vista 3D, localiza el **marcador interactivo** en el extremo del brazo (flechas y anillos de colores)
2. Arrastra las flechas para trasladar la posición del efector final, y arrastra los anillos para rotar la orientación
3. El sistema resuelve la IK automáticamente y actualiza los ángulos de las articulaciones en tiempo real
4. Haz clic en **Plan** para ver la trayectoria planificada (naranja)
5. Cuando estés satisfecho, haz clic en **Execute** para ejecutarla

> Si el arrastre se entrecorta, parte de la pose predefinida `rest` antes de arrastrar.

#### Método B: Poses predefinidas

1. Desplegable **Query Goal State** → selecciona `open` / `extended` / `rest`, etc.
2. Haz clic en **Update**
3. Haz clic en **Plan**
4. Haz clic en **Execute**

#### Método C: Establecer los ángulos de las articulaciones manualmente

1. **Query Goal State** → pestaña **Joints**
2. Arrastra cada deslizador de articulación para establecer el ángulo objetivo
3. Referencia de rangos de las articulaciones:

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. Haz clic en **Update**
2. Haz clic en **Plan**
3. Haz clic en **Execute**

#### Método D: Objetivo válido aleatorio

Haz clic en **Random Valid** para generar una pose alcanzable aleatoria y luego Plan → Execute.

### 4.3  Notas de seguridad

1. **Ve despacio en el primer uso**: configura Velocity / Acceleration en 0,1–0,3
2. **Parada de emergencia**: pulsa Ctrl+C en cualquier momento para terminar el programa, o corta la alimentación
3. **Límites de las articulaciones**: MoveIt no planificará más allá de los rangos de `joint_limits.yaml`, pero asegúrate de que estén configurados correctamente
4. **Hardware real**: asegúrate de que haya suficiente espacio alrededor del brazo antes de ejecutar

### Resumen de la configuración de MoveIt

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Simulación en Gazebo

La simulación en Gazebo requiere **4 terminales ejecutándose a la vez**. Sigue el orden estrictamente.

### 5.1  Iniciar la simulación en Gazebo  (Terminal 1)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Espera a que aparezca la ventana de Gazebo; el robot queda brevemente suspendido en el aire y luego aterriza.

### 5.2  Cargar el controlador de trayectoria  (Terminal 2)

De forma predeterminada, Gazebo activa solo `forward_position_controller`; debes cambiar manualmente a  
`joint_trajectory_controller`:

```Markdown
#  Terminal 2
source ~/so101_ws/install/setup.bash

# Paso A — desactivar forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# Paso B — cargar y activar joint_trajectory_controller con el spawner
ros2 run controller_manager spawner joint_trajectory_controller

# Paso C — verificar
ros2 control list_controllers
```

Salida esperada:

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ ¡No uses primero `ros2 control load_controller`! Deja el controlador en el  
estado `unconfigured`, lo que impide que el spawner lo active. Si ya lo hiciste,  
ejecuta primero `unload_controller` y vuelve a empezar.
</callout>

### 5.3  Iniciar move_group  (Terminal 3)

```Bash
#  Terminal 3
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py use_sim_time:=True
```

### 5.4  Iniciar RViz  (Terminal 4)

```Bash
#  Terminal 4
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

Cuando RViz esté listo:

1. **Planning Group → manipulator**
2. **Goal State → open** (o `extended`, `rest`)
3. Haz clic en **Plan** y luego en **Execute**

Las articulaciones del brazo en Gazebo seguirán el movimiento.

<callout emoji="💡">
**Nota**: debido a la limitación de ganancia del PID en la versión Humble de `gz_ros2_control`,  
puede que la pinza no se abra físicamente en Gazebo (el registro de ejecución sigue informando de éxito).  
El modo Mock y el hardware real no tienen este problema.
</callout>

### 5.5  Modo sin interfaz gráfica (sin GUI)

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  Solución de problemas: fallos de carga repetidos

Si el spawner sigue informando de `Failed to activate controller`, haz lo siguiente para reiniciar por completo:

```Bash
# 1. Descargar el controlador bloqueado
ros2 control unload_controller joint_trajectory_controller

# 2. Desactivar forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# 3. Volver a generar (spawn)
ros2 run controller_manager spawner joint_trajectory_controller
```

## Hardware real

Requisito previo: el brazo SO-ARM101 está montado y la placa controladora de servos está conectada al PC mediante USB.

### 6.1  Iniciar los controladores (opcional)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

El complemento `so_arm_hardware` hace automáticamente lo siguiente:

1. Abre el puerto serie
2. Escanea los 6 IDs de servo (1–6)
3. Verifica que todos los servos respondan
4. Activa el par y lee la posición actual

Cuando los controladores estén listos, abre dos terminales más para iniciar MoveIt:

```Bash
#  Terminal 2 — move_group
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py
```

```Bash
#  Terminal 3 — RViz
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

### 6.2  MoveIt (arranque con un solo comando)

> El siguiente comando **sustituye** al 6.1 (no ejecutes ambos a la vez; detén los comandos del 6.1): `demo.launch.py` ya incluye internamente la pila de controladores.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  Solución de problemas del puerto serie

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  La visualización de RViz no coincide con la pose real

Si la pose del brazo en RViz no coincide con el hardware real (por ejemplo, un desfase de articulación o un informe de colisión falso):

1. Confirma que los servos se han calibrado en el centro
2. Ajusta el `position_offset` de cada articulación en `so_arm101.ros2_control.xacro`
3. Fórmula de conversión: `new offset = current offset + (currently displayed rad / 0.00153398)`
4. Recompila el paquete `so_arm101_description` después del cambio

---

## Preguntas frecuentes

### P1: "package not found" al compilar

**R**: Asegúrate de que todas las dependencias del sistema estén instaladas correctamente y de que el entorno de ROS 2 esté cargado:

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### P2: "Permission denied" al acceder al puerto serie durante el arranque

**R**: Comprueba los permisos del puerto serie:

```Bash
# Solución temporal
sudo chmod 666 /dev/ttyACM0

# Solución permanente (surte efecto tras cerrar sesión)
sudo usermod -a -G dialout $USER
```

### P3: La planificación de MoveIt falla con "Motion planning start tree could not be initialized"

**R**: Normalmente hay dos causas:

1. **Articulaciones fuera de los límites**: comprueba la salida `FixStartStateBounds` en el registro. La tolerancia actual es  
0,3 rad; si el exceso está dentro de ese rango, pasa. De lo contrario, ajusta `start_state_max_bounds_error`  
o comprueba los desfases de los servos.
2. **Estado inicial en colisión**: comprueba la salida `FixStartStateCollision` en el registro. Si  
aparece "Unable to find a valid state nearby", la pose actual está autocolisionando.  
El brazo puede estar en una pose plegada (por ejemplo, la pinza tocando el hombro), o los desfases son incorrectos.  
Ajusta `position_offset` y vuelve a intentarlo.

### P4: El brazo no se mueve después de Execute

**R**: Comprueba los estados de los controladores:

```Bash
ros2 control list_controllers
```

Asegúrate de que `joint_trajectory_controller` esté `active`. Si no, vuelve a generarlo (spawn):

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### P5: RViz arranca despacio o se queda colgado

**R**: Esto es normal. Al arrancar, MoveIt carga el modelo URDF, los complementos de comprobación de colisiones,  
los solucionadores de cinemática, etc.; el primer arranque tarda unos 10 segundos.

### P6: La trayectoria planificada no es fluida o da tirones

**R**: Prueba lo siguiente:

- Cambia a otro planificador (elige `RRTConnect` en el desplegable Planner de RViz)
- Aumenta Planning Time a 10 segundos
- Asegúrate de que el objetivo esté dentro del espacio de trabajo (pruébalo con `Random Valid`)

### P7: La pinza no se mueve en Gazebo

**R**: Es una limitación de ganancia del PID codificada de forma fija en la versión Humble de `gz_ros2_control`  
(fijada en 0,1) que no se puede sobrescribir mediante parámetros URDF. Execute informa de éxito en el registro,  
pero la pinza no se abre en la simulación física de Gazebo. El modo Mock y el hardware real no tienen este problema.

## Apéndice: referencia rápida de parámetros de launch

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Estructura de directorios

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # Biblioteca de utilidades de Python
├── so_arm101_description/          # URDF · controladores · mallas · RViz · MuJoCo
├── so_arm101_moveit_config/        # SRDF de MoveIt 2 · planificadores · archivos launch
├── so_arm_gz/                      # launch de simulación de Gazebo
├── so_arm_hardware/                # Controlador serie SCS integrado (C++)
└── Simulation/                     # URDF de CAD original (conservado como referencia)
```
