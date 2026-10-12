[English](../en/index.md) | [简体中文](../zh-hans/index.md) | [繁體中文](../zh-hant/index.md) | [Deutsch](../de/index.md) | Español | [Français](../fr/index.md) | [Italiano](../it/index.md) | [日本語](../ja/index.md) | [한국어](../ko/index.md) | [Português (BR)](../pt-br/index.md) | [Português (PT)](../pt-pt/index.md)

# Contenido

## **Haz clic en los dos iconos de la esquina superior izquierda para expandir la lista completa de capítulos**

![La imagen muestra un icono formado por un punto y tres líneas paralelas. Este icono aparece en un documento que presenta LeRobot, cuyo contexto describe LeRobot como el marco de software de robots inteligentes encarnados de código abierto de HuggingFace que reduce la barrera de entrada para la recopilación de datos, el entrenamiento de algoritmos y el despliegue de inferencia en aprendizaje por refuerzo y aprendizaje por imitación (VLA), con el aprendizaje por imitación (VLA) como foco principal. Este icono puede representar el marco de software LeRobot o una función relacionada.](../en/images/d02-01.png)

![La imagen muestra un icono de botón de reproducción, un triángulo blanco, situado en la esquina inferior izquierda del marco. Este icono se relaciona con la presentación que hace el documento de LeRobot, que es el marco de software de robots inteligentes encarnados de código abierto de HuggingFace y que reduce la barrera de entrada para la recopilación de datos, el entrenamiento de algoritmos y el despliegue de inferencia en aprendizaje por refuerzo y aprendizaje por imitación (VLA), con el aprendizaje por imitación (VLA) como foco principal. Este icono puede indicar contenido de vídeo o demostración para ayudar a los usuarios a entender el material de LeRobot.](../en/images/d02-02.png)

![La imagen muestra el texto "Speedrunning Embodied Intelligence VLA" sobre un fondo degradado claro. En el marco, una mano sostiene un objeto blanco mientras otra mano maneja un brazo robótico con cableado rojo. En la esquina inferior derecha aparece un bocadillo con el texto "Grab!". La imagen se relaciona con la presentación que hace el documento de LeRobot, un marco de software de robots inteligentes encarnados que reduce la barrera del aprendizaje por imitación (VLA); esta imagen puede tener como objetivo mostrar visualmente el uso de VLA en la manipulación robótica y su papel en el aprendizaje por imitación.](../en/images/d02-03.png)

## ¿Qué es la inteligencia encarnada?

Inteligencia con un cuerpo. Conecta la IA con diversas entidades de hardware físicas, como:

Perros robots cuadrúpedos, robots humanoides bípedos, robots con ruedas y patas, drones, coches autónomos

## ¿Qué es LeRobot?

LeRobot es el `marco de software de robots inteligentes encarnados` de código abierto de HuggingFace

Dirección de GitHub: https://github.com/huggingface/lerobot

Reduce la barrera de entrada para la **recopilación de datos, el entrenamiento de algoritmos y el despliegue de inferencia** en aprendizaje por refuerzo y **aprendizaje por imitación (VLA)**, con el **aprendizaje por imitación (VLA)** como foco principal

- ¿Qué robots se pueden desarrollar con LeRobot?

Desde el brazo robótico SO-ARM 101 y el carrito LeKiwi, de gama de miles de yuanes, hasta el brazo AgileX piper, de decenas de miles de yuanes, el brazo StarAI de Huaxinjing y la mano diestra Hope-JR, y llegando al robot humanoide Unitree G1, de cientos de miles de yuanes. LeRobot se ha convertido en el estándar para la recopilación de datos y el entrenamiento de algoritmos en la industria de la inteligencia encarnada.

También puedes adaptar tu propio robot al marco LeRobot.

- Conjuntos de datos y modelos de LeRobot

LeRobot define su propio formato de conjunto de datos para aprendizaje por imitación. Puedes ver, usar, descargar y entrenar con todos los conjuntos de datos y modelos públicos de HuggingFace, y también puedes subir tus propios conjuntos de datos a HuggingFace.

## ¿Qué es el brazo robótico SO-ARM 101?

Este tutorial toma como ejemplo el brazo robótico SO-ARM 101; utiliza piezas estructurales impresas en 3D y servos Feetech, con un coste muy bajo.

Es un cuerpo de inteligencia encarnada que incluso un estudiante sin recursos puede permitirse, y es uno de los cuerpos recomendados oficialmente por LeRobot.

El brazo consta de dos brazos: un brazo Leader y un brazo Follower. Cada brazo tiene 5 grados de libertad más 1 grado de libertad de la pinza.

## ¿Qué configuración de equipo necesito?

Un portátil Windows normal puede con todo hasta el entrenamiento.

Un Mac normal puede con todo.

Una máquina Ubuntu con una GPU NVIDIA puede con todo.

En este tutorial usamos una [plataforma de GPU en la nube](https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1) para entrenar modelos, así que tu propio ordenador no necesita una configuración de gama alta.

## ¿Qué es el **aprendizaje por imitación y VLA**?

Los humanos arrastran el robot para demostrar y recopilar un conjunto de datos. Ese conjunto de datos se usa después para entrenar un algoritmo de aprendizaje por imitación, que finalmente se despliega en el robot, permitiéndole imitar acciones humanas de forma autónoma y generalizar al entorno real. No se necesita teleoperación ni control remoto.

Por ejemplo, en el vídeo de arriba, una persona arrastra el brazo robótico SO-ARM para agarrar un cangrejo de río, mojarlo en condimento y dejarlo caer en aceite caliente, y el brazo acaba realizando esta acción por sí solo. Incluso con un cangrejo nuevo, puede reaccionar y completar la acción en cualquier momento.

El aprendizaje por imitación también tiene un nombre moderno y de vanguardia: VLA (modelo grande de Visión-Lenguaje-Acción). Este es además el campo de investigación de inteligencia encarnada que se desarrolla más rápido en la actualidad, que atrae las inversiones más candentes, que vive la competencia entre China y Estados Unidos más feroz, que disfruta del ecosistema de código abierto más próspero, que atrae una intensa atención mediática y que arrastra a innumerables estudiantes de máster y doctorado.

Los algoritmos que LeRobot adapta principalmente son los de aprendizaje por imitación, como ACT, Diffusion Policy, SmolVLA, Pi0, Pi0.5, Wall-OSS y otros.

El aprendizaje por imitación de este tutorial es exclusivamente VLA.
