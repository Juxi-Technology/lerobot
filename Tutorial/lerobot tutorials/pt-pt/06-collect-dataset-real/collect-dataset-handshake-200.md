[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Português (BR)](../../pt-br/06-collect-dataset-real/collect-dataset-handshake-200.md) | Português (PT)

# Recolher um conjunto de dados por demonstração — Handshake 200

## Criar um repositório de conjunto de dados no HuggingFace

https://huggingface.co/new-dataset

![A imagem mostra a interface para criar um novo repositório de conjunto de dados no HuggingFace. "Owner" é apresentado como TommyZihao, o nome do conjunto de dados é "lerobot_zihao_dataset_shake200", a "License" está definida como mit e o tipo de conjunto de dados é "Public", visível por qualquer pessoa, embora apenas o proprietário do conjunto de dados ou os membros da organização possam fazer commits. Em baixo, indica que, após criar o conjunto de dados, pode carregar ficheiros através da interface web ou do git, e há um botão "Create dataset" na parte inferior. Esta imagem está relacionada com o conteúdo sobre criar um repositório de conjunto de dados no HuggingFace, e mostra a interface da operação de criar o conjunto de dados.](../../en/images/d37-01.png)

## Eliminar qualquer conjunto de dados existente com o mesmo nome (se existir)

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Recolha do conjunto de dados Shake200

Uma câmara, a recolher um conjunto de dados - computador Mac

```Shell
lerobot-record \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 1920, height: 1080, fps: 60, fourcc: "MJPG"}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm \
    --display_data=true \
    --dataset.repo_id=Tommymy/lerobot_my_dataset_shake200 \
    --dataset.num_episodes=200 \
    --dataset.single_task="Shanke Hands" \
    --dataset.push_to_hub=false \
    --dataset.episode_time_s=12 \
    --dataset.reset_time_s=1
```

## Durante a recolha

<grid>
<column width-ratio="0.508765">
![A imagem mostra a interface do terminal durante a recolha de um conjunto de dados num Mac. Apresenta a saída de SvtInfo() e SvtInfo(), incluindo o número de versão, o compilador e a arquitetura. Apresenta também os parâmetros de configuração SvtConfig(), como largura, altura, taxa de fotogramas e preset. Em baixo há saída marcada como "INFO" e "INFO 0", como "Starting second pass: moving the moving atom to the beginning of the file". Esta imagem está relacionada com o conteúdo "Durante a recolha", apresentando visualmente a configuração e a informação mostradas no terminal durante a recolha.](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![A imagem mostra a saída do terminal durante a recolha de um conjunto de dados com o script Open_Duck_Mini_Runtime_2 num Mac. Mostra SVT e outros parâmetros de configuração de codificação de vídeo, como gop size e key - frame type, e apresenta a versão do codificador de vídeo e a data de compilação. Em baixo há registos de ficheiros MP4, como "Starting second pass: moving the moov atom to the beginning of the file". Esta imagem está relacionada com o fluxo de trabalho de recolha de conjuntos de dados, apresentando visualmente o feedback do terminal durante a recolha.](../../en/images/d37-03.png)
</column>
</grid>

Controlos das setas do teclado:  
→ (seta para a direita) Termina o episódio atual antecipadamente; avança para o episódio seguinte.  
← (seta para a esquerda) Cancela o episódio atual; volta a gravá-lo.  
ESC, para imediatamente, codifica o vídeo e carrega o conjunto de dados.

## Recolha concluída — Diretório de gravação do conjunto de dados

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
