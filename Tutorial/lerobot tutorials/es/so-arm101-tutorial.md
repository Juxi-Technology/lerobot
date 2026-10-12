[English](../en/so-arm101-tutorial.md) | [简体中文](../zh-hans/so-arm101-tutorial.md) | [繁體中文](../zh-hant/so-arm101-tutorial.md) | [Deutsch](../de/so-arm101-tutorial.md) | Español | [Français](../fr/so-arm101-tutorial.md) | [Italiano](../it/so-arm101-tutorial.md) | [日本語](../ja/so-arm101-tutorial.md) | [한국어](../ko/so-arm101-tutorial.md) | [Português (BR)](../pt-br/so-arm101-tutorial.md) | [Português (PT)](../pt-pt/so-arm101-tutorial.md)

<title>Tutorial del brazo robótico SO-ARM101</title>

# Descripción general del producto

El SO-ARM101 es un **brazo robótico de 6 grados de libertad, de bajo coste y totalmente de código abierto** desarrollado por el equipo de LeRobot bajo Hugging Face, diseñado para la iniciación educativa, la validación de investigación y la creación de prototipos industriales ligeros. Con una alta flexibilidad y un ecosistema de código abierto completo, reduce la barrera para aplicar la inteligencia encarnada y la tecnología robótica.

### 1. Diseño de hardware: alto rendimiento, modular y fácil de montar y personalizar

- **Material estructural**: la estructura principal combina piezas impresas en 3D con componentes de carga reforzados, con un diseño optimizado del cableado y de las articulaciones para evitar interferencias de movimiento, equilibrando ligereza y durabilidad; los usuarios pueden imprimir ellos mismos las piezas de repuesto o de ampliación.
- **Configuración de accionamiento**: el brazo Follower incorpora **6 servos de alto par de 12 V y 30 KG con encoder magnético**, combinados con realimentación de encoder magnético de 360° y un algoritmo de control PID: un movimiento fluido y sin vibraciones, alta precisión de posicionamiento repetitivo, gran potencia y desplazamiento preciso.
- **Sistema de visión**: incluye de serie un **sistema de visión inteligente de doble cámara**; la cámara del efector final captura el detalle del agarre a corta distancia, mientras que la cámara global cubre el entorno de trabajo. La fusión de los datos de ambas cámaras construye un modelo 3D y proporciona un rico soporte de datos para el aprendizaje por imitación.
- **Conexión de control**: incorpora una placa controladora de servos que se conecta directamente a un PC o a una Raspberry Pi mediante una interfaz USB-C: conexión plug and play, que simplifica el proceso de conexión del hardware y permite montar el entorno de control rápidamente.

### 2. Ecosistema de software: integración profunda con LeRobot y desarrollo de IA sin barreras

- **Compatibilidad con el marco principal**: profundamente adaptado al **marco de ML para robots de código abierto LeRobot** de Hugging Face, construido sobre PyTorch, con modelos preentrenados, conjuntos de datos para múltiples escenarios y un entorno de simulación integrados, y compatible con conocidos conjuntos de datos de código abierto como Stanford ALOHA.
- **Comunicación de baja latencia**: utiliza el **motor de flujo de datos distribuido DORA** para una interacción de baja latencia entre el hardware y los algoritmos; Python se ejecuta 17 veces más rápido que ROS2, y se admite la recarga en caliente del código para poder ajustar las políticas en tiempo real sin reiniciar.
- **Código abierto de pila completa**: los archivos de impresión 3D del hardware, el código de control del software, los scripts de entrenamiento de IA y todo el conjunto de tutoriales son **completamente de código abierto**; los usuarios pueden modificarlos y desarrollarlos libremente para implementar rápidamente ampliaciones de funciones personalizadas.

### 3. Escenarios de aplicación principales: adecuados para todo el proceso, desde la iniciación hasta el despliegue

