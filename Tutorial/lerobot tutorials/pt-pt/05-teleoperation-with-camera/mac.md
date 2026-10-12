[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | [Português (BR)](../../pt-br/05-teleoperation-with-camera/mac.md) | Português (PT)

# Computador Mac

## Ligar a câmara ao computador

```Shell
lerobot-find-cameras opencv
```

![A imagem mostra o resultado da deteção após ligar uma câmara a um Mac. Lista as duas câmaras geradas automaticamente, a câmara externa e a câmara frontal integrada do Mac. O Fps da câmara externa é 60.00024 e o Fps da câmara integrada é 30.0. Esta imagem está relacionada com o conteúdo sobre ligar uma câmara a um Mac, apresentando visualmente o resultado da deteção após a ligação e ajudando os utilizadores a compreender o tipo, ID, API de backend e taxa de fotogramas de cada câmara.](../../en/images/d31-01.png)

## Uma câmara, teleoperação com a imagem da câmara apresentada

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

Após a execução, a teleoperação inicia

A janela do rerun.io abre-se, mostrando a trajetória de cada articulação dos servos em tempo real, juntamente com a imagem da câmara ao vivo

e guarda as imagens no diretório `~/username/outputs/captured_images`

![A imagem mostra a janela do rerun.io aberta quando a teleoperação inicia após a execução. À esquerda estão gráficos das trajetórias de várias articulações dos servos, apresentados como curvas que mostram o movimento das diferentes articulações. À direita, a imagem da câmara da cena interior é mostrada em tempo real, onde se podem ver uma mesa, cadeiras e alguns objetos. Existe também alguma informação em forma de barras na parte inferior. Esta imagem está estreitamente relacionada com o contexto, apresentando visualmente as trajetórias das articulações dos servos e a imagem da câmara ao vivo durante a teleoperação, e ilustra também que as imagens são guardadas no diretório especificado.](../../en/images/d31-02.png)

## Várias câmaras, teleoperação com as imagens das câmaras apresentadas

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}, side: {type: opencv, index_or_path: 1, width: 1920, height: 1080, fps: 30, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

![A imagem mostra a janela do rerun.io utilizada para a teleoperação com várias imagens de câmara. À esquerda está a imagem da câmara ao vivo, mostrando objetos sobre uma secretária; à direita estão gráficos de dados que mostram as trajetórias de diferentes articulações, como observation_wip. Na parte inferior está uma área Streams que lista os dados de várias articulações. No canto superior direito há informação de dados como Application ID e Source IP. Esta imagem corresponde ao conteúdo "Várias câmaras, teleoperação com imagens de câmara", apresentando visualmente as imagens e os dados durante a teleoperação.](../../en/images/d31-03.png)
