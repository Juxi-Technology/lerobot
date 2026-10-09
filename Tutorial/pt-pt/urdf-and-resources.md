[English](../en/urdf-and-resources.md) | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | [Español](../es/urdf-and-resources.md) | [Français](../fr/urdf-and-resources.md) | [Italiano](../it/urdf-and-resources.md) | [日本語](../ja/urdf-and-resources.md) | [한국어](../ko/urdf-and-resources.md) | [Português (BR)](../pt-br/urdf-and-resources.md) | Português (PT)

<title>URDF Files and Reference Resources</title>

# [Ficheiro URDF](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf) oficial do Lerbot



## URDF Studio

https://urdf.d-robotics.cc/



## Controlo de simulação ROS2 (implemente-o você mesmo)

https://github.com/holmsslk/so-arm-moveit-hardware



## Interface gráfica oficial do LeRobot

https://github.com/huggingface/leLab

O LeLab é uma aplicação web que reúne todo o fluxo de trabalho do LeRobot — calibração, teleoperação, gravação, treino, reprodução — numa única interface de browser. Basta ligar o braço robótico, abrir a aplicação e pode começar a trabalhar. Sem trabalho fastidioso de linha de comandos e sem necessidade de introduzir nada pelo teclado.

🤗 O ponto de entrada web nativo do LeRobot, concebido para permitir que os novos utilizadores passem de "pronto a usar" a "treinar a sua primeira política" em questão de minutos.

🤗 Instale e execute tudo com um único comando.



# Controlar o Braço Follower a Partir de um Telefone

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## Desenvolvimento de robótica na nuvem: dispositivos ROS 2 e simulação e streaming de dados LeRobot no Isaac Sim na AWS

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## Definir IDs dos servos e calibração de centro na interface web

https://bambot.org/feetech.js?lang=zh

1. Introduza 0 ou 1 consoante o modelo do servo e, em seguida, clique em "Connect"

![A imagem mostra a interface de ligação para definir IDs dos servos e a calibração de centro na interface web. A interface tem uma secção "Connect" com uma lista pendente de taxa de baud, atualmente definida para "1,000,000 bps (Index 0)"; uma lista pendente de extremidade de protocolo, atualmente definida para "0=STS/SMS"; e um botão "Connect". Na base da interface aparece "Status: Disconnected". A imagem está estreitamente ligada ao contexto: depois de introduzir 0 ou 1 consoante o modelo do servo e clicar em "Connect", são digitalizados os servos com IDs 1~6 para confirmar o servo com o ID correspondente — esta é uma interface essencial nesse fluxo.](../en/images/d68-01.png)

2. Digitalize os servos com IDs 1\~6; utilize FOUND nos resultados da digitalização para confirmar o servo com o ID correspondente. Por exemplo, na imagem foi encontrado o servo com ID 1

![A imagem mostra a interface de digitalização de servos no URDF Studio oficial do Lerbot. A interface mostra um ID inicial de 1 e um ID final de 6, com um botão "Start scan" por baixo. Nos resultados da digitalização, ao digitalizar o ID1 foi encontrado o ID1239, enquanto ao digitalizar do ID2 ao ID6 cada um reporta "ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0". Esta imagem relaciona-se com a operação de digitalização de servos no URDF Studio oficial do Lerbot descrita no contexto e apresenta visualmente o processo de digitalização e os seus resultados.](../en/images/fix-01.png)

3. Definição do ID e calibração de centro

① Defina a introdução do ID do servo atual para o ID do servo digitalizado

② Introduza um número em "ID management" e clique em "Change ID" para definir o ID

③ Calibração de centro (o centro do servo STS3215 é 2047, o centro do servo SCS0009 é 511)

Servo STS: introduza 2047 em "Position control" e clique em "Set"

Servo SCS: introduza 511 em "Position control" e clique em "Set"

![A imagem mostra a interface de controlo de servo único do Lerbot. O "Current servo ID" aparece como 1; por baixo, em "ID management", está o número 1 e um botão "Change ID", com a mensagem "Success: ID changed to 1" por baixo. Na área Position Control há um botão "Read position" a mostrar a posição 2047, ao lado de um botão "Set". Esta imagem relaciona-se com a secção "Definição do ID e calibração de centro" do documento e apresenta visualmente a interface para definir IDs dos servos e calibrar o centro, ajudando os utilizadores a compreender como fazer estas definições no Lerbot.](../en/images/d68-02.png)
