[English](../en/servo-calibration-tool.md) | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | [Deutsch](../de/servo-calibration-tool.md) | [Español](../es/servo-calibration-tool.md) | [Français](../fr/servo-calibration-tool.md) | [Italiano](../it/servo-calibration-tool.md) | [日本語](../ja/servo-calibration-tool.md) | [한국어](../ko/servo-calibration-tool.md) | [Português (BR)](../pt-br/servo-calibration-tool.md) | Português (PT)

# Ferramenta de Calibração do Servo STS3215 para a Série So-ARM (opcional)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**Um conjunto de ferramentas de calibração de fábrica de servos FTServo e de calibração LeRobot concebido para braços da série So-ARM 10X**

> ⚠️ **Nota de compatibilidade: este sistema atualmente só suporta servos Feetech (série STS3215)**. A tabela de registos, o formato dos parâmetros xdat e a tabela de taxas de baud foram todos concebidos para a série Feetech STS3215.

> 📜 **Origem e créditos: esta ferramenta é adaptada e melhorada do projeto** [**Seeed_RoboController da Seeed Studio**](https://github.com/Seeed-Studio), **originalmente lançada sob a licença MIT**. Mantendo a funcionalidade central original, este projeto reformula a interface gráfica e acrescenta o depurador FT, a cópia de segurança/restauro de parâmetros xdat, o suporte multiplataforma, a alternância chinês/inglês e outras melhorias.

---

## ✨ Funcionalidades

| Funcionalidade | Descrição |
|-|-|
| Deteção automática de porta | Deteta inteligentemente portas série USB e filtra dispositivos virtuais |
| Suporte multiplataforma | Compatível com Windows / Ubuntu / macOS |
| Sincronização de porta dupla | As portas série esquerda e direita funcionam de forma independente, com suporte para controlo remoto sincronizado de porta dupla leader/follower |
| Alternância chinês/inglês | Alternância entre chinês/inglês na interface com um clique, com a escolha memorizada automaticamente |
| Calibração de centro | Grava a posição atual do servo como centro 2048 (persistido na EEPROM) |
| Teste de centro | Ativa o binário e move o servo para o centro para verificar o resultado da calibração |
| Desativar motores | Desativa o binário de todos os servos com um clique, para facilitar o ajuste manual |
| Digitalização automática | Deteta automaticamente todos os servos online dentro dos IDs 1–20 |
| Controlo de servo único | Um cursor controla em tempo real a posição e o ligar/desligar do binário de um servo |
| Depurador FT | Ligação série, digitalização, leitura/escrita de parâmetros, controlo de posição, alteração da taxa de baud, reposição de fábrica, cópia de segurança de parâmetros xdat |
| Parâmetros xdat | Guardar os parâmetros EEPROM atuais do servo / abrir uma cópia de segurança para restaurar |
| Calibração LeRobot | Gera ficheiros de calibração JSON no formato LeRobot |
| Correr até ao centro a partir de um ficheiro de calibração | Move o braço para o centro com base num ficheiro de calibração |

---

## 📚 Tutoriais Detalhados

### Chinês

| SO | Tutorial |
|-|-|
| Windows | \[Tutorial do Windows\](docs/zh/Windows教程.md) |
| Linux | \[Tutorial do Linux\](docs/zh/Linux教程.md) |
| macOS | \[Tutorial do macOS\](docs/zh/macOS教程.md) |

### Inglês

| SO | Guia |
|-|-|
| Windows | \[Guia do Windows\](docs/en/Windows.md) |
| Linux | \[Guia do Linux\](docs/en/Linux.md) |
| macOS | \[Guia do macOS\](docs/en/macOS.md) |

---

## 🖥️ Visão Geral da Interface

O programa principal tem três separadores:

```Plain Text
┌─────────────────────────────────────────────────────────────┐
│  SoARM Series Calibration Tool  [Port1▾] [Port2▾] [🔄]  [🎮Remote][EN]│  ← Top bar
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────┬──────────────────────────────┐ │
│  │ Port1 - Servo Calib.    │ Port2 - Servo Calib.         │ │
│  │  [🔴Disconnected] Cur:… │  [🔴Disconnected] Cur:…      │ │
│  │  Servo1~6 status table  │  Servo1~6 status table       │ │
│  │  [CenterCal][CenterTest]│  [CenterCal][CenterTest]…    │ │
│  └─────────────────────────┴──────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

- **Barra superior**: título da aplicação, listas pendentes de seleção de porta, botão de atualização, botão de controlo remoto, botão de mudança de idioma.
- **🦾 Separador 1 Calibração de Servos**: ações rápidas para os painéis esquerdo e direito (calibração de centro, teste de centro, desativar motores) mais o estado em tempo real.
- **🎚️ Separador 2 Controlo de Servo Único**: afinar a posição de cada servo online com um cursor e alternar o respetivo binário.
- **🔬 Separador 3 Depurador FT**: ligação série, digitalização, leitura/escrita de parâmetros, controlo de posição, taxa de baud/reposição de fábrica, cópia de segurança e restauro de parâmetros xdat.

---

## 🚀 Início Rápido

> Para os tutoriais completos por sistema, consulte \[📚 Tutoriais Detalhados\](#-详细教程). Abaixo estão os pontos essenciais de cada sistema.

### Windows

1. Instale o [Python 3.10+](https://www.python.org/downloads/) (assinale **Add to PATH**)
2. Crie um ambiente virtual e instale as dependências:

```Bash
cd Juxi_ServoController
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

1. Verifique o ambiente e inicie:

```Bash
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Confirme o número da porta no Gestor de Dispositivos (por exemplo `COM3`) e selecione-a na barra superior. Para especificar as portas manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux (Ubuntu / Debian)

1. Instale as fontes CJK e as dependências:

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ Adicione as permissões da porta série (grupo dialout)** [obrigatório]:

```Bash
sudo usermod -a -G dialout $USER
# Tem efeito depois de terminar sessão e voltar a iniciar sessão
```

1. Crie um ambiente virtual, instale as dependências e inicie:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. Os dispositivos série são `/dev/ttyUSB0` / `/dev/ttyACM0`. Para especificar manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/ttyUSB0 --port2 /dev/ttyUSB1
```

### macOS

1. Instale o `Python` com o `Homebrew `:

```Bash
brew install python
```

1. Crie um ambiente virtual, instale as dependências e inicie:

```Bash
cd Juxi_ServoController
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python setup.py
python -m src.gui.factory_calibration_tool
```

1. **⚠️ Nomenclatura da porta série**: no macOS use `/dev/cu.usbserial-*` (**recomendado, não bloqueante**) em vez de `/dev/tty.*`. Para as listar:

```Bash
ls /dev/cu.*
```

Para especificar manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### Ferramentas de linha de comandos gerais (sem necessidade de interface gráfica)

```Bash
# Digitalizar servos
python -m src.tools.scan_id

# Calibração rápida do centro do servo
python -m src.tools.servo_quick_calibration

# Teste do centro do servo
python -m src.tools.servo_center_test

# Desativar todos os servos
python -m src.tools.servo_disable

# Calibração ao estilo LeRobot
python -m src.tools.lerobot_calibrate

# Controlo remoto sincronizado de porta dupla
python -m src.tools.servo_remote_control
```

---

## 📖 Passos de Utilização

### 1. Ligar e detetar os servos

1. Ligue a placa de controlo do braço através de um adaptador USB-série e alimente os servos.
2. Abra a interface gráfica e selecione a porta na lista pendente da barra superior (ou clique em `🔄` para atualizar).
3. A parte superior do painel mostra `🟢 Connected` e digitaliza automaticamente os servos online dentro dos IDs 1–20 (normalmente 1–6).

> Se indicar que a porta está ocupada, certifique-se de que nenhum outro programa (um monitor série, uma ferramenta aberta anteriormente que não foi fechada) a está a usar.

### 2. Calibração de centro (definir a posição atual como 2048)

> Antes de calibrar, coloque fisicamente o braço na posição "zero / centro" pretendida para cada junta.

1. Clique no botão **PortX Center Calibration** no painel.
2. O programa começa por desativar os servos e pede-lhe para os mover manualmente até ao centro pretendido.
3. Depois de confirmar, o programa executa, para cada servo: desbloquear a EEPROM → escrever o comando de calibração (valor 128 no endereço 40) → voltar a bloquear a EEPROM.
4. Após a calibração, utilize "Center test" para verificar: o servo deve manter-se no lugar (com muito pouco movimento), o que significa que a calibração foi bem-sucedida.

### 3. Teste de centro

1. Clique em **PortX Center Test**.
2. O programa ativa o binário e move todos os servos para 2048.
3. Se os servos quase não se moverem da posição atual, a calibração está correta; se se moverem muito, o valor de calibração não é fiável e tem de ser refeito.

### 4. Desativar motores (ajuste manual)

- Clique em **PortX Disable Motors** para desligar o binário de todos os servos dessa porta, para que possam ser rodados livremente à mão.
- Para um servo individual, alterne o respetivo binário na página **Single-Servo Control**, usando o interruptor de binário por baixo do cursor.

### 5. Alterar o ID de um servo

1. Vá à página **🔬 FT Debugger**, ligue a porta série e digitalize os servos.
2. Selecione o servo pretendido, altere o valor "Servo ID" (endereço 0x05) na tabela de parâmetros e clique em escrever.
3. O programa executa: desbloquear → escrever no endereço 5 → verificar o novo ID → voltar a bloquear.

> ⚠️ Antes de alterar um ID, certifique-se de que este é o único servo no barramento, para evitar conflitos de ID.

### 6. Alterar a taxa de baud / reposição de fábrica

- **Alterar a taxa de baud**: na área "Baud rate / factory reset" da página FT Debugger, selecione a nova taxa de baud (38400 – 1000000 bps) e aplique-a. Depois de escrever, a taxa de baud da porta série é alterada automaticamente e verificada por ping; em caso de falha, reverte automaticamente.
- **Reposição de fábrica**: o servo volta aos valores predefinidos de fábrica (ID=1, taxa de baud=1000000); volte a digitalizar depois.

### 7. Cópia de segurança e restauro de parâmetros xdat

Na área "xdat parameters (EEPROM only)" da página FT Debugger:

1. **💾 Save current servo**: guarda os parâmetros EEPROM do servo atualmente selecionado num ficheiro xdat (cópia de segurança).
2. Depois de alterar livremente os parâmetros do servo, se quiser restaurar:
3. **📂 Open xdat**: carrega o ficheiro de cópia de segurança.
4. **📤 Restore parameters to servo**: reescreve a cópia de segurança na EEPROM do servo atual.

### 8. Controlo remoto sincronizado de porta dupla

> ⚠️ **Direção: a Porta 1 controla a Porta 2**. A Porta 1 (leader) apenas lê os ângulos dos servos; a Porta 2 (follower) é controlada em sincronia.

1. Clique em **🎮 Remote** na barra superior (a Porta 1 lê os ângulos → a Porta 2 controla sincronizadamente os servos com os mesmos IDs).
2. Ambas as portas têm de ter IDs de servo correspondentes; apenas os servos na interseção são sincronizados.
3. Clique novamente no mesmo botão para parar; em seguida, as threads de digitalização dos painéis esquerdo e direito retomam automaticamente.

### 9. Calibração LeRobot (linha de comandos)

```Bash
# Calibrar o braço follower (guardado em ~/.cache/huggingface/lerobot/calibration/robots/so_follower/)
python -m src.tools.lerobot_calibrate --arm-type follower

# Calibrar o braço leader
python -m src.tools.lerobot_calibrate --arm-type leader
```

Fluxo: desativar os servos → mover cada junta até ao centro e registar o `homing_offset` → percorrer lentamente toda a amplitude e registar `range_min/max` (o `wrist_roll` é uma junta de rotação contínua com um intervalo fixo de `[0,4095]`) → guardar o JSON.

Correr até ao centro usando um ficheiro de calibração:

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ Notas



1. **Segurança em primeiro lugar**: a calibração de centro é persistida na EEPROM. Antes de calibrar, certifique-se de que a alimentação é estável e que o braço não irá colidir com pessoas ou objetos.
2. **Alimentação**: para o SoARM 101 padrão, recomenda-se DC 5V 5A; para a versão Pro, DC 12V 5A. Uma alimentação insuficiente provoca perda de passos dos servos ou falhas de comunicação.
3. **Exclusividade da porta série**: no Windows a porta é bloqueada em exclusivo, pelo que a mesma porta não pode ser usada ao mesmo tempo pela thread de digitalização da interface gráfica e pelo subprocesso de calibração. A ferramenta para automaticamente a thread de digitalização e encerra o processo antigo antes de operar; não clique repetidamente à mão.
4. **Permissões de série no Linux**: aceder a `/dev/ttyUSB*` / `/dev/ttyACM*` requer adicionar o utilizador ao grupo `dialout` (veja o \[Tutorial do Linux\](docs/zh/Linux教程.md)).
5. **Nomenclatura de série no macOS**: use `/dev/cu.*` (não bloqueante) em vez de `/dev/tty.*` (bloqueante, pode bloquear); veja o \[Tutorial do macOS\](docs/zh/macOS教程.md).
6. **Ligação a quente**: depois de desligar o USB, o programa tenta reconectar-se automaticamente; depois de o voltar a ligar, clique em `🔄` para atualizar a lista de portas.
7. **Proteção contra sobretemperatura / sobretensão**: o programa monitoriza a tensão e a temperatura (alarme acima de 60°C). Se os servos continuarem quentes, pare e deixe-os arrefecer.
8. **A calibração de centro é irreversível**: depois de escrita, o desvio original é substituído e não pode ser anulado. Registe primeiro a posição original antes de calibrar.
9. **Risco de alteração de ID**: se a escrita ou a verificação falharem, o programa reporta um erro e retoma a digitalização, mas em casos extremos o servo pode ficar "perdido". Se isso acontecer, experimente "Factory reset" (após a reposição, o ID volta a 1).
10. **Problema de codificação**: se os emoji aparecerem corrompidos na consola do Windows, defina `PYTHONIOENCODING=utf-8` antes de executar as ferramentas de linha de comandos. O Linux/macOS com UTF-8 nativo geralmente não têm este problema.

---

## 🛠️ Resolução de Problemas

| Sintoma | Causa possível | Solução |
|-|-|-|
| Não consegue abrir a porta série / porta ocupada | Outro programa está a usá-la | Feche programas como monitores série, ou mude de porta e reinicie a ferramenta |
| Não foram encontrados servos na digitalização | Alimentação insuficiente / cablagem errada / taxa de baud diferente | Verifique a alimentação e a cablagem, e confirme que os servos estão a 1M de baud |
| Os servos descontrolam-se após a calibração de centro | A posição não foi definida corretamente antes da calibração | Refaça "desativar → colocar manualmente → calibração de centro" |
| A temperatura sobe demasiado depressa | Carga excessiva ou bloqueio | Verifique se o mecanismo está preso; reduza a velocidade/aceleração |
| Servo não encontrado depois de alterar o ID | Conflito de ID ou falha de escrita | Faça reposição de fábrica e volte a digitalizar |
| Controlo remoto dessincronizado | As duas portas têm IDs que não correspondem | Confirme que estão online servos com o mesmo ID nas portas leader e follower |

---

## 📁 Estrutura de Diretórios

```Plain Text
Juxi_ServoController/
├── docs/                    # Tutoriais por sistema (chinês/inglês)
│   ├── zh/                  # Tutoriais em chinês
│   │   ├── Windows教程.md
│   │   ├── Linux教程.md
│   │   └── macOS教程.md
│   └── en/                  # Tutoriais em inglês
│       ├── Windows.md
│       ├── Linux.md
│       └── macOS.md
├── src/
│   ├── gui/                  # Interface gráfica PySide6
│   │   ├── factory_calibration_tool.py   # Ferramenta principal (calibração de porta dupla + controlo remoto + mudança de idioma)
│   │   ├── ft_debugger.py                # Depurador FT (leitura/escrita de parâmetros / cópia de segurança xdat)
│   │   ├── calibration_wizard.py         # Assistente de calibração LeRobot
│   │   ├── theme_utils.py                # Tema claro
│   │   └── language_dialog.py            # Caixa de diálogo de seleção de idioma
│   ├── tools/                # Ferramentas de linha de comandos
│   ├── xdat_utils.py         # Leitura/escrita de ficheiros de parâmetros xdat
│   ├── i18n*.py / i18n_translations/     # Internacionalização chinês/inglês
│   ├── port_utils.py         # Deteção de porta série
│   └── calibration_manager.py# Gestão de ficheiros de calibração LeRobot
├── scservo_sdk/              # SDK de comunicação do servo FTServo
├── requirements.txt
└── setup.py                  # Script de verificação do ambiente
```
