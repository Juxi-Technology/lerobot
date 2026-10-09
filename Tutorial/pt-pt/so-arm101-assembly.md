[English](../en/so-arm101-assembly.md) | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | Português (PT)

<title>SO-ARM101 Robotic Arm Kit Assembly Tutorial</title>

<callout emoji="💡">
Nota: ignore este tutorial se tiver um braço pré-montado
</callout>

## Peças impressas em 3D do braço follower

![Esta imagem mostra as peças impressas em 3D do braço follower necessárias para montar o braço robótico SO-ARM101, todas peças de plástico PLA branco dispostas sobre uma superfície clara com veios de madeira. As peças incluem conectores de várias formas, uma estrutura em forquilha com grelha, uma peça tipo base com furos, um braço de suporte em forquilha de forma especial e assim por diante, correspondendo ao ponto do tutorial de que a extremidade do braço follower é uma pinça. Estas peças são as moldadas básicas do braço follower do braço e são os objetos manipulados no passo de remoção dos suportes, correspondendo diretamente às peças impressas em 3D do braço follower apresentadas no tutorial.](../en/images/d09-01.jpg)

## Peças impressas em 3D do braço leader

![A imagem mostra peças impressas em 3D do braço robótico SO-ARM101. Diversas peças impressas em 3D pretas estão dispostas ordenadamente na moldura, com linhas azuis nas bordas de algumas peças. Estas peças incluem estruturas dos braços leader e follower, como a pinça, o punho e o gatilho, além de conectores. A imagem corresponde à secção "Peças impressas em 3D do braço leader" do documento e apresenta visualmente o aspeto das peças impressas em 3D, fornecendo uma referência para os passos posteriores de remoção dos suportes sobrantes e de distinção dos servos.](../en/images/d09-02.jpg)

Os braços leader e follower são muito parecidos; só a extremidade é diferente

O leader tem um punho e um gatilho; o follower tem uma pinça

## Remover os suportes sobrantes das peças impressas em 3D

Verifique todos os furos, aberturas, ranhuras e grelhas, especialmente os cinco furos que se assemelham à peça "cinco pontos" do mahjong

Este passo é muito importante; caso contrário, não conseguirá enfiar os parafusos mais tarde

## Distinguir os quatro servos

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">Tamanho grande</td><td vertical-align="middle">Tamanho pequeno</td><td vertical-align="middle">Tensão (V)</td><td vertical-align="middle">Relação de engrenagem</td><td vertical-align="middle">Junta do braço</td><td vertical-align="middle">Quantidade</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Todas as juntas do follower</td><td vertical-align="middle">6</td></tr></tbody></table>

> A relação de engrenagem é a razão "velocidade do motor : velocidade do veio de saída do servo"; por exemplo, 1:345 significa que o motor dá 345 voltas para que o veio de saída dê uma volta.
> 
> Uma relação de engrenagem alta multiplica o binário através do trem de engrenagens, pelo que consegue acionar uma carga mais pesada (como o braço follower)
> 
> Mas, ao mesmo tempo, o veio de saída gira mais devagar (porque está "reduzido")
> 
> Arrastar a junta também exige mais esforço

Abaixo estão os modelos e as relações de engrenagem de todos os servos deste projeto; as partes sublinhadas são os seus números

![A imagem mostra os modelos, as tensões e as relações de engrenagem dos servos usados no braço. À esquerda está o braço leader, com dois modelos, C046 (7.4V, 1:147) e C044 (7.4V, 1:191); à direita está o braço follower, com dois modelos, C001 (7.4V, 1:345) e C047 (12V, 1:345). A imagem está estreitamente ligada ao contexto, que apresenta em detalhe os modelos, as tensões e as relações de engrenagem dos servos dos braços leader e follower; esta imagem mostra visualmente estes valores essenciais para ajudar os leitores a compreender melhor a configuração dos servos.](../en/images/d09-03.png)

