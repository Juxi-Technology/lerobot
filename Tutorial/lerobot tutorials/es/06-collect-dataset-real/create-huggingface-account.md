[English](../../en/06-collect-dataset-real/create-huggingface-account.md) | [简体中文](../../zh-hans/06-collect-dataset-real/create-huggingface-account.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/create-huggingface-account.md) | [Deutsch](../../de/06-collect-dataset-real/create-huggingface-account.md) | Español | [Français](../../fr/06-collect-dataset-real/create-huggingface-account.md) | [Italiano](../../it/06-collect-dataset-real/create-huggingface-account.md) | [日本語](../../ja/06-collect-dataset-real/create-huggingface-account.md) | [한국어](../../ko/06-collect-dataset-real/create-huggingface-account.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/create-huggingface-account.md) | [Português (PT)](../../pt-pt/06-collect-dataset-real/create-huggingface-account.md)

# Registrar una cuenta de Hugging Face (opcional)

## Configurar un espejo de HuggingFace para China

- Ubuntu

```Shell
sudo nano ~/.bashrc

# Añadir esto al final del archivo
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.bashrc
echo $HF_ENDPOINT

# Salida
# https://hf-mirror.com
```

- Mac

```Shell
sudo nano ~/.zshrc

# Añadir esto al final del archivo
export HF_ENDPOINT=https://hf-mirror.com
```

```Shell
source ~/.zshrc

# Salida
# https://hf-mirror.com
```



## Crear un token

https://huggingface.co/settings/tokens

![La imagen muestra la interfaz de la plataforma Hugging Face, con el área del avatar y del perfil del usuario a la izquierda y contenido de modelos y conjuntos de datos a la derecha. A la derecha, una flecha roja señala la opción "Access Tokens", situada bajo "Settings". El contexto menciona que, tras crear un token, hay que usar las teclas arriba/abajo para seleccionar y pegar la clave; esta imagen presenta visualmente dónde está "Access Tokens" en la plataforma, se relaciona con el paso de registrar el token después de crearlo y es la interfaz para configurar los permisos correspondientes tras crear un token.](../../en/images/d34-01.png)

![La imagen muestra la página Access Tokens de la plataforma Hugging Face. En la barra de navegación izquierda, la opción "Access Tokens" está seleccionada. A la derecha se muestra la información de User Access Tokens, incluidos nombre, valor, fecha de última actualización, fecha de último uso y permisos. En la parte superior derecha hay un botón "Create new token" resaltado con una flecha roja. Esta imagen se relaciona con la sección "Crear un token" y presenta visualmente dónde crear un nuevo token, lo que ayuda al usuario a comprender la página concreta para crear un token en Hugging Face.](../../en/images/d34-02.png)

![Esta imagen muestra la interfaz para crear un nuevo token de acceso en la plataforma Hugging Face, con el título de la página "Create new Access Token". Hay que configurar tres cosas: seleccionar el tipo de token llamado "Write", establecer el nombre como "so-arm101" y, a continuación, hacer clic en el botón "Create token". Estas operaciones están marcadas con recuadros rojos y los números 1, 2 y 3 para guiar al usuario en la creación de un token con permiso de escritura. Esto corresponde a los pasos para crear un token, un paso clave para obtener la clave necesaria y vincular Hugging Face.](../../en/images/d34-03.png)

![Esta imagen es la página de guardado del token de acceso de una cuenta de Hugging Face; su contenido central es un recordatorio de guardar bien el valor del token, porque después de cerrar la ventana emergente ya no se podrá ver y, si se pierde, habrá que volver a crearlo. La página muestra la clave de acceso generada hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx, con el nombre so-arm101 y permiso de escritura. Hay un botón "Copy" señalado por una flecha roja y resaltado con un recuadro rojo, utilizado para copiar el token, y un botón "Done" en la parte inferior derecha para finalizar la operación actual. Esta imagen corresponde al paso de registrar o vincular el token de la cuenta de Hugging Face.](../../en/images/d34-04.png)

## Registrar el token

Por ejemplo, el mío es:

```Shell
hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## Vincular el token

```Shell
hf auth login

hf auth whoami
```

![La imagen muestra el inicio de sesión con un token de Hugging Face en la línea de comandos. Tras introducir el comando "hf auth login", aparece el mensaje "? How would you like to log in?" y se muestra la opción "Paste an access token". Esto se relaciona con el paso "Vincular el token" e indica que, tras seleccionar y pegar la clave con las teclas arriba/abajo, la pantalla de inicio de sesión pregunta cómo quieres iniciar sesión, momento en el que puedes elegir pegar un token de acceso para iniciar sesión y completar la vinculación del token de Hugging Face.](../../en/images/d34-05.png)

> Usa las teclas arriba/abajo para seleccionar y pegar la clave

![Esta imagen muestra la operación de una cuenta de Hugging Face en la línea de comandos, con un recuadro rojo que resalta que el token activo actual es "so-arm101-upload", que se ha guardado en la ruta especificada. La línea de comandos cerró la sesión y volvió a iniciarla; el sistema avisó de que iniciar sesión en Hugging Face requiere un token y, tras pegar el token con éxito, mostró el permiso del token como write, luego completó el guardado y, por último, mostró la información del token activo actual. Este contenido corresponde al paso "Vincular el token".](../../en/images/d34-06.png)

> Pantalla de éxito

## Crear un repositorio de conjunto de datos

<grid>
<column width-ratio="0.434605">
![Esta imagen muestra un menú desplegable en la interfaz de Hugging Face; en la parte superior se muestra el usuario con sesión iniciada como "juxi-admin", y el menú enumera varias opciones de funciones, como new model, new space y new bucket. La opción resaltada con un recuadro rojo es "New Dataset", que corresponde al paso "Crear un repositorio de conjunto de datos". Esta opción es el punto de entrada para crear un repositorio de conjunto de datos, a través del cual el usuario puede completar su creación.](../../en/images/d34-07.png)
</column>
<column width-ratio="0.565395">
![La imagen muestra la interfaz para crear un Dataset Repo en Hugging Face. En "Dataset name" se introduce el valor "so-arm101", "License" se establece en "apache-2.0" y se selecciona la opción "Public", lo que significa que cualquiera puede ver este Dataset y solo tú puedes hacer commits. Esta imagen se relaciona con el paso "Crear un repositorio de conjunto de datos" y muestra una de las pantallas de configuración, lo que ayuda al usuario a comprender la información clave que hay que rellenar al crear uno.](../../en/images/d34-08.png)
</column>
</grid>

![La imagen muestra la página del conjunto de datos "so - arm101" en la plataforma Hugging Face. En la parte superior hay una barra de búsqueda y una barra de navegación que dan acceso a secciones como Models y Datasets. En el centro se muestra la información del conjunto de datos, incluida License apache - 2.0 y un tamaño de archivo de 2.53 kB. Debajo hay una sección "Getting started with your dataset" que te anima a añadir metadatos y completar la ficha del conjunto de datos para mejorar su visibilidad, y ofrece la opción de editar la ficha del conjunto de datos. A la derecha hay botones "Copy to bucket" y "Edit dataset card", y un registro de descarga de archivos del conjunto de datos. Esta imagen se relaciona con la creación de un Dataset Repo y muestra la interfaz de gestión del conjunto de datos.](../../en/images/d34-09.png)
