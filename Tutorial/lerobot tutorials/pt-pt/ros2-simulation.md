[English](../en/ros2-simulation.md) | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | [Deutsch](../de/ros2-simulation.md) | [Español](../es/ros2-simulation.md) | [Français](../fr/ros2-simulation.md) | [Italiano](../it/ros2-simulation.md) | [日本語](../ja/ros2-simulation.md) | [한국어](../ko/ros2-simulation.md) | [Português (BR)](../pt-br/ros2-simulation.md) | Português (PT)

# Controlo de Simulação ROS2

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

Um workspace ROS 2 completo para o braço robótico SO-ARM101 de 6 graus de liberdade, abrangendo a descrição do robô, um controlador de hardware integrado, a simulação Gazebo e o planeamento de movimento do MoveIt 2.

O SO-ARM101 é o braço follower de código aberto de segunda geração, co-concebido pela [TheRobotStudio](https://www.therobotstudio.com/) e pela comunidade [LeRobot](https://huggingface.co/lerobot), usando seis servos STS3215, uma placa controladora de servos e peças de PLA+ impressas em 3D.

<callout emoji="📌">
**Nota: o braço exige calibração de centro; faça a calibração de centro com todas as juntas no meio da sua amplitude de movimento**
</callout>

## Estrutura dos Pacotes

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

Plataforma alvo: **ROS 2 Humble / Jazzy**.

---

## Preparar o Ambiente ROS 2

Antes de compilar este projeto, certifique-se de que o ROS 2 e os componentes relevantes estão instalados no seu sistema.

### Requisitos de Sistema

- Ubuntu 22.04 (recomendado) ou 24.04
- Pelo menos 4 GB de RAM
- É necessária uma porta série USB para o modo de hardware real

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

### 0.2  Instalar as Ferramentas de Compilação e as Dependências

```Bash
# Ferramenta de compilação colcon
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  Definir as Variáveis de Ambiente

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  Definir as Permissões da Porta Série (necessário para hardware real)

**Configuração permanente (recomendada)**:

```Bash
sudo usermod -a -G dialout $USER
# Tem efeito depois de terminar sessão e voltar a iniciar sessão
```

**Configuração temporária (tem de ser refeita após cada reinício)**:

```Bash
sudo chmod 666 /dev/ttyACM0
```

## Instalar o Workspace

```Markdown
# Passo 1  Criar o workspace
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# Passo 2  Colocar o código-fonte
cp -r /path/to/SO-ARM101_ROS2 ./

# Passo 3  Instalar as dependências do sistema
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# Passo 4  Compilar todos os pacotes
colcon build --symlink-install

# Passo 5  Carregar o ambiente  ← execute isto em cada novo terminal
source install/setup.bash
```

<callout emoji="💡">
**Nota sobre hardware real** — o pacote `so_arm_hardware` já vem integrado. Não é necessário instalar nenhum controlador adicional;  
comunica diretamente com os servos STS3215 através da porta série, usando o protocolo SCS.
</callout>

## Verificação Visual

Comece por aqui — é o caminho mais simples: sem controladores, sem hardware.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

O RViz apresenta o modelo completo do robô; arraste os controlos deslizantes para verificar se cada junta se move corretamente.

---

## Teste dos Controladores (hardware virtual / modo Mock)

Continua a não ser necessário um robô real — tudo corre em memória.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

Quando o registo mostrar o seguinte, está pronto:

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**Nota**: o modo de simulação inicia apenas dois controladores (`joint_state_broadcaster` e  
`joint_trajectory_controller`). O `gripper_controller` foi removido; a pinça  
é controlada em conjunto com as 6 juntas pelo `joint_trajectory_controller`.
</callout>

### Responsabilidades dos Controladores

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## Planeamento de Movimento MoveIt (hardware Mock)

**Basta um único terminal** — o MoveIt inicia a pilha de controladores internamente.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

Assim que a janela do RViz abrir:

1. No painel **MotionPlanning**, defina **Planning Group → manipulator**
2. **Start State → `<current>`**, **Goal State → extended**
3. Clique em **Plan** e depois em **Execute**

Posições predefinidas disponíveis: `open`, `zero`, `extended`, `rest`.

### 4.1  Apresentação da Interface do MoveIt

Depois de o RViz arrancar, o painel **MotionPlanning** aparece à esquerda com os seguintes separadores principais:

#### Separador Planning

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Parâmetros de Planeamento

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **Dica para o primeiro teste**: defina Velocity e Acceleration para 0.3 para abrandar o movimento por segurança.

#### Separador Scene Objects

- Adicione obstáculos (Box / Sphere / Cylinder) para a verificação de colisões
- Importe / exporte cenas
- O MoveIt planeia automaticamente a contornar os obstáculos

#### Separador Stored States

- Guarde posições do braço usadas com frequência
- Posições predefinidas: `open`, `zero`, `extended`, `rest`

### 4.2  Fluxo de Trabalho Básico

#### Método A: Arrasto interativo (recomendado)

1. Na vista 3D, encontre o **marcador interativo** na extremidade do braço (setas e anéis coloridos)
2. Arraste as setas para transladar a posição do efetuador final e arraste os anéis para rodar a orientação
3. O sistema resolve a cinemática inversa (IK) automaticamente e atualiza os ângulos das juntas em tempo real
4. Clique em **Plan** para ver a trajetória planeada (laranja)
5. Quando estiver satisfeito, clique em **Execute** para a executar

> Se o arrasto ficar intermitente, comece pela posição predefinida `rest` antes de arrastar.

#### Método B: Posições predefinidas

1. Lista pendente **Query Goal State** → selecione `open` / `extended` / `rest`, etc.
2. Clique em **Update**
3. Clique em **Plan**
4. Clique em **Execute**

#### Método C: Definir os ângulos das juntas manualmente

1. **Query Goal State** → separador **Joints**
2. Arraste cada cursor de junta para definir o ângulo pretendido
3. Referência de amplitude das juntas:

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. Clique em **Update**
2. Clique em **Plan**
3. Clique em **Execute**

#### Método D: Alvo válido aleatório

Clique em **Random Valid** para gerar uma posição alcançável aleatória e, em seguida, Plan → Execute.

### 4.3  Notas de Segurança

1. **Abrande na primeira utilização**: defina Velocity / Acceleration para 0.1–0.3
2. **Paragem de emergência**: prima Ctrl+C em qualquer momento para terminar o programa, ou corte a alimentação
3. **Limites das juntas**: o MoveIt não planeia para além das amplitudes em `joint_limits.yaml`, mas certifique-se de que estas estão configuradas corretamente
4. **Hardware real**: certifique-se de que há espaço suficiente à volta do braço antes de executar

### Visão Geral da Configuração do MoveIt

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Simulação Gazebo

A simulação Gazebo requer **4 terminais a funcionar ao mesmo tempo**. Siga a ordem rigorosamente.

### 5.1  Iniciar a simulação Gazebo  (Terminal 1)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Aguarde que a janela do Gazebo apareça; o robô fica suspenso no ar durante um instante e depois aterra.

### 5.2  Carregar o controlador de trajetória  (Terminal 2)

Por predefinição, o Gazebo ativa apenas o `forward_position_controller`; tem de mudar manualmente para  
o `joint_trajectory_controller`:

```Markdown
#  Terminal 2
source ~/so101_ws/install/setup.bash

# Passo A — desativar o forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# Passo B — carregar e ativar o joint_trajectory_controller com o spawner
ros2 run controller_manager spawner joint_trajectory_controller

# Passo C — verificar
ros2 control list_controllers
```

Saída esperada:

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ Não use primeiro `ros2 control load_controller`! Coloca o controlador no estado  
`unconfigured`, o que impede o spawner de o ativar. Se já o fez,  
execute primeiro `unload_controller` e comece de novo.
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

As juntas do braço no Gazebo acompanham o movimento.

<callout emoji="💡">
**Nota**: devido à limitação do ganho do PID na versão Humble do `gz_ros2_control`,  
a pinça pode não abrir fisicamente no Gazebo (o registo de execução continua a indicar sucesso).  
O modo Mock e o hardware real não têm este problema.
</callout>

### 5.5  Modo headless (sem interface gráfica)

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  Resolução de problemas: falhas repetidas de carregamento

Se o spawner continuar a reportar `Failed to activate controller`, faça o seguinte para reiniciar por completo:

```Bash
# 1. Descarregar o controlador bloqueado
ros2 control unload_controller joint_trajectory_controller

# 2. Desativar o forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# 3. Voltar a criar o controlador (spawn)
ros2 run controller_manager spawner joint_trajectory_controller
```

## Hardware Real

Pré-requisito: o braço SO-ARM101 está montado e a placa controladora de servos está ligada ao PC através de USB.

### 6.1  Iniciar os controladores (opcional)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

O plugin `so_arm_hardware` faz automaticamente o seguinte:

1. Abre a porta série
2. Digitaliza os 6 IDs dos servos (1–6)
3. Verifica se cada servo responde
4. Ativa o binário e lê a posição atual

Assim que os controladores estiverem prontos, abra mais dois terminais para iniciar o MoveIt:

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

### 6.2  MoveIt (arranque com um único comando)

> O seguinte comando **substitui** o 6.1 (não execute ambos ao mesmo tempo; pare os comandos do 6.1) — o `demo.launch.py` já incluí a pilha de controladores internamente.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  Resolução de Problemas da Porta Série

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  A Visualização no RViz Não Corresponde à Pose Real

Se a pose do braço no RViz não corresponder ao hardware real (por exemplo, um desvio de junta ou um falso relatório de colisão):

1. Confirme que os servos foram alvo de calibração de centro
2. Ajuste o `position_offset` de cada junta em `so_arm101.ros2_control.xacro`
3. Fórmula de conversão: `new offset = current offset + (currently displayed rad / 0.00153398)`
4. Volte a compilar o pacote `so_arm101_description` depois da alteração

---

## Perguntas Frequentes

### P1: "package not found" ao compilar

**R**: Certifique-se de que todas as dependências do sistema estão instaladas corretamente e que o ambiente ROS 2 está carregado:

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### P2: "Permission denied" ao aceder à porta série no arranque

**R**: Verifique as permissões da porta série:

```Bash
# Correção temporária
sudo chmod 666 /dev/ttyACM0

# Correção permanente (tem efeito após terminar sessão)
sudo usermod -a -G dialout $USER
```

### P3: O planeamento do MoveIt falha com "Motion planning start tree could not be initialized"

**R**: Costuma haver duas causas:

1. **Juntas fora dos limites** — verifique a saída do `FixStartStateBounds` no registo. A tolerância atual é  
0.3 rad; se o desvio estiver dentro desse intervalo, passa. Caso contrário, ajuste `start_state_max_bounds_error`  
ou verifique os desvios dos servos.
2. **Estado inicial em colisão** — verifique a saída do `FixStartStateCollision` no registo. Se  
aparecer "Unable to find a valid state nearby", a pose atual está em autocolisão.  
O braço pode estar numa pose dobrada (por exemplo, a pinça a tocar no ombro), ou os desvios estão incorretos.  
Ajuste o `position_offset` e tente de novo.

### P4: O braço não se move após o Execute

**R**: Verifique o estado dos controladores:

```Bash
ros2 control list_controllers
```

Certifique-se de que o `joint_trajectory_controller` está `active`. Se não estiver, volte a criar o controlador (spawn):

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### P5: O RViz arranca lentamente ou bloqueia

**R**: Isto é normal. No arranque, o MoveIt carrega o modelo URDF, plugins de verificação de colisões,  
solucionadores de cinemática e assim por diante; o primeiro lançamento demora cerca de 10 segundos.

### P6: O caminho planeado não é suave ou é irregular

**R**: Experimente o seguinte:

- Mude para um planeador diferente (escolha `RRTConnect` na lista pendente Planner no RViz)
- Aumente o Planning Time para 10 segundos
- Certifique-se de que o alvo está dentro do espaço de trabalho (teste com `Random Valid`)

### P7: A pinça não se move no Gazebo

**R**: Trata-se de uma limitação do ganho do PID fixado no código na versão Humble do `gz_ros2_control`  
(fixado em 0.1) que não pode ser substituída através de parâmetros do URDF. O Execute reporta sucesso no registo,  
mas a pinça não abre na simulação física do Gazebo. O modo Mock e o hardware real não têm este problema.

## Anexo: Referência Rápida dos Parâmetros de Launch

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Estrutura de Diretórios

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # Biblioteca utilitária Python
├── so_arm101_description/          # URDF · controladores · malhas · RViz · MuJoCo
├── so_arm101_moveit_config/        # MoveIt 2 SRDF · planeadores · ficheiros de launch
├── so_arm_gz/                      # Launch da simulação Gazebo
├── so_arm_hardware/                # Controlador série SCS integrado (C++)
└── Simulation/                     # URDF CAD original (mantido para referência)
```
