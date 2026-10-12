[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/windows.md) | Português (PT)

# Computador Windows

## Ligar a câmara ao computador

```Shell
lerobot-find-cameras opencv
```

![Esta imagem é a janela da linha de comandos do Windows, mostrando erros de ligação da câmara e resultados de deteção de dispositivos. No topo há um erro: "ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range". Abaixo lista as câmaras detetadas, incluindo Camera #0 e Camera #1, com o respetivo nome, tipo, API de backend, configuração predefinida do fluxo, formato, origem, largura, altura e taxa de fotogramas; na parte inferior há erros como "lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0". Isto corresponde ao cenário de erro mencionado no documento, "a câmara não consegue ligar-se, mas a troca de câmaras no Tencent Meeting ainda abre normalmente", e é o feedback real do erro em tempo de execução antes de modificar o código do backend do OpenCV.](../../en/images/d32-01.png)

## Teleoperação com a imagem da câmara apresentada

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

A janela do rerun.io abre-se, mostrando a trajetória de cada articulação dos servos em tempo real, juntamente com a imagem da câmara ao vivo

e guarda as imagens no diretório `C:\Users\username\outputs\captured_images`

![A imagem mostra a janela do rerun.io, apresentando as trajetórias das articulações dos servos e a imagem da câmara ao vivo em tempo real. À esquerda está a interface de blueprint com opções como "teleoperation". Ao centro está o gráfico de trajetórias, mostrando dados de posição das articulações como "observation_wrist_rot.pos". À direita está a imagem da câmara, mostrando a cena a partir da perspetiva do robô. No canto superior direito mostra "Waiting for data on rerun: http://127.0.0.1:9876/remote...", com informação da fonte de dados em baixo. Esta imagem está relacionada com o conteúdo que descreve a janela do rerun.io a mostrar a imagem da câmara em tempo real, apresentando visualmente o efeito.](../../en/images/d32-02.png)

## Se encontrar o seguinte erro

A câmara não consegue ligar-se, mas a troca de câmaras no Tencent Meeting ainda abre normalmente

![A imagem mostra a interface da linha de comandos do Windows com resultados de deteção de câmaras. No topo mostra "Detected Cameras" e informação relacionada com câmaras, como nome, tipo, ID e API de backend. Abaixo há um erro que indica que, ao executar lerobot_find_cameras_openpyc, a câmara OpenCV não conseguiu ligar-se ou ser configurada, sugerindo executar lerobot_find_cameras_opencv para encontrar uma câmara disponível, e que, não sendo possível ligar nenhuma câmara, a gravação de imagens será abortada. Esta imagem corresponde ao contexto do problema de ligação da câmara, apresentando visualmente o erro.](../../en/images/d32-03.png)

Modifique o ficheiro `lerobot\src\lerobot\cameras\utils.py` para alterar o backend do OpenCV para `cv2.CAP_SHOW`

![A imagem mostra o código da função `get_cv2_backend()` no ficheiro `lerobot\\src\\lerobot\\cameras\\utils.py`. Quando o sistema é Windows, a função devolve `int(cv2.CAP_DSHOW)`, utilizado para usar MSMF em vez de AVFOUNDATION no Windows. O código contém também um comentário sobre `cv2.CAP_MSMF`, e como outros sistemas, como Darwin (macOS) e Linux, são tratados. Esta imagem está relacionada com a operação de modificar o ficheiro `lerobot\\src\\lerobot\\cameras\\utils.py` para alterar o backend do OpenCV para `cv2.CAP_SHOW`, e é um exemplo de modificação de código.](../../en/images/d32-04.png)

> Este é um erro que nem o Doubao consegue resolver; é tudo porque a biblioteca lerobot está demasiado encapsulada e é muito difícil para os principiantes depurarem

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## Ligar várias câmaras, teleoperação com as imagens das câmaras apresentadas

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![A imagem mostra a janela do rerun.io utilizada para a teleoperação com imagens de câmara. À esquerda está um gráfico de trajetórias que mostra os dados de trajetória de várias articulações, como observation_wrist_l_pos e observation_wrist_r_pos. À direita, em cima está a imagem da câmara ao vivo e em baixo a janela do Tencent Meeting. No canto superior direito mostra "Waiting for data on rerun: http://127.0.0.1:9678/remote...". Esta imagem está relacionada com o conteúdo sobre ligar várias câmaras e mostrar imagens de câmara durante a teleoperação, apresentando visualmente o efeito.](../../en/images/d32-05.png)
