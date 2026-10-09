[English](../en/servo-calibration-tool.md) | [简体中文](../zh-hans/servo-calibration-tool.md) | [繁體中文](../zh-hant/servo-calibration-tool.md) | [Deutsch](../de/servo-calibration-tool.md) | [Español](../es/servo-calibration-tool.md) | [Français](../fr/servo-calibration-tool.md) | [Italiano](../it/servo-calibration-tool.md) | [日本語](../ja/servo-calibration-tool.md) | [한국어](../ko/servo-calibration-tool.md) | Português (BR) | [Português (PT)](../pt-pt/servo-calibration-tool.md)

# Ferramenta de calibração de servo STS3215 para a série So-ARM (opcional)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

**Um kit de ferramentas de calibração de fábrica de servo FTServo e de calibração do LeRobot projetado para os braços da série So-ARM 10X**

> ⚠️ **Nota de compatibilidade: este sistema atualmente suporta apenas servos Feetech (série STS3215)**. A tabela de registradores, o formato de parâmetros xdat e a tabela de taxas de baud são todos projetados para a série Feetech STS3215.

> 📜 **Origem e créditos: esta ferramenta é adaptada e aprimorada a partir do projeto** [**Seeed_RoboController da Seeed Studio**](https://github.com/Seeed-Studio)**, originalmente publicado sob a licença MIT**. Mantendo a funcionalidade principal original, este projeto reformula a GUI e adiciona o depurador FT, backup/restauração de parâmetros xdat, suporte multiplataforma, alternância chinês/inglês e outras melhorias.

---

## ✨ Recursos

| Recurso | Descrição |
|-|-|
| Detecção automática de porta | Detecta de forma inteligente as portas seriais USB e filtra dispositivos virtuais |
| Suporte multiplataforma | Compatível com Windows / Ubuntu / macOS |
| Sincronização de porta dupla | As portas seriais esquerda e direita operam de forma independente, com suporte a controle remoto de porta dupla sincronizado leader/follower |
| Alternância chinês/inglês | Alterna entre chinês/inglês na interface com um clique, e a escolha é lembrada automaticamente |
| Calibração de centro | Grava a posição atual do servo como o centro 2048 (persistida na EEPROM) |
| Teste de centro | Habilita o torque e move o servo até o centro para verificar o resultado da calibração |
| Desabilitar motores | Desabilita o torque de todos os servos com um clique, para facilitar o ajuste manual |
| Varredura automática | Detecta automaticamente todos os servos online com ID entre 1 e 20 |
| Controle de servo individual | Um controle deslizante ajusta a posição de um servo e liga/desliga o torque em tempo real |
| Depurador FT | Conexão serial, varredura, leitura/escrita de parâmetros, controle de posição, mudança de taxa de baud, reset de fábrica, backup de parâmetros xdat |
| Parâmetros xdat | Salva os parâmetros atuais da EEPROM do servo / abre um backup para restaurar |
| Calibração do LeRobot | Gera arquivos de calibração JSON no formato do LeRobot |
| Ir para o centro a partir de um arquivo de calibração | Move o braço até o centro com base em um arquivo de calibração |

---

## 📚 Tutoriais detalhados

### Chinês

| Sistema | Tutorial |
|-|-|
| Windows | \[Tutorial do Windows\](docs/zh/Windows教程.md) |
| Linux | \[Tutorial do Linux\](docs/zh/Linux教程.md) |
| macOS | \[Tutorial do macOS\](docs/zh/macOS教程.md) |

### Inglês

| Sistema | Guia |
|-|-|
| Windows | \[Guia do Windows\](docs/en/Windows.md) |
| Linux | \[Guia do Linux\](docs/en/Linux.md) |
| macOS | \[Guia do macOS\](docs/en/macOS.md) |

---

## 🖥️ Visão geral da interface

O programa principal tem três abas:

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

- **Barra superior**: título do aplicativo, menus suspensos de seleção de porta, botão de atualizar, botão de controle remoto, botão de alternância de idioma.
- **🦾 Aba1 Servo Calibration**: ações rápidas para os painéis esquerdo e direito (calibração de centro, teste de centro, desabilitar motores) além do status ao vivo.
- **🎚️ Aba2 Single-Servo Control**: ajuste fino da posição de cada servo online com um controle deslizante e ligue/desligue o torque.
- **🔬 Aba3 FT Debugger**: conexão serial, varredura, leitura/escrita de parâmetros, controle de posição, taxa de baud/reset de fábrica, backup e restauração de parâmetros xdat.

---

## 🚀 Início rápido

> Para os tutoriais completos por sistema, veja \[📚 Tutoriais detalhados\](#-详细教程). Abaixo estão os pontos principais para cada sistema.

### Windows

1. Instale o [Python 3.10+](https://www.python.org/downloads/) (marque **Add to PATH**)
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

1. Confirme o número da porta no Gerenciador de Dispositivos (por exemplo `COM3`) e selecione-o na barra superior. Para especificar as portas manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 COM3 --port2 COM4
```

### Linux (Ubuntu / Debian)

1. Instale as fontes CJK e as dependências:

```Bash
sudo apt install python3-venv fonts-noto-cjk fonts-noto-color-emoji
```

1. **⚠️ Adicione as permissões da porta serial (grupo dialout)** [obrigatório]:

```Bash
sudo usermod -a -G dialout $USER
# Passa a valer depois que você sai da sessão e entra novamente
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

1. Os dispositivos seriais são `/dev/ttyUSB0` / `/dev/ttyACM0`. Para especificar manualmente:

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

1. **⚠️ Nomeação da porta serial**: no macOS use `/dev/cu.usbserial-*` (**recomendado, não bloqueante**) em vez de `/dev/tty.*`. Para listá-los:

```Bash
ls /dev/cu.*
```

Para especificar manualmente:

```Bash
python -m src.gui.factory_calibration_tool --port1 /dev/cu.usbserial-0001 --port2 /dev/cu.usbmodem141101
```

### Ferramentas de linha de comando gerais (sem necessidade de GUI)

```Bash
# Escanear servos
python -m src.tools.scan_id

# Calibração rápida do centro do servo
python -m src.tools.servo_quick_calibration

# Teste de centro do servo
python -m src.tools.servo_center_test

# Desabilitar todos os servos
python -m src.tools.servo_disable

# Calibração no estilo LeRobot
python -m src.tools.lerobot_calibrate

# Controle remoto de porta dupla sincronizado
python -m src.tools.servo_remote_control
```

---

## 📖 Etapas de uso

### 1. Conectar e detectar servos

1. Conecte a placa de controle do braço por meio de um adaptador USB-serial e ligue os servos.
2. Abra a GUI e selecione a porta no menu suspenso da barra superior (ou clique em `🔄` para atualizar).
3. A parte superior do painel mostra `🟢 Connected` e escaneia automaticamente os servos online com ID entre 1 e 20 (normalmente 1–6).

> Se ele reportar que a porta está ocupada, certifique-se de que nenhum outro programa (um monitor serial, uma ferramenta aberta anteriormente que não foi encerrada) esteja usando-a.

### 2. Calibração de centro (definir a posição atual como 2048)

> Antes de calibrar, posicione fisicamente o braço de modo que cada junta esteja na posição "zero / centro" desejada.

1. Clique no botão **PortX Center Calibration** no painel.
2. O programa primeiro desabilita os servos e pede que você os mova manualmente até o centro desejado.
3. Depois que você confirma, o programa executa, para cada servo: desbloquear a EEPROM → gravar o comando de calibração (valor 128 no endereço 40) → relockar a EEPROM.
4. Após a calibração, use o "Center test" para verificar: o servo deve permanecer no lugar (movimento muito pequeno), o que significa que a calibração foi bem-sucedida.

### 3. Teste de centro

1. Clique em **PortX Center Test**.
2. O programa habilita o torque e move todos os servos para 2048.
3. Se os servos quase não se moverem da posição atual, a calibração está correta; se se moverem muito, o valor da calibração não é confiável e precisa ser refeito.

### 4. Desabilitar motores (ajuste manual)

- Clique em **PortX Disable Motors** para desligar o torque de todos os servos dessa porta, para que possam ser girados livremente com a mão.
- Para um servo individual, ligue/desligue o torque dele na página **Single-Servo Control**, usando o interruptor de torque abaixo do controle deslizante.

### 5. Alterar o ID de um servo

1. Vá até a página **🔬 FT Debugger**, conecte a porta serial e escaneie os servos.
2. Selecione o servo desejado, altere o valor de "Servo ID" (endereço 0x05) na tabela de parâmetros e clique em write.
3. O programa executa: desbloquear → gravar no endereço 5 → verificar o novo ID → relockar.

> ⚠️ Antes de alterar um ID, certifique-se de que este é o único servo no barramento, para evitar conflitos de ID.

### 6. Alterar a taxa de baud / reset de fábrica

- **Alterar a taxa de baud**: na área "Baud rate / factory reset" da página FT Debugger, selecione a nova taxa de baud (38400 – 1000000 bps) e aplique-a. Após a gravação, a taxa de baud serial é trocada automaticamente e verificada por ping; em caso de falha, ela é revertida automaticamente.
- **Reset de fábrica**: o servo retorna aos padrões de fábrica (ID=1, taxa de baud=1000000); escaneie novamente depois.

### 7. Backup e restauração de parâmetros xdat

Na área "xdat parameters (EEPROM only)" da página FT Debugger:

1. **💾 Save current servo**: salva os parâmetros da EEPROM do servo selecionado no momento em um arquivo xdat (backup).
2. Depois de alterar os parâmetros do servo livremente, se você quiser restaurar:
3. **📂 Open xdat**: carrega o arquivo de backup.
4. **📤 Restore parameters to servo**: regrava o backup na EEPROM do servo atual.

### 8. Controle remoto de porta dupla sincronizado

> ⚠️ **Direção: a Porta 1 controla a Porta 2**. A Porta 1 (leader) apenas lê os ângulos dos servos; a Porta 2 (follower) é controlada em sincronia.

1. Clique em **🎮 Remote** na barra superior (a Porta 1 lê os ângulos → a Porta 2 controla de forma síncrona os servos com os mesmos IDs).
2. Ambas as portas devem ter servos com IDs correspondentes; apenas os servos na interseção são sincronizados.
3. Clique no mesmo botão novamente para parar; depois disso, as threads de varredura dos painéis esquerdo e direito são retomadas automaticamente.

### 9. Calibração do LeRobot (linha de comando)

```Bash
# Calibrar o braço follower (salvo em ~/.cache/huggingface/lerobot/calibration/robots/so_follower/)
python -m src.tools.lerobot_calibrate --arm-type follower

# Calibrar o braço leader
python -m src.tools.lerobot_calibrate --arm-type leader
```

Fluxo: desabilitar os servos → mover cada junta até o centro e registrar `homing_offset` → percorrer lentamente todo o curso e registrar `range_min/max` (o `wrist_roll` é uma junta de rotação contínua com faixa fixa de `[0,4095]`) → salvar o JSON.

Ir para o centro usando um arquivo de calibração:

```Bash
python -m src.tools.run_calibration_middle <校准文件.json> --mode zero
```

---

## ⚠️ Observações



1. **Segurança em primeiro lugar**: a calibração de centro é persistida na EEPROM. Antes de calibrar, certifique-se de que a fonte de alimentação está estável e de que o braço não vai colidir com pessoas ou objetos.
2. **Energia**: para o SoARM 101 padrão, recomenda-se DC 5V 5A; para a versão Pro, DC 12V 5A. Energia insuficiente causa perda de passos do servo ou falhas de comunicação.
3. **Exclusividade da porta serial**: no Windows a porta é bloqueada de forma exclusiva, então a mesma porta não pode ser usada ao mesmo tempo pela thread de varredura da GUI e pelo subprocesso de calibração. A ferramenta interrompe automaticamente a thread de varredura e encerra o processo antigo antes de operar; não clique repetidamente com a mão.
4. **Permissões seriais no Linux**: acessar `/dev/ttyUSB*` / `/dev/ttyACM*` exige adicionar o usuário ao grupo `dialout` (veja o \[Tutorial do Linux\](docs/zh/Linux教程.md)).
5. **Nomeação serial no macOS**: use `/dev/cu.*` (não bloqueante) em vez de `/dev/tty.*` (bloqueante, pode travar); veja o \[Tutorial do macOS\](docs/zh/macOS教程.md).
6. **Hot-plug**: depois de desconectar o USB, o programa tenta se reconectar automaticamente; depois de reconectá-lo, clique em `🔄` para atualizar a lista de portas.
7. **Proteção contra sobretemperatura / sobretensão**: o programa monitora tensão e temperatura (alarme acima de 60°C). Se os servos continuarem quentes, pare e deixe-os esfriar.
8. **A calibração de centro é irreversível**: após a gravação, o deslocamento original é sobrescrito e não pode ser desfeito. Registre a posição original antes de calibrar.
9. **Risco de alteração de ID**: se a gravação ou a verificação falhar, o programa reporta um erro e retoma a varredura, mas, em casos extremos, o servo pode ficar "perdido". Se isso acontecer, tente "Factory reset" (após o reset o ID volta a 1).
10. **Problema de codificação**: se os emojis aparecerem ilegíveis no console do Windows, defina `PYTHONIOENCODING=utf-8` antes de executar as ferramentas de linha de comando. Linux/macOS com UTF-8 nativo geralmente não têm esse problema.

---

## 🛠️ Solução de problemas

| Sintoma | Causa possível | Solução |
|-|-|-|
| Não é possível abrir a porta serial / porta ocupada | Outro programa está usando-a | Feche programas como monitores seriais, ou troque de porta e reinicie a ferramenta |
| Nenhum servo encontrado na varredura | Energia insuficiente / fiação errada / taxa de baud incompatível | Verifique a energia e a fiação, e confirme que os servos estão a 1M de taxa de baud |
| Os servos disparam após a calibração de centro | A pose não foi definida corretamente antes da calibração | Refaça "desabilitar → posicionar manualmente → calibração de centro" |
| A temperatura sobe rápido demais | Carga excessiva ou travamento | Verifique se o mecanismo está preso; reduza a velocidade/aceleração |
| Servo não encontrado após alterar o ID | Conflito de ID ou falha na gravação | Faça o reset de fábrica e escaneie novamente |
| Controle remoto fora de sincronia | As duas portas têm IDs incompatíveis | Confirme que servos com o mesmo ID estão online tanto na porta leader quanto na follower |

---

## 📁 Estrutura de diretórios

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
│   ├── gui/                  # GUI em PySide6
│   │   ├── factory_calibration_tool.py   # Ferramenta principal (calibração de porta dupla + controle remoto + alternância de idioma)
│   │   ├── ft_debugger.py                # Depurador FT (leitura/escrita de parâmetros / backup xdat)
│   │   ├── calibration_wizard.py         # Assistente de calibração do LeRobot
│   │   ├── theme_utils.py                # Tema claro
│   │   └── language_dialog.py            # Diálogo de seleção de idioma
│   ├── tools/                # Ferramentas de linha de comando
│   ├── xdat_utils.py         # Leitura/escrita de arquivos de parâmetros xdat
│   ├── i18n*.py / i18n_translations/     # Internacionalização chinês/inglês
│   ├── port_utils.py         # Detecção de porta serial
│   └── calibration_manager.py# Gerenciamento de arquivos de calibração do LeRobot
├── scservo_sdk/              # SDK de comunicação do servo FTServo
├── requirements.txt
└── setup.py                  # Script de verificação de ambiente
```