1. **Iniciación a la educación en robótica**: ofrece un tutorial de principio a fin, desde el montaje del brazo y la programación básica hasta el despliegue de políticas de IA, con una interfaz de operación visual y código de ejemplo, para que los principiantes dominen rápidamente el control del robot y las habilidades de aplicación de IA.
2. **Validación de algoritmos de investigación**: centrado en la investigación de **aprendizaje por imitación y aprendizaje por refuerzo**, con soporte para registrar datos de operación humana mediante VR para entrenar el robot; un caso típico: a partir de 50 clips de vídeo de operación de 15 segundos, 2 horas de entrenamiento bastan para dominar tareas como doblar ropa, insertar una llave y clasificar materiales.
3. **Creación de prototipos industriales ligeros**: validación de soluciones de automatización a bajo coste, adecuada para escenarios como el **manejo de materiales, el montaje de precisión y la clasificación de piezas**, y que ofrece las funciones principales de un brazo robótico de grado industrial a un coste de gama de miles de yuanes para una validación rápida de prototipos.

### 4. Ventajas del producto

- **Relación calidad-precio extrema**: la versión básica parte de unos 100 USD, y el diseño de código abierto reduce los costes de adquisición y de desarrollo secundario, lo que lo hace adecuado para el despliegue en lote por parte de particulares, laboratorios y pequeñas y medianas empresas.
- **Código abierto en toda la cadena**: el hardware, el software y los tutoriales son totalmente abiertos y sin barreras técnicas, lo que permite personalizar y ampliar funciones libremente para adaptarse rápidamente a muchos escenarios.
- **Apto para el desarrollo de IA**: respaldado por el ecosistema LeRobot, llama a modelos preentrenados y conjuntos de datos con un solo clic, simplifica todo el flujo desde la recopilación de datos y el entrenamiento de políticas hasta el despliegue, y acelera la implantación de algoritmos de inteligencia encarnada.

### 5. Especificaciones del producto

| **Especificación** | **Detalles** |
|-|-|
| Grados de libertad | 6 ejes (giro/inclinación del hombro, flexión del codo, flexión/rotación de la muñeca, apertura/cierre de la pinza) |
| Material estructural | Piezas impresas en 3D (PLA+) |
| Motores de accionamiento | 12 \* servomotores Feetech STS3215 (alimentación de 12 V)  <br/>Relación de engranajes del brazo Follower STS3215-C018: 1/345  <br/>Relación de engranajes del brazo Leader STS3215-C001: 1/345 (hombro), STS3215-C044 1/191 (codo), STS3215-C046 1/147 (muñeca) |
| Capacidad de carga | Carga máxima del efector final 200 g (pinza cerrada) |
| Precisión de posicionamiento repetitivo | ±1,5 mm (afectada por la calibración y la holgura del motor) |
| Radio de trabajo | Alcance máximo del efector final 350 mm |
| Requisitos de alimentación | Leader: adaptador de 5 V 6 A; Follower: adaptador de 12 V 5 A (para demandas de alto par) |
| Interfaz de comunicación | Conexión directa USB-C a PC (transferencia de comandos de control) |
| Sistema de visión | Cámara (1080P@30FPS, FOV86° sin distorsión, o enfoque fijo 1080P@60FPS FOV100°) |
| Tipo de pinza | Pinza de PLA+, pinza de TPU y pinza paralela de dos dedos compatibles, rango de apertura de 0-50 mm, fuerza de agarre máxima 5 N |
| Marco de control | Biblioteca LeRobot basada en Python, que proporciona una API de control de motores (lerobot.control) |
| Modelos preentrenados | Admite algoritmos de aprendizaje por imitación como ACT (Action Chunking Transformer) y Diffusion Policy |
| Modelo ligero | Modelo de visión-lenguaje-acción SmolVLA (450 M de parámetros): ・Inferencia en CPU en tiempo real (funciona en MacBook) ・Respuesta asíncrona un 30 % más rápida ・Solo 64 tokens visuales por fotograma ・Visualización de estado: monitorización en tiempo real con la biblioteca rerun |
| Peso total | ≈1,2 kg (incluidos motores y cables) |
| Dimensiones montado | Diámetro de la base 120 mm, altura (totalmente extendido) 650 mm |
| Temperatura de funcionamiento | 0℃–40℃ (límite del servomotor) |
| Nivel de ruido | <45 dB (funcionamiento en vacío) |
| Tutorial para principiantes | Sí |
| GITHUB oficial | Sí |

