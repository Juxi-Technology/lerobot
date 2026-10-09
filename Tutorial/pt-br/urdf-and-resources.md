[English](../en/urdf-and-resources.md) | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | [Español](../es/urdf-and-resources.md) | [Français](../fr/urdf-and-resources.md) | [Italiano](../it/urdf-and-resources.md) | [日本語](../ja/urdf-and-resources.md) | [한국어](../ko/urdf-and-resources.md) | Português (BR) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>Arquivos URDF e recursos de referência</title>

# Arquivo [URDF](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf) oficial do Lerbot



## URDF Studio

https://urdf.d-robotics.cc/



## Controle de simulação ROS2 (implemente você mesmo)

https://github.com/holmsslk/so-arm-moveit-hardware



## Interface gráfica oficial do LeRobot

https://github.com/huggingface/leLab

O LeLab é um aplicativo web que reúne todo o fluxo de trabalho do LeRobot — calibração, teleoperação, gravação, treinamento, reprodução — em uma única interface de navegador. Basta conectar o braço robótico, abrir o aplicativo e começar a trabalhar. Sem trabalho complicado na linha de comando e sem precisar de teclado.

🤗 O ponto de entrada web nativo do LeRobot, projetado para levar novos usuários de "pronto para usar" a "treinar a primeira policy" em poucos minutos.

🤗 Instale e execute tudo com um único comando.



# Controlando o braço Follower pelo celular

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## Desenvolvimento de robótica na nuvem: dispositivos ROS 2 e simulação Isaac Sim LeRobot e streaming de dados na AWS

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## Configurar IDs de servo e calibração de centro na interface web

https://bambot.org/feetech.js?lang=zh

1. Digite 0 ou 1 conforme o modelo do servo e clique em "Connect"

![A imagem mostra a interface de conexão para definir IDs de servo e calibração de centro na interface web. A interface tem uma seção "Connect" com um menu suspenso de taxa de baud, atualmente definida como "1,000,000 bps (Index 0)"; um menu suspenso de protocolo, atualmente definido como "0=STS/SMS"; e um botão "Connect". Na parte inferior da interface aparece "Status: Disconnected". A imagem está intimamente ligada ao contexto: depois de digitar 0 ou 1 conforme o modelo do servo e clicar em "Connect", os servos com IDs 1~6 são escaneados para confirmar o servo com o ID correspondente — esta é uma interface-chave nesse fluxo.](../en/images/d68-01.png)

2. Escaneie os servos com IDs 1\~6; use FOUND nos resultados da varredura para confirmar o servo com o ID correspondente. Por exemplo, na imagem o servo de ID 1 foi encontrado

![A imagem mostra a interface de varredura de servos no URDF Studio oficial do Lerbot. A interface mostra um ID inicial de 1 e um ID final de 6, com um botão "Start scan" abaixo. Nos resultados da varredura, escanear o ID1 encontrou o ID1239, enquanto escanear do ID2 ao ID6 reporta, em cada caso, "ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0". Esta imagem está relacionada à operação de varredura de servos no URDF Studio oficial do Lerbot descrita no contexto e apresenta visualmente o processo de varredura e seus resultados.](../en/images/fix-01.png)

3. Definição de ID e calibração de centro

① Ajuste a entrada do ID de servo atual para o ID do servo escaneado

② Digite um número em "ID management" e clique em "Change ID" para definir o ID

③ Calibração de centro (o centro do servo STS3215 é 2047 e o do servo SCS0009 é 511)

Servo STS: digite 2047 em "Position control" e clique em "Set"

Servo SCS: digite 511 em "Position control" e clique em "Set"

![A imagem mostra a interface de controle de servo individual do Lerbot. O "Current servo ID" aparece como 1; abaixo, em "ID management", há o número 1 e um botão "Change ID", com a mensagem "Success: ID changed to 1" logo abaixo. Na área Position Control há um botão "Read position" mostrando a posição 2047, ao lado de um botão "Set". Esta imagem está relacionada à seção "Definição de ID e calibração de centro" do documento e apresenta visualmente a interface para definir IDs de servo e calibrar o centro, ajudando os usuários a entender como fazer essas configurações no Lerbot.](../en/images/d68-02.png)
