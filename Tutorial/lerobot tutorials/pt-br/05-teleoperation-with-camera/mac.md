[English](../../en/05-teleoperation-with-camera/mac.md) | [简体中文](../../zh-hans/05-teleoperation-with-camera/mac.md) | [繁體中文](../../zh-hant/05-teleoperation-with-camera/mac.md) | [Deutsch](../../de/05-teleoperation-with-camera/mac.md) | [Español](../../es/05-teleoperation-with-camera/mac.md) | [Français](../../fr/05-teleoperation-with-camera/mac.md) | [Italiano](../../it/05-teleoperation-with-camera/mac.md) | [日本語](../../ja/05-teleoperation-with-camera/mac.md) | [한국어](../../ko/05-teleoperation-with-camera/mac.md) | Português (BR) | [Português (PT)](../../pt-pt/05-teleoperation-with-camera/mac.md)

# Computador Mac

## Conectar a Câmera ao Computador

```Shell
lerobot-find-cameras opencv
```

![A imagem mostra o resultado da detecção após conectar uma câmera a um Mac. Ela lista as duas câmeras geradas automaticamente, a câmera externa e a câmera frontal interna do Mac. O Fps da câmera externa é 60.00024 e o Fps da câmera interna é 30.0. Esta imagem está relacionada ao conteúdo sobre conectar uma câmera a um Mac, apresentando visualmente o resultado da detecção após a conexão e ajudando os usuários a entender o tipo, o ID, a API de backend e a taxa de quadros de cada câmera.](../../en/images/d31-01.png)

## Uma Câmera, Teleoperação com o Feed da Câmera Exibido

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

Após a execução, a teleoperação começa

A janela do rerun.io abre, mostrando a trajetória de cada articulação dos servos em tempo real, juntamente com o feed ao vivo da câmera

e salva as imagens no diretório `~/username/outputs/captured_images`

![A imagem mostra a janela do rerun.io que abre quando a teleoperação começa após a execução. À esquerda estão gráficos das trajetórias de várias articulações dos servos, apresentados como curvas que mostram o movimento de diferentes articulações. À direita, o feed da câmera da cena interna é mostrado em tempo real, onde é possível ver uma mesa, cadeiras e alguns objetos. Também há algumas informações em forma de barras na parte inferior. Esta imagem está intimamente relacionada ao contexto, apresentando visualmente as trajetórias das articulações dos servos e o feed ao vivo da câmera durante a teleoperação, e também ilustra que as imagens são salvas no diretório especificado.](../../en/images/d31-02.png)

## Várias Câmeras, Teleoperação com os Feeds das Câmeras Exibidos

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

![A imagem mostra a janela do rerun.io usada para teleoperação com vários feeds de câmera. À esquerda está o feed ao vivo da câmera, mostrando objetos sobre uma mesa; à direita estão gráficos de dados mostrando as trajetórias de diferentes articulações, como observation_wip. Na parte inferior há uma área Streams listando dados de várias articulações. No canto superior direito há informações de dados, como Application ID e Source IP. Esta imagem corresponde ao conteúdo "Várias câmeras, teleoperação com feeds de câmera", apresentando visualmente os feeds e os dados durante a teleoperação.](../../en/images/d31-03.png)