![La imagen muestra los diagramas de dimensiones de los brazos Leader y Follower del brazo robótico SO-ARM101, junto con el nombre del producto, el material, las dimensiones y otra información. Los diagramas de dimensiones indican el tamaño de cada pieza; por ejemplo, el brazo Leader mide 525 mm de largo y el brazo Follower 532 mm de largo. El material del producto es PLA+ con optimización topológica, y las dimensiones del producto son 111x239x525 mm (Leader) y 111x173x532 mm (Follower). Esta imagen corresponde a la sección Especificaciones del producto del documento y presenta visualmente las especificaciones dimensionales del brazo.](../en/images/d01-01.png)

| **Elemento / nombre del paquete** | **Función / descripción** |
|-|-|
| Biblioteca LeRobot | Versión: ≥0.1.0 Marco de control principal: • API de Python (lerobot.control) ・Planificación de movimiento en tiempo real ・Procesamiento de flujos de datos de sensores |
| PyTorch | Versión: ≥2.0 Motor de inferencia de aprendizaje profundo (admite modelos como SmolVLA) |
| Transformers | Versión: ≥4.40.0 Biblioteca de modelos de Hugging Face (carga ACT/Diffusion Policy preentrenados) |
| rerun | Versión: ≥0.16.0 Herramienta de visualización del estado del robot en tiempo real (renderizado 3D de ángulos de articulación / trayectorias) |
| ROS 2 | Versión: Humble/Foxy Opcional: interfaz de controlador ROS2 (paquete soarm100_ros) |
| ACT | Action Chunking Transformer, predicción de acciones de secuencia larga (p. ej., tareas de agarre continuo) |
| Diffusion Policy | Política de difusión, control robusto en espacios de acción de alta dimensión (manipulación resistente a perturbaciones) |
| SmolVLA | Modelo de visión-lenguaje-acción, ejecución de instrucciones multimodales (p. ej., "agarra el bloque rojo") ・450 M de parámetros, funciona en CPU/GPU |

| **Categoría de función** | **Descripción de la función** |
|-|-|
| Control a nivel de articulación | ・Control independiente de ángulo/velocidad de 6 ejes (rango de ±180°) ・Protección de límites suaves de las articulaciones ・Realimentación en tiempo real de la temperatura / el voltaje del motor |
| Control en espacio cartesiano | ・Posicionamiento por coordenadas XYZ del efector final (precisión ±1,5 mm) ・Ajuste de orientación mediante ángulos de Euler (Roll/Pitch/Yaw) |
| Operación de la pinza | ・Ajuste de apertura continuo de 0-50 mm ・Ajuste dinámico de la fuerza de agarre (0,1-5 N) ・Agarre adaptable al grosor del objeto |
| Modo Leader/Follower | ・Enseñanza manual con el brazo Leader → imitación en tiempo real con el brazo Follower ・Grabación / reproducción de datos de acciones |

| **Categoría de función** | **Descripción de la función** |
|-|-|
| Aprendizaje por imitación | ・Grabación de datos de demostración humana → entrenamiento de modelos ACT/Diffusion Policy ・Compatibilidad con la transferencia de políticas multitarea (p. ej., apilar bloques → clasificar objetos) |
| Interacción multimodal | ・El modelo SmolVLA interpreta instrucciones en lenguaje natural (p. ej., "agarra el bloque azul") ・Ejecución de visión-acción de extremo a extremo |
| Interfaz de aprendizaje por refuerzo | ・Entorno compatible con Gymnasium ・Funciones de recompensa personalizadas (p. ej., tiempo de finalización de la tarea / optimización de energía) |
| Sistema de calibración | ・Calibración del punto cero Leader/Follower ・Calibración mano-ojo cámara-brazo ・Compensación automática del par de las articulaciones |
| Gestión de flujos de datos | ・Grabación / reproducción de conjuntos de datos en formato .h5 ・Sincronización en la nube con Hugging Face Hub ・Alineación de marcas de tiempo de los datos de sensores |
| Monitorización en tiempo real | ・Visualización con rerun de los ángulos de articulación / la trayectoria del efector final ・Alarmas de anomalías del motor (sobrecalentamiento / bloqueo) ・Diagnóstico de latencia de comunicación |
| Integración con ROS 2 | ・Publicar estados de las articulaciones (/joint_states) ・Suscribirse a comandos de control (/arm_controller) ・Transferencia de flujos de nubes de puntos (/depth_points) |
| Despliegue multiplataforma | • Linux/Windows/macOS (API de Python) ・Contenedorización con Docker ・Control remoto web (interfaz FastAPI) |