![A imagem mostra quatro caixas de servos com a etiqueta "STS3215". Cada caixa tem impressa a palavra "SPECIFICATION" e inclui parâmetros como binário, velocidade e dimensões, por exemplo um binário de 9.2kg·cm/127.98oz·in(6V). O STS3215-C001 tem um binário de 12.5kg·cm/173.88oz·in(6V), e o STS3215-C046 tem um binário de 16kg·cm/220.58oz·in(7V). Estes servos são o modelo usado em todas as juntas do braço follower, correspondendo ao braço follower apresentado no documento, e são usados na instalação dos servos nos passos de montagem posteriores.](../en/images/d09-04.jpg)

## Distinguir os dois adaptadores de alimentação

Adaptador de alimentação 5V 6A 30W: alimenta os servos de 7.4V (braço leader), preto

Adaptador de alimentação 12V 5A 60W: alimenta os servos de 12V (braço follower), branco

## Descarregar a ferramenta de depuração de servo da Feetech

### PC com Windows

https://gitee.com/ftservo/fddebug

Descarregue [`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z), extraia-o e execute o programa exe que está lá dentro

### Ubuntu e Mac (o arquivo inclui um tutorial)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![Esta imagem é uma ilustração auxiliar do tutorial de montagem do kit do braço robótico SO-ARM101, correspondente à secção sobre distinguir os adaptadores de alimentação. Mostra dois modelos de servo e as suas posições de montagem, STS3215-C001 e STS3215-C018, e também identifica servos como o STS3215-C004, correspondentes às diferentes juntas do braço. A figura lista também os parâmetros destes dois servos, incluindo velocidade de rotação, binário de bloqueio, precisão do servo, funções de proteção e feedback de parâmetros, fornecendo uma referência para a seleção e a instalação dos servos durante a montagem do braço.](../en/images/d09-05.jpg)

**Versão Pro: o braço leader usa um adaptador de alimentação de 5V6A, e o braço follower usa um adaptador de alimentação de 12V5A**

A configuração dos IDs dos servos, a calibração do ângulo dos servos e a montagem têm de ser feitas antecipadamente; consulte o [tutorial de montagem oficial](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# Passo 1: Definir os IDs dos servos e instalar os braços dos servos (exceto o servo 5)

<grid>
<column width-ratio="0.500000">
![A imagem mostra a interface da ferramenta de depuração de host da Feetech. A interface tem três separadores, "Debug", "Program" e "Upgrade", estando "Program" atualmente selecionado. Informação essencial: 1. Nas definições de comunicação, a porta é a COM6 e a taxa de baud é 1000000; 2. Nas operações de servo, a escrita síncrona, a escrita assíncrona e a saída de binário estão todas assinaladas; 3. No feedback do servo, parâmetros como tensão, corrente, temperatura e posição mostram todos 0; 4. Na pesquisa de servos, está selecionado o id 1, modelo ST53215. Esta imagem relaciona-se com as operações de depuração descritas acima, como definir os IDs dos servos e instalar o braço do servo, e apresenta a interface da ferramenta de depuração.](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![A imagem mostra a interface da ferramenta de depuração de host da Feetech, usada para definir os IDs dos servos. A interface tem três separadores, "Debug", "Program" e "Upgrade", estando "Program" atualmente selecionado. Na área "Center calibration", o número de ID é 4, com um botão "Save" à direita. O lado esquerdo da interface mostra o ID do servo, o modelo e outras informações. Esta imagem relaciona-se com o conteúdo "Passo 1: Definir os IDs dos servos e instalar os braços dos servos (exceto o servo 5)" do documento e apresenta a interface da operação de definição do ID do servo, mostrando visualmente onde se define o número de ID.](../en/images/d09-07.png)
</column>
</grid>

1. Abra a ferramenta de depuração de host da Feetech, selecione a porta COM, defina a taxa de baud para um milhão e clique em "Open"
2. Clique em "Search"; assim que aparecer "STS3215", clique em "Stop" e depois clique em "STS3215"
3. Selecione "Debug" no topo; pode arrastar o cursor para rodar o servo, ou clicar em "Scan" para o fazer mover-se para a frente e para trás. Confirme que o servo funciona normalmente
4. Selecione "Program" no topo
5. Clique em "Center calibration" para definir a posição atual do veio de rotação do servo como centro (0-4095)
6. Clique em "ID", defina o número de ID do servo correspondente no canto inferior direito e clique em "Save". Note que o número é em algarismos árabes simples, sem letras.
7. Desligue o cabo que liga o servo à placa de controlo
8. Ligue o cabo do servo ao servo

O servo 1 recebe dois cabos; os outros servos recebem apenas um cabo por agora

![A imagem mostra a instalação dos servos durante a montagem do kit do braço SO-ARM101. A moldura contém o braço follower e o braço leader, com o braço follower numerado 123456 e o braço leader numerado 123456. Os servos estão etiquetados com relações de engrenagem de 1:345, 1:191 e 1:147. Abaixo está a placa de controlo, ligada a dois cabos, um branco e um preto. Esta imagem relaciona-se com os passos de montagem acima e apresenta visualmente as posições e os números de montagem dos servos, ajudando quem monta a associar os servos à placa de controlo com precisão.](../en/images/d09-08.png)

<callout emoji="💡">
Mais uma vez: certifique-se de que o ID da junta e a relação de engrenagem de cada servo correspondem exatamente ao **SO-ARM101**.
</callout>

Cada motor no barramento tem um ID único. Os motores novos costumam vir com um ID predefinido de `1`. Para garantir que a comunicação entre os motores e o controlador funciona, temos primeiro de definir um ID único para cada motor. Além disso, a velocidade de transmissão de dados no barramento é determinada pela taxa de baud. Para comunicarem entre si, o controlador e todos os motores têm de estar configurados com a mesma taxa de baud; os servos deste braço usam uma taxa de baud de 100000.

Para isso, temos primeiro de ligar o controlador a cada motor, um a um, para os podermos configurar. Como escrevemos estes parâmetros na área não volátil da memória interna do motor (EEPROM), isto só precisa de ser feito uma vez.

Se estiver a reutilizar motores de outro robô, poderá também precisar de fazer este passo, porque os IDs e as taxas de baud podem não coincidir.

O vídeo abaixo mostra a sequência de passos para definir os IDs dos motores.

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Utilize a ferramenta de host de servo da Feetech para definir os IDs dos servos e calibrar o centro. Os IDs são definidos de 1 a 6!

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu e Mac

<callout emoji="💡">
Se precisar da ferramenta de host de servo da Feetech, consulte a [ferramenta de depuração de servo da Feetech](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb) acima
</callout>

Comece por concluir a configuração do ambiente seguindo a página de [instalação oficial do LeRobot](https://huggingface.co/docs/lerobot/installation)

<callout emoji="💡">
Lembre-se de ativar o ambiente virtual e entrar no diretório src/lerobot correspondente
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. Encontre a porta USB do braço. Para encontrar a porta correta de cada braço, execute o script utilitário duas vezes::

```Plain Text
lerobot-find-port
```

Exemplo de saída ao identificar a porta do braço Leader (por exemplo `/dev/tty.usbmodem575E0031751` num Mac, ou possivelmente `/dev/ttyACM0` no Linux):

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
Lembre-se de desligar o conetor USB, caso contrário a porta não pode ser detetada.
</callout>

2. Ligue o PC à placa controladora de servos do braço follower com um cabo USB e ligue-o. Depois execute o seguinte comando. Altere --robot.port=/dev/ttyACM0 no comando para a porta que encontrou. Por exemplo, se a porta que encontrou for /dev/ttyACM1, altere-a para --robot.port=/dev/ttyACM1

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

Verá a seguinte saída.

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

Seguindo as instruções, ligue o servo da pinça. Certifique-se de que é o único servo ligado à placa controladora de servos e que este servo ainda não está ligado a nenhum outro servo. Depois de premir **[Enter]**, o script define automaticamente o ID e a taxa de baud desse servo. Os IDs são definidos de 6 a 1!

Depois disso, deverá ver o seguinte:

```Python
'gripper' motor id set to 6
```

Em seguida, a saída é:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**Nota** Repita o processo acima para cada servo, seguindo as instruções.
Tal como nos servos anteriores, certifique-se de que é o único servo ligado à placa controladora e que o próprio servo não está ligado a nenhum outro servo.
</callout>

Antes de premir **Enter** de cada vez, verifique sempre as ligações dos cabos. Por exemplo, o cabo de alimentação pode soltar-se ao manusear a placa de circuitos.

Quando tiver concluído todos os passos, o script termina automaticamente e os servos ficam prontos a usar. Pode agora ligar o conetor de 3 pinos de cada servo, um a um, e ligar o cabo do primeiro servo (o servo "shoulder pan" com ID 1) à placa controladora. A placa controladora pode agora ser montada na base do braço.

Repita os mesmos passos para o braço leader.

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# Passo 2: Montagem

<callout emoji="💡">
- Os passos de montagem do braço follower são essencialmente os mesmos do braço leader. A única diferença é que, após o passo 12, o efetuador final (pinça e punho) é instalado de forma diferente.
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
Instalar a placa controladora de servos: primeiro, monte os 4 espaçadores de latão e, em seguida, fixe a placa controladora com quatro parafusos M2.5\*8
</callout>

<grid>
<column width-ratio="0.525947">
![Instalar os quatro espaçadores de latão](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![Fixar a placa controladora de servos com parafusos M2.5*8](../en/images/d09-10.webp)
</column>
</grid>

![Montar no braço e fazer a cablagem](../en/images/d09-11.png)

**Versão Pro: o braço leader preto usa um adaptador de alimentação de 5V6A, e o braço follower branco usa um adaptador de alimentação de 12V5A**







# Definir IDs dos servos e calibração de centro na interface web

https://bambot.org/feetech.js?lang=zh

1. Introduza 0 ou 1 consoante o modelo do servo e, em seguida, clique em "Connect"

![A imagem mostra a interface "Connect" no tutorial de montagem do kit do braço. À esquerda da interface está a palavra "Connect", e à direita estão uma lista pendente "Baud rate" definida para 1,000,000 bps (Index 0) e uma caixa de introdução para "Protocol end (0=STS/SMS, 1=SCS)" definida para 0, com um retângulo vermelho em torno do número "1" ao lado da caixa de introdução. Abaixo está um botão verde "Connect", com um retângulo vermelho em torno do número "2" ao lado. Na base aparece "Status: Disconnected". Esta imagem corresponde ao conteúdo acima, "Introduza 0 ou 1 consoante o modelo do servo e, em seguida, clique em 'Connect'", e apresenta visualmente as definições da operação de ligação.](../en/images/d09-12.png)

2. Digitalize os servos com IDs 1\~6; utilize FOUND nos resultados da digitalização para confirmar o servo com o ID correspondente. Por exemplo, na imagem foi encontrado o servo com ID 1

![A imagem mostra a interface do passo "Scan servos" no tutorial de montagem do kit do braço SO-ARM101. Na parte superior da interface estão as caixas de introdução "Start ID" e "End ID", atualmente com start ID 1 e end ID 6. Abaixo está um botão "Start scan". Nos resultados da digitalização, ao digitalizar os IDs 1-6 não é encontrado nenhum servo, reportando "Exception: No status packet! Error code: 0". Esta imagem está estreitamente ligada ao contexto e apresenta visualmente a interface e os resultados ao digitalizar servos, ajudando os utilizadores a compreender o estado da digitalização de servos.](../en/images/d09-13.png)

3. Definição do ID e calibração de centro

① Defina a introdução do ID do servo atual para o ID do servo digitalizado

② Introduza um número em "ID management" e clique em "Change ID" para definir o ID

③ Calibração de centro (o centro do servo STS3215 é 2047, o centro do servo SCS0009 é 511)

Servo STS: introduza 2047 em "Position control" e clique em "Set"

Servo SCS: introduza 511 em "Position control" e clique em "Set"

![A imagem mostra uma interface de controlo de servo único. O ID do servo atual é 1; depois de introduzir o número 1 em ID management e clicar em "Change ID", aparece a mensagem "Success: ID changed to 1". Em Position Control o valor é 2047, e clicar no botão "Set" aplica-o. Esta imagem relaciona-se com o contexto "Definição do ID e calibração de centro" e apresenta visualmente a interface da operação de configuração do ID, ajudando os utilizadores a compreender como introduzir um número em "ID management" para definir o ID e como introduzir o valor de centro em "Position control" e clicar em "Set" para concluir.](../en/images/d09-14.png)
