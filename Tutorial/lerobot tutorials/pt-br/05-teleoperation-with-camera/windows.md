[English](../../en/05-teleoperation-with-camera/windows.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/windows.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/windows.md) | [Deutsch](../../de/05-teleoperation-with-camera/windows.md) | [Español](../../es/05-teleoperation-with-camera/windows.md) | [Français](../../fr/05-teleoperation-with-camera/windows.md) | [Italiano](../../it/05-teleoperation-with-camera/windows.md) | [日本語](../../ja/05-teleoperation-with-camera/windows.md) | [한국어](../../ko/05-teleoperation-with-camera/windows.md) | Português (BR) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/windows.md)

# Computador Windows

## Conectar a Câmera ao Computador

```Shell
lerobot-find-cameras opencv
```

![Esta imagem é a janela de linha de comando do Windows, mostrando erros de conexão de câmera e resultados de detecção de dispositivos. No topo há um erro: "ERROR: @2.323 global obsensor_uvc_stream_channel.cpp:163 cv::obsensor::getStreamChannelGroup Camera index out of range". Abaixo, ela lista as câmeras detectadas, incluindo Camera #0 e Camera #1, com seus nomes, tipo, API de backend, configuração de fluxo padrão, formato, origem, largura, altura e taxa de quadros; na parte inferior há erros como "lerobot.scripts.lerobot:Failed to connect or configure OpenCV camera 0". Isso corresponde ao cenário de erro mencionado no documento, "a câmera não consegue conectar, mas trocar de câmera no Tencent Meeting ainda abre normalmente", e é o retorno do erro real em tempo de execução antes de modificar o código do backend do OpenCV.](../../en/images/d32-01.png)

## Teleoperação com o Feed da Câmera Exibido

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

A janela do rerun.io abre, mostrando a trajetória de cada articulação dos servos em tempo real, juntamente com o feed ao vivo da câmera

e salva as imagens no diretório `C:\Users\username\outputs\captured_images`

![A imagem mostra a janela do rerun.io, exibindo as trajetórias das articulações dos servos e o feed ao vivo da câmera em tempo real. À esquerda está a interface de blueprint com opções como "teleoperation". No meio está o gráfico de trajetória, mostrando dados de posição das articulações como "observation_wrist_rot.pos". À direita está o feed da câmera, mostrando a cena da perspectiva do robô. No canto superior direito é exibido "Waiting for data on rerun: http://127.0.0.1:9876/remote...", com informações da fonte de dados abaixo. Esta imagem está relacionada ao conteúdo que descreve a janela do rerun.io mostrando o feed da câmera em tempo real, apresentando visualmente o efeito.](../../en/images/d32-02.png)

## Se Você Encontrar o Seguinte Erro

A câmera não consegue conectar, mas trocar de câmera no Tencent Meeting ainda abre normalmente

![A imagem mostra a interface de linha de comando do Windows com resultados de detecção de câmera. No topo é exibido "Detected Cameras" e informações relacionadas à câmera, como nome, tipo, ID e API de backend. Abaixo há um erro informando que, ao executar lerobot_find_cameras_openpyc, a câmera OpenCV falhou ao conectar ou ser configurada, sugerindo que você execute lerobot_find_cameras_opencv para encontrar uma câmera disponível, e que nenhuma câmera pode ser conectada, então o salvamento das imagens será abortado. Esta imagem corresponde ao contexto do problema de conexão da câmera, apresentando visualmente o erro.](../../en/images/d32-03.png)

Modifique o arquivo `lerobot\src\lerobot\cameras\utils.py` para alterar o backend do OpenCV para `cv2.CAP_SHOW`

![A imagem mostra o código da função `get_cv2_backend()` no arquivo `lerobot\\src\\lerobot\\cameras\\utils.py`. Quando o sistema é Windows, a função retorna `int(cv2.CAP_DSHOW)`, usado para usar MSMF em vez de AVFOUNDATION no Windows. O código também contém um comentário sobre `cv2.CAP_MSMF`, e como outros sistemas, como Darwin (macOS) e Linux, são tratados. Esta imagem está relacionada à operação de modificar o arquivo `lerobot\\src\\lerobot\\cameras\\utils.py` para alterar o backend do OpenCV para `cv2.CAP_SHOW`, e é um exemplo de modificação de código.](../../en/images/d32-04.png)

> Este é um bug que nem o Doubao consegue resolver; é tudo porque a biblioteca lerobot está encapsulada de forma muito profunda, e é muito difícil para iniciantes depurar

<figure view-type="Preview">[Attachment: wx_camera_1768139334330.mp4](../../en/images/wx_camera_1768139334330.mp4)</figure>

## Conectar Várias Câmeras, Teleoperação com os Feeds das Câmeras Exibidos

```Shell
lerobot-teleoperate --robot.type=so101_follower --robot.port=COM6 --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 640, height: 480, fps: 60, fourcc: "MJPG"}}" --teleop.type=so101_leader --teleop.port=COM7 --teleop.id=my_leader_arm --display_data=true
```

![A imagem mostra a janela do rerun.io usada para teleoperação com feeds de câmera. À esquerda está um gráfico de trajetória mostrando dados de trajetória de várias articulações, como observation_wrist_l_pos e observation_wrist_r_pos. À direita, no topo está o feed ao vivo da câmera e embaixo está a janela do Tencent Meeting. No canto superior direito é exibido "Waiting for data on rerun: http://127.0.0.1:9678/remote...". Esta imagem está relacionada ao conteúdo sobre conectar várias câmeras e mostrar os feeds das câmeras durante a teleoperação, apresentando visualmente o efeito.](../../en/images/d32-05.png)
