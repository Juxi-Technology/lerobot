[English](../../en/06-collect-dataset-real/collect-dataset-handshake-200.md) | [简体中文](../../zh-hans/06-collect-dataset-real/collect-dataset-handshake-200.md) | [繁體中文](../../zh-hant/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Deutsch](../../de/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Español](../../es/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Français](../../fr/06-collect-dataset-real/collect-dataset-handshake-200.md) | [Italiano](../../it/06-collect-dataset-real/collect-dataset-handshake-200.md) | [日本語](../../ja/06-collect-dataset-real/collect-dataset-handshake-200.md) | [한국어](../../ko/06-collect-dataset-real/collect-dataset-handshake-200.md) | Português (BR) | [Português (PT)](../../pt-pt/06-collect-dataset-real/collect-dataset-handshake-200.md)

# Coletando um Conjunto de Dados por Demonstração — Handshake 200

## Criar um Repositório de Dataset no HuggingFace

https://huggingface.co/new-dataset

![A imagem mostra a interface para criar um novo repositório de conjunto de dados no HuggingFace. "Owner" é exibido como TommyZihao, o nome do conjunto de dados é "lerobot_zihao_dataset_shake200", "License" está definida como mit, e o tipo de conjunto de dados é "Public", visível por qualquer pessoa, enquanto apenas o proprietário do conjunto de dados ou membros da organização podem fazer commits. Abaixo, observa-se que, após criar o conjunto de dados, você pode enviar arquivos pela interface web ou por git, e há um botão "Create dataset" na parte inferior. Esta imagem está relacionada ao conteúdo sobre criar um Repositório de Dataset no HuggingFace, e mostra a interface da operação de criação de conjunto de dados.](../../en/images/d37-01.png)

## Excluir Qualquer Conjunto de Dados Existente com o Mesmo Nome (Se Houver)

```Shell
sudo rm -rf /Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```

## Coleta do Conjunto de Dados Shake200

Uma câmera, coletando um conjunto de dados - computador Mac

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

## Durante a Coleta

<grid>
<column width-ratio="0.508765">
![A imagem mostra a interface do terminal durante a coleta de um conjunto de dados em um Mac. Ela exibe a saída de SvtInfo() e SvtInfo(), incluindo número de versão, compilador e arquitetura. Também apresenta os parâmetros de configuração de SvtConfig(), como largura, altura, taxa de quadros e preset. Abaixo há uma saída marcada como "INFO" e "INFO 0", como "Starting second pass: moving the moving atom to the beginning of the file". Esta imagem está relacionada ao conteúdo "Durante a Coleta", apresentando visualmente a configuração e as informações mostradas no terminal durante a coleta.](../../en/images/d37-02.png)
</column>
<column width-ratio="0.491235">
![A imagem mostra a saída do terminal durante a coleta de um conjunto de dados com o script Open_Duck_Mini_Runtime_2 em um Mac. Ela mostra parâmetros de configuração de codificação de vídeo, como SVT e outros, como tamanho de gop e tipo de quadro-chave, e apresenta a versão do codificador de vídeo e a data de compilação. Abaixo há registros de arquivos MP4, como "Starting second pass: moving the moov atom to the beginning of the file". Esta imagem está relacionada ao fluxo de trabalho de coleta do conjunto de dados, apresentando visualmente o retorno do terminal durante a coleta.](../../en/images/d37-03.png)
</column>
</grid>

Controles pelas teclas de seta do teclado:  
→ (Seta para a direita) Encerra o episódio atual antecipadamente; passa para o próximo episódio.  
← (Seta para a esquerda) Cancela o episódio atual; grava-o novamente.  
ESC, para imediatamente, codifica o vídeo e envia o conjunto de dados.

## Coleta Concluída — Diretório de Salvamento do Conjunto de Dados

```Shell
/Users/tommy/.cache/huggingface/lerobot/Tommymy/lerobot_my_dataset_shake200
```
