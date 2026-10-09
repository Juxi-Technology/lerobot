[English](../en/ros2-simulation.md) | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | [Deutsch](../de/ros2-simulation.md) | [Español](../es/ros2-simulation.md) | [Français](../fr/ros2-simulation.md) | [Italiano](../it/ros2-simulation.md) | [日本語](../ja/ros2-simulation.md) | [한국어](../ko/ros2-simulation.md) | Português (BR) | [Português (PT)](../pt-pt/ros2-simulation.md)

# Controle de simulação ROS2

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

Um workspace completo de ROS 2 para o braço robótico SO-ARM101 de 6 graus de liberdade, cobrindo a descrição do robô, um driver de hardware integrado, a simulação Gazebo e o planejamento de movimento do MoveIt 2.

O SO-ARM101 é o braço follower de código aberto de segunda geração, co-projetado pela [TheRobotStudio](https://www.therobotstudio.com/) e pela comunidade [LeRobot](https://huggingface.co/lerobot), usando seis servos STS3215, uma placa driver de servo e peças de PLA+ impressas em 3D.

<callout emoji="📌">
**Observação: o braço exige calibração de centro; faça a calibração de centro com todas as juntas no meio da sua faixa de movimento**
</callout>

## Estrutura dos pacotes

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

Plataforma-alvo: **ROS 2 Humble / Jazzy**.

---

## Preparando o ambiente ROS 2

Antes de compilar este projeto, certifique-se de que o ROS 2 e os componentes relevantes estão instalados no seu sistema.

### Requisitos do sistema

- Ubuntu 22.04 (recomendado) ou 24.04
- Pelo menos 4 GB de RAM
- É necessária uma porta serial USB para o modo de hardware real

### 0.1  Instalar o ROS 2 Humble

```Bash
# Definir o locale
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# Adicionar o repositório de software do ROS 2
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Instalar o ROS 2 Humble Desktop
sudo apt update
sudo apt install ros-humble-desktop
```

### 0.2  Instalar ferramentas de build e dependências

```Bash
# ferramenta de build colcon
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  Definir variáveis de ambiente

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  Definir permissões da porta serial (necessário para hardware real)

**Configuração permanente (recomendada)**:

```Bash
sudo usermod -a -G dialout $USER
# Passa a valer depois que você sai da sessão e entra novamente
```

**Configuração temporária (precisa ser refeita após cada reinicialização)**:

```Bash
sudo chmod 666 /dev/ttyACM0
```

## Instalando o workspace

```Markdown
# Etapa 1  Criar o workspace
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# Etapa 2  Colocar o código-fonte
cp -r /path/to/SO-ARM101_ROS2 ./

# Etapa 3  Instalar as dependências do sistema
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# Etapa 4  Compilar todos os pacotes
colcon build --symlink-install

# Etapa 5  Carregar o ambiente  ← execute isto em cada novo terminal
source install/setup.bash
```

<callout emoji="💡">
**Observação sobre hardware real** — o pacote `so_arm_hardware` já vem integrado. Não é preciso instalar nenhum driver extra;  
ele se comunica diretamente com os servos STS3215 pela porta serial usando o protocolo SCS.
</callout>

## Verificação visual

Comece por aqui — é o caminho mais simples: sem controladores, sem hardware.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

O RViz exibe o modelo completo do robô; arraste os controles deslizantes para verificar se cada junta se move corretamente.

---

## Teste de controladores (hardware virtual / modo Mock)

Ainda não é preciso um robô real — tudo roda na memória.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

Quando o log mostrar o seguinte, está pronto:

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**Observação**: o modo de simulação inicia apenas dois controladores (`joint_state_broadcaster` e  
`joint_trajectory_controller`). O `gripper_controller` foi removido; a garra  
é controlada junto com todas as 6 juntas pelo `joint_trajectory_controller`.
</callout>

### Responsabilidades dos controladores

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## Planejamento de movimento com MoveIt (hardware Mock)

**É preciso apenas um terminal** — o MoveIt inicia a pilha de controladores internamente.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

Assim que a janela do RViz abrir:

1. No painel **MotionPlanning**, defina **Planning Group → manipulator**
2. **Start State → `<current>`**, **Goal State → extended**
3. Clique em **Plan** e depois em **Execute**

Poses predefinidas disponíveis: `open`, `zero`, `extended`, `rest`.

### 4.1  Tour pela interface do MoveIt

Depois que o RViz iniciar, o painel **MotionPlanning** aparece à esquerda com as seguintes abas principais:

#### Aba Planning

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Parâmetros de planejamento

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **Dica para o primeiro teste**: defina Velocity e Acceleration como 0.3 para deixar o movimento mais lento por segurança.

#### Aba Scene Objects

- Adicione obstáculos (Box / Sphere / Cylinder) para verificação de colisão
- Importe / exporte cenas
- O MoveIt planeja automaticamente desviando dos obstáculos

#### Aba Stored States

- Salve poses do braço usadas com frequência
- Poses padrão: `open`, `zero`, `extended`, `rest`

### 4.2  Fluxo de trabalho básico

#### Método A: arrastar de forma interativa (recomendado)

1. Na visualização 3D, encontre o **marcador interativo** na extremidade do braço (setas e anéis coloridos)
2. Arraste as setas para transladar a posição do efetuador final, e arraste os anéis para girar a orientação
3. O sistema resolve a IK automaticamente e atualiza os ângulos das juntas em tempo real
4. Clique em **Plan** para ver a trajetória planejada (laranja)
5. Quando estiver satisfeito, clique em **Execute** para executá-la

> Se o arrasto travar, comece pela pose predefinida `rest` antes de arrastar.

#### Método B: poses predefinidas

1. Menu suspenso **Query Goal State** → selecione `open` / `extended` / `rest`, etc.
2. Clique em **Update**
3. Clique em **Plan**
4. Clique em **Execute**

#### Método C: definir os ângulos das juntas manualmente

1. **Query Goal State** → aba **Joints**
2. Arraste o controle deslizante de cada junta para definir o ângulo desejado
3. Referência da faixa das juntas:

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. Clique em **Update**
2. Clique em **Plan**
3. Clique em **Execute**

#### Método D: alvo válido aleatório

Clique em **Random Valid** para gerar uma pose alcançável aleatória e depois Plan → Execute.

### 4.3  Notas de segurança

1. **Reduza a velocidade no primeiro uso**: defina Velocity / Acceleration entre 0.1 e 0.3
2. **Parada de emergência**: pressione Ctrl+C a qualquer momento para encerrar o programa, ou corte a energia
3. **Limites das juntas**: o MoveIt não planejará além das faixas em `joint_limits.yaml`, mas certifique-se de que estejam configuradas corretamente
4. **Hardware real**: certifique-se de que há espaço suficiente ao redor do braço antes de executar

### Visão geral da configuração do MoveIt

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Simulação no Gazebo

A simulação no Gazebo requer **4 terminais rodando ao mesmo tempo**. Siga a ordem à risca.

### 5.1  Iniciar a simulação no Gazebo  (Terminal 1)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Aguarde a janela do Gazebo aparecer; o robô fica pendurado brevemente no ar e depois pousa.

### 5.2  Carregar o controlador de trajetória  (Terminal 2)

Por padrão, o Gazebo ativa apenas o `forward_position_controller`; você precisa trocar manualmente para  
o `joint_trajectory_controller`:

```Markdown
#  Terminal 2
source ~/so101_ws/install/setup.bash

# Etapa A — desligar o forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# Etapa B — carregar e ativar o joint_trajectory_controller com o spawner
ros2 run controller_manager spawner joint_trajectory_controller

# Etapa C — verificar
ros2 control list_controllers
```

Saída esperada:

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ Não use `ros2 control load_controller` primeiro! Ele coloca o controlador no  
estado `unconfigured`, o que impede o spawner de ativá-lo. Se você já fez isso,  
execute `unload_controller` primeiro e comece de novo.
</callout>

### 5.3  Iniciar o move_group  (Terminal 3)

```Bash
#  Terminal 3
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py use_sim_time:=True
```

### 5.4  Iniciar o RViz  (Terminal 4)

```Bash
#  Terminal 4
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

Assim que o RViz estiver pronto:

1. **Planning Group → manipulator**
2. **Goal State → open** (ou `extended`, `rest`)
3. Clique em **Plan** e depois em **Execute**

As juntas do braço no Gazebo vão acompanhar o movimento.

<callout emoji="💡">
**Observação**: por causa da limitação de ganho do PID na versão Humble do `gz_ros2_control`,  
a garra pode não abrir fisicamente no Gazebo (o log de execução ainda reporta sucesso).  
O modo Mock e o hardware real não têm esse problema.
</callout>

### 5.5  Modo headless (sem GUI)

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  Solução de problemas: falhas de carregamento repetidas

Se o spawner continuar reportando `Failed to activate controller`, faça o seguinte para reiniciar por completo:

```Bash
# 1. Descarregar o controlador travado
ros2 control unload_controller joint_trajectory_controller

# 2. Desligar o forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# 3. Fazer o spawn novamente
ros2 run controller_manager spawner joint_trajectory_controller
```

## Hardware real

Pré-requisito: o braço SO-ARM101 está montado e a placa driver de servo está conectada ao PC via USB.

### 6.1  Iniciar os controladores (opcional)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

O plugin `so_arm_hardware` automaticamente:

1. Abre a porta serial
2. Escaneia os 6 IDs de servo (1–6)
3. Verifica se todos os servos respondem
4. Habilita o torque e lê a posição atual

Quando os controladores estiverem prontos, abra mais dois terminais para iniciar o MoveIt:

```Bash
#  Terminal 2 — move_group
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py
```

```Bash
#  Terminal 3 — RViz
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

### 6.2  MoveIt (inicialização com um comando)

> O comando a seguir **substitui** o 6.1 (não execute os dois ao mesmo tempo; pare os comandos do 6.1) — o `demo.launch.py` já inclui a pilha de controladores internamente.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  Solução de problemas da porta serial

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  A exibição no RViz não corresponde à pose real

Se a pose do braço no RViz não corresponder ao hardware real (por exemplo, um deslocamento de junta ou um relatório de colisão falso):

1. Confirme que os servos foram calibrados no centro
2. Ajuste o `position_offset` de cada junta em `so_arm101.ros2_control.xacro`
3. Fórmula de conversão: `new offset = current offset + (currently displayed rad / 0.00153398)`
4. Recompile o pacote `so_arm101_description` após a alteração

---

## Perguntas frequentes

### P1: "package not found" ao compilar

**R**: Certifique-se de que todas as dependências do sistema estão instaladas corretamente e de que o ambiente ROS 2 foi carregado:

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### P2: "Permission denied" ao acessar a porta serial na inicialização

**R**: Verifique as permissões da porta serial:

```Bash
# Correção temporária
sudo chmod 666 /dev/ttyACM0

# Correção permanente (tem efeito após encerrar a sessão)
sudo usermod -a -G dialout $USER
```

### P3: O planejamento do MoveIt falha com "Motion planning start tree could not be initialized"

**R**: Normalmente há duas causas:

1. **Juntas fora dos limites** — verifique a saída de `FixStartStateBounds` no log. A tolerância atual é  
0.3 rad; se o excesso estiver dentro dessa faixa, passa. Caso contrário, ajuste `start_state_max_bounds_error`  
ou verifique os deslocamentos dos servos.
2. **Estado inicial em colisão** — verifique a saída de `FixStartStateCollision` no log. Se  
aparecer "Unable to find a valid state nearby", a pose atual está colidindo consigo mesma.  
O braço pode estar em uma pose dobrada (por exemplo, a garra tocando o ombro), ou os deslocamentos estão incorretos.  
Ajuste `position_offset` e tente novamente.

### P4: O braço não se move após o Execute

**R**: Verifique os estados dos controladores:

```Bash
ros2 control list_controllers
```

Certifique-se de que `joint_trajectory_controller` está `active`. Se não estiver, gere-o novamente:

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### P5: O RViz inicia devagar ou trava

**R**: Isso é normal. Na inicialização, o MoveIt carrega o modelo URDF, plugins de verificação de colisão,  
solucionadores de cinemática e assim por diante; a primeira inicialização leva cerca de 10 segundos.

### P6: A trajetória planejada não é suave ou está aos trancos

**R**: Tente o seguinte:

- Troque para outro planejador (escolha `RRTConnect` no menu suspenso Planner do RViz)
- Aumente o Planning Time para 10 segundos
- Certifique-se de que o alvo está dentro do espaço de trabalho (teste com `Random Valid`)

### P7: A garra não se move no Gazebo

**R**: É uma limitação de ganho do PID embutida no código da versão Humble do `gz_ros2_control`  
(fixado em 0.1) que não pode ser sobreposta por parâmetros de URDF. O Execute reporta sucesso no log,  
mas a garra não abre na simulação física do Gazebo. O modo Mock e o hardware real não têm esse problema.

## Apêndice: referência rápida dos parâmetros de launch

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Layout do diretório

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # Biblioteca utilitária em Python
├── so_arm101_description/          # URDF · controladores · meshes · RViz · MuJoCo
├── so_arm101_moveit_config/        # MoveIt 2 SRDF · planejadores · arquivos de launch
├── so_arm_gz/                      # launch da simulação Gazebo
├── so_arm_hardware/                # Driver serial SCS integrado (C++)
└── Simulation/                     # URDF de CAD original (mantido como referência)
```
