[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | Português (BR) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>Tutorial de montagem do kit do braço robótico SO-ARM101</title>

<callout emoji="💡">
Observação: pule este tutorial se você tiver um braço pré-montado
</callout>

## Peças impressas em 3D do braço follower

![Esta imagem mostra as peças impressas em 3D do braço follower necessárias para montar o braço robótico SO-ARM101, todas peças de plástico PLA branco dispostas sobre uma superfície clara com veios de madeira. As peças incluem conectores de vários formatos, uma estrutura em forquilha com grade, uma peça tipo base com furos, um braço de suporte em forquilha de formato especial e assim por diante, correspondendo ao ponto do tutorial de que a extremidade do braço follower é uma garra. Essas peças são as moldadas básicas do braço follower do braço e são os objetos manipulados na etapa de remoção dos suportes, correspondendo diretamente às peças impressas em 3D do braço follower apresentadas no tutorial.](../en/images/d09-01.jpg)

## Peças impressas em 3D do braço leader

![A imagem mostra peças impressas em 3D do braço robótico SO-ARM101. Diversas peças impressas em 3D pretas estão dispostas ordenadamente no quadro, com linhas azuis nas bordas de algumas peças. Essas peças incluem estruturas dos braços leader e follower, como a garra, o manete e o gatilho, além de conectores. A imagem corresponde à seção "Peças impressas em 3D do braço leader" do documento e apresenta visualmente a aparência das peças impressas em 3D, fornecendo uma referência para as etapas posteriores de remoção dos suportes restantes e de distinção dos servos.](../en/images/d09-02.jpg)

Os braços leader e follower são muito parecidos; só a extremidade é diferente

O leader tem um manete e um gatilho; o follower tem uma garra

## Removendo os suportes restantes das peças impressas em 3D

Confira cada furo, abertura, ranhura e grade, especialmente os cinco furos que lembram a peça "cinco pontos" do mahjong

Esta etapa é muito importante; caso contrário, você não conseguirá parafusar mais adiante

## Distinguindo os quatro servos

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">Tamanho grande</td><td vertical-align="middle">Tamanho pequeno</td><td vertical-align="middle">Tensão (V)</td><td vertical-align="middle">Relação de engrenagem</td><td vertical-align="middle">Junta do braço</td><td vertical-align="middle">Quantidade</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Todas as juntas do follower</td><td vertical-align="middle">6</td></tr></tbody></table>

> A relação de engrenagem é a razão entre "velocidade do motor : velocidade do eixo de saída do servo"; por exemplo, 1:345 significa que o motor gira 345 vezes para o eixo de saída girar uma vez.
> 
> Uma relação de engrenagem alta multiplica o torque por meio do trem de engrenagens, então ele pode mover uma carga mais pesada (como o braço follower)
> 
> Mas, ao mesmo tempo, o eixo de saída gira mais devagar (porque há "redução")
> 
> Arrastar a junta também exige mais esforço

Abaixo estão os modelos e as relações de engrenagem de todos os servos deste projeto; as partes sublinhadas são os seus números

![A imagem mostra os modelos, as tensões e as relações de engrenagem dos servos usados no braço. À esquerda está o braço leader, com dois modelos, C046 (7.4V, 1:147) e C044 (7.4V, 1:191); à direita está o braço follower, com dois modelos, C001 (7.4V, 1:345) e C047 (12V, 1:345). A imagem está intimamente ligada ao contexto, que apresenta em detalhes os modelos, as tensões e as relações de engrenagem dos servos dos braços leader e follower; esta imagem mostra visualmente essas figuras-chave para ajudar os leitores a entender melhor a configuração dos servos.](../en/images/d09-03.png)

![A imagem mostra quatro caixas de servos rotuladas "STS3215". Cada caixa traz impressa a palavra "SPECIFICATION" e inclui parâmetros como torque, velocidade e dimensões, por exemplo um torque de 9.2kg·cm/127.98oz·in(6V). O STS3215-C001 tem torque de 12.5kg·cm/173.88oz·in(6V), e o STS3215-C046 tem torque de 16kg·cm/220.58oz·in(7V). Esses servos são o modelo usado em todas as juntas do braço follower, correspondendo ao braço follower apresentado no documento, e são usados na instalação dos servos nas etapas de montagem posteriores.](../en/images/d09-04.jpg)

## Distinguindo os dois adaptadores de energia

Adaptador de energia 5V 6A 30W: alimenta os servos de 7.4V (braço leader), preto

Adaptador de energia 12V 5A 60W: alimenta os servos de 12V (braço follower), branco

## Baixando a ferramenta de depuração de servo da Feetech

### PC Windows

https://gitee.com/ftservo/fddebug

Baixe [`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z), extraia e execute o programa exe dentro dele

### Ubuntu e Mac (o arquivo inclui um tutorial)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![Esta imagem é uma ilustração auxiliar do tutorial de montagem do kit do braço robótico SO-ARM101, correspondente à seção sobre distinguir os adaptadores de energia. Ela mostra dois modelos de servo e suas posições de montagem, STS3215-C001 e STS3215-C018, e também identifica servos como o STS3215-C004, correspondentes às diferentes juntas do braço. A figura também lista os parâmetros desses dois servos, incluindo velocidade de rotação, torque de travamento, precisão do servo, recursos de proteção e feedback de parâmetros, fornecendo uma referência para a seleção e a instalação dos servos durante a montagem do braço.](../en/images/d09-05.jpg)

**Versão Pro: o braço leader usa um adaptador de energia de 5V6A, e o braço follower usa um adaptador de energia de 12V5A**

A configuração do ID do servo, a calibração do ângulo do servo e a montagem devem ser feitas antes; consulte o [tutorial de montagem oficial](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# Etapa 1: Definir os IDs dos servos e instalar os chifres dos servos (exceto o servo 5)

<grid>
<column width-ratio="0.500000">
![A imagem mostra a interface da ferramenta de depuração de host da Feetech. A interface tem três abas, "Debug", "Program" e "Upgrade", com "Program" selecionada no momento. Informações principais: 1. Nas configurações de comunicação, o número da porta é COM6 e a taxa de baud é 1000000; 2. Nas operações de servo, escrita síncrona, escrita assíncrona e saída de torque estão todas marcadas; 3. No feedback do servo, parâmetros como tensão, corrente, temperatura e posição mostram todos 0; 4. Na busca de servo, o id 1 está selecionado, modelo ST53215. Esta imagem está relacionada às operações de depuração descritas acima, como definir IDs de servo e instalar o chifre do servo, e apresenta a interface da ferramenta de depuração.](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![A imagem mostra a interface da ferramenta de depuração de host da Feetech, usada para definir IDs de servo. A interface tem três abas, "Debug", "Program" e "Upgrade", com "Program" selecionada no momento. Na área "Center calibration", o número do ID é 4, com um botão "Save" à direita. O lado esquerdo da interface mostra o ID do servo, o modelo e outras informações. Esta imagem está relacionada ao conteúdo "Etapa 1: Definir os IDs dos servos e instalar os chifres dos servos (exceto o servo 5)" do documento e apresenta a interface da operação de definição de ID do servo, mostrando visualmente onde o número do ID é definido.](../en/images/d09-07.png)
</column>
</grid>

1. Abra a ferramenta de depuração de host da Feetech, selecione a porta COM, defina a taxa de baud como um milhão e clique em "Open"
2. Clique em "Search"; quando "STS3215" aparecer, clique em "Stop" e depois clique em "STS3215"
3. Selecione "Debug" na parte superior; você pode arrastar o controle deslizante para girar o servo, ou clicar em "Scan" para fazê-lo ir e voltar. Confirme que o servo funciona normalmente
4. Selecione "Program" na parte superior
5. Clique em "Center calibration" para definir a posição atual do eixo de rotação do servo como o centro (0-4095)
6. Clique em "ID", defina o número de ID do servo correspondente no canto inferior direito e clique em "Save". Observe que o número é em algarismos arábicos simples, sem letras.
7. Desconecte o cabo que liga o servo à placa de controle
8. Conecte o cabo do servo ao servo

O servo 1 recebe dois cabos; os outros servos recebem apenas um cabo por enquanto

![A imagem mostra a instalação dos servos durante a montagem do kit do braço SO-ARM101. O quadro contém o braço follower e o braço leader, com o braço follower numerado 123456 e o braço leader numerado 123456. Os servos estão rotulados com relações de engrenagem de 1:345, 1:191 e 1:147. Abaixo está a placa de controle, conectada a dois cabos, um branco e um preto. Esta imagem está relacionada às etapas de montagem acima e apresenta visualmente as posições e os números de montagem dos servos, ajudando quem monta a associar os servos à placa de controle com precisão.](../en/images/d09-08.png)

<callout emoji="💡">
De novo: certifique-se de que o ID de junta e a relação de engrenagem de cada servo correspondam exatamente ao **SO-ARM101**.
</callout>

Todo motor no barramento tem um ID único. Motores novos geralmente vêm com um ID padrão `1`. Para garantir que a comunicação entre os motores e o controlador funcione, primeiro precisamos definir um ID único para cada motor. Além disso, a velocidade de transmissão de dados no barramento é determinada pela taxa de baud. Para se comunicarem entre si, o controlador e todos os motores precisam ser configurados com a mesma taxa de baud; os servos deste braço usam uma taxa de baud de 100000.

Para isso, primeiro precisamos conectar o controlador a cada motor, um de cada vez, para podermos configurá-los. Como gravamos esses parâmetros na área não volátil da memória interna do motor (EEPROM), isso só precisa ser feito uma vez.

Se você estiver reutilizando motores de outro robô, talvez também precise fazer esta etapa, porque os IDs e as taxas de baud podem não coincidir.

O vídeo abaixo mostra a sequência de etapas para definir os IDs dos motores.

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Use a ferramenta de host de servo da Feetech para definir os IDs dos servos e calibrar o centro. Os IDs são definidos de 1 a 6!

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu e Mac

<callout emoji="💡">
Se você precisar da ferramenta de host de servo da Feetech, consulte a [ferramenta de depuração de servo da Feetech](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb) acima
</callout>

Primeiro, conclua a configuração do ambiente seguindo a página de [instalação oficial do LeRobot](https://huggingface.co/docs/lerobot/installation)

<callout emoji="💡">
Lembre-se de ativar o ambiente virtual e entrar no diretório src/lerobot correspondente
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. Encontre a porta USB do braço. Para encontrar a porta correta de cada braço, execute o script utilitário duas vezes::

```Plain Text
lerobot-find-port
```

Exemplo de saída ao identificar a porta do braço Leader (por exemplo `/dev/tty.usbmodem575E0031751` em um Mac, ou possivelmente `/dev/ttyACM0` no Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

Exemplo de saída ao identificar a porta do braço Follower (por exemplo `/dev/tty.usbmodem575E0032081`, ou possivelmente `/dev/ttyACM1` no Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
Lembre-se de desconectar o conector USB, caso contrário a porta não será detectada.
</callout>

2. Conecte o PC à placa driver de servo do braço follower com um cabo USB e ligue-a. Depois execute o comando a seguir. Troque --robot.port=/dev/ttyACM0 no comando pela porta que você encontrou. Por exemplo, se a porta que você encontrou for /dev/ttyACM1, troque por --robot.port=/dev/ttyACM1

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

Você verá a seguinte saída.

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

Seguindo as instruções, conecte o servo da garra. Certifique-se de que ele é o único servo conectado à placa driver de servo e que esse servo ainda não está conectado a nenhum outro servo. Depois de pressionar **[Enter]**, o script define automaticamente o ID e a taxa de baud desse servo. Os IDs são definidos de 6 a 1!

Depois disso, você deverá ver o seguinte:

```Python
'gripper' motor id set to 6
```

Em seguida, a próxima saída é:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**Observação** Repita o procedimento acima para cada servo, seguindo as instruções.
Como nos servos anteriores, certifique-se de que ele é o único servo conectado à placa driver e que o próprio servo não está conectado a nenhum outro servo.
</callout>

Antes de pressionar **Enter** a cada vez, verifique com atenção as conexões dos cabos. Por exemplo, o cabo de alimentação pode se soltar ao manusear a placa de circuito.

Quando você tiver concluído todas as etapas, o script termina automaticamente e os servos estão prontos para uso. Agora você pode conectar, um a um, o conector de 3 pinos de cada servo e ligar o cabo do primeiro servo (o servo de "rotação do ombro" com ID 1) à placa driver. A placa driver agora pode ser montada na base do braço.

Repita as mesmas etapas para o braço leader.

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# Etapa 2: Montagem

<callout emoji="💡">
- As etapas de montagem do braço follower são essencialmente as mesmas do braço leader. A única diferença é que, após a etapa 12, o efetuador final (garra e manete) é instalado de forma diferente.
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
Instalando a placa driver de servo: primeiro monte os 4 distanciadores de latão, depois fixe a placa driver com quatro parafusos M2.5\*8
</callout>

<grid>
<column width-ratio="0.525947">
![Instale os quatro distanciadores de latão](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![Fixe a placa driver de servo com parafusos M2.5*8](../en/images/d09-10.webp)
</column>
</grid>

![Monte no braço e faça a fiação](../en/images/d09-11.png)

**Versão Pro: o braço leader preto usa um adaptador de energia de 5V6A, e o braço follower branco usa um adaptador de energia de 12V5A**







# Definir IDs de servo e calibração de centro na interface web

https://bambot.org/feetech.js?lang=zh

1. Digite 0 ou 1 conforme o modelo do servo e clique em "Connect"

![A imagem mostra a interface "Connect" no tutorial de montagem do kit do braço. À esquerda da interface está a palavra "Connect", e à direita estão um menu suspenso "Baud rate" definido como 1,000,000 bps (Index 0) e uma caixa de entrada para "Protocol end (0=STS/SMS, 1=SCS)" definida como 0, com um retângulo vermelho em torno do número "1" ao lado da caixa de entrada. Abaixo há um botão verde "Connect", com um retângulo vermelho em torno do número "2" ao lado dele. Na parte inferior aparece "Status: Disconnected". Esta imagem corresponde ao conteúdo acima, "Digite 0 ou 1 conforme o modelo do servo e clique em 'Connect'", e apresenta visualmente as configurações da operação de conexão.](../en/images/d09-12.png)

2. Escaneie os servos com IDs 1\~6; use FOUND nos resultados da varredura para confirmar o servo com o ID correspondente. Por exemplo, na imagem o servo de ID 1 foi encontrado

![A imagem mostra a interface da etapa "Scan servos" no tutorial de montagem do kit do braço SO-ARM101. Na parte superior da interface há caixas de entrada "Start ID" e "End ID", atualmente com ID inicial 1 e ID final 6. Abaixo há um botão "Start scan". Nos resultados da varredura, escanear os IDs 1-6 não encontra servos, reportando "Exception: No status packet! Error code: 0". Esta imagem está intimamente ligada ao contexto e apresenta visualmente a interface e os resultados ao escanear servos, ajudando os usuários a entender o status da varredura de servos.](../en/images/d09-13.png)

3. Definição de ID e calibração de centro

① Ajuste a entrada do ID de servo atual para o ID do servo escaneado

② Digite um número em "ID management" e clique em "Change ID" para definir o ID

③ Calibração de centro (o centro do servo STS3215 é 2047 e o do servo SCS0009 é 511)

Servo STS: digite 2047 em "Position control" e clique em "Set"

Servo SCS: digite 511 em "Position control" e clique em "Set"

![A imagem mostra uma interface de controle de servo individual. O ID do servo atual é 1; após digitar o número 1 em ID management e clicar em "Change ID", a mensagem "Success: ID changed to 1" aparece. Em Position Control o valor é 2047, e clicar no botão "Set" o aplica. Esta imagem está relacionada ao contexto "Definição de ID e calibração de centro" e apresenta visualmente a interface da operação de definição de ID, ajudando os usuários a entender como digitar um número em "ID management" para definir o ID e como digitar o valor do centro em "Position control" e clicar em "Set" para concluir.](../en/images/d09-14.png)
