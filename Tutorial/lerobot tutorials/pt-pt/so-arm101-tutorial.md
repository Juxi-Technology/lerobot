[English](../en/so-arm101-tutorial.md) | [简体中文](../zh-hans/so-arm101-tutorial.md) | [繁體中文](../zh-hant/so-arm101-tutorial.md) | [Deutsch](../de/so-arm101-tutorial.md) | [Español](../es/so-arm101-tutorial.md) | [Français](../fr/so-arm101-tutorial.md) | [Italiano](../it/so-arm101-tutorial.md) | [日本語](../ja/so-arm101-tutorial.md) | [한국어](../ko/so-arm101-tutorial.md) | [Português (BR)](../pt-br/so-arm101-tutorial.md) | Português (PT)

<title>SO-ARM101 Robotic Arm Tutorial</title>

# Visão Geral do Produto

O SO-ARM101 é um **braço robótico de 6 graus de liberdade de baixo custo e totalmente de código aberto**, construído pela equipa LeRobot, da Hugging Face, concebido para iniciação educativa, validação de investigação e prototipagem industrial leve. Com elevada flexibilidade e um ecossistema de código aberto completo, reduz a barreira à aplicação da inteligência corporizada e da tecnologia robótica.

### 1. Conceção de Hardware: Alto Desempenho, Modular, Fácil de Montar e Personalizar

- **Material estrutural**: a estrutura central combina peças impressas em 3D com componentes reforçados de suporte de carga, com encaminhamento de cabos e conceção das juntas otimizados para evitar interferências de movimento, equilibrando a leveza e a durabilidade; os utilizadores podem imprimir eles próprios peças de substituição ou de extensão.
- **Configuração de acionamento**: o braço Follower tem **6 servos de binário elevado de 12V 30KG com encoder magnético**, combinados com feedback de encoder magnético de 360° e um algoritmo de controlo PID — movimento suave, sem tremores, elevada precisão de posicionamento repetível, grande potência e movimento preciso.
- **Sistema de visão**: vem de série com um **sistema de visão inteligente com duas câmaras**; a câmara do efetuador final capta o detalhe da preensão à curta distância, enquanto a câmara global cobre o ambiente de trabalho. A fusão dos dados de ambas as câmaras constrói um modelo 3D e fornece um rico suporte de dados para a aprendizagem por imitação.
- **Ligação de controlo**: equipado com uma placa controladora de servos que se liga diretamente a um PC ou a um Raspberry Pi através de uma interface USB-C — plug and play, o que simplifica o processo de ligação do hardware e permite-lhe construir rapidamente o ambiente de controlo.

### 2. Ecossistema de Software: Profundamente Integrado com o LeRobot, Desenvolvimento de IA Sem Barreiras

- **Compatibilidade com a estrutura central**: profundamente adaptado à **estrutura de aprendizagem automática para robôs de código aberto LeRobot da Hugging Face**, construída sobre PyTorch, com modelos pré-treinados integrados, conjuntos de dados multi-cenário e um ambiente de simulação, e compatível com conjuntos de dados de código aberto conhecidos como o Stanford ALOHA.
- **Comunicação de baixa latência**: utiliza o **motor de fluxo de dados distribuído DORA** para interação de baixa latência entre o hardware e os algoritmos; o Python corre 17 vezes mais depressa do que o ROS2, e o recarregamento de código a quente é suportado, para que possa ajustar as políticas em tempo real sem reiniciar.
- **Código aberto de pilha completa**: os ficheiros de impressão 3D do hardware, o código de controlo do software, os scripts de treino de IA e todo o conjunto de tutoriais são **completamente de código aberto**; os utilizadores podem modificá-los e desenvolvê-los livremente para implementar rapidamente extensões de funcionalidades personalizadas.

### 3. Cenários de Aplicação Principais: Adequação a Todos os Cenários, do Início à Implementação

1. **Iniciação à educação em robótica**: disponibiliza um tutorial ponta a ponta desde a montagem do braço e a programação básica até à implementação de políticas de IA, com uma interface de operação visual e código de exemplo, para que os principiantes dominem rapidamente o controlo de robôs e as competências de aplicação de IA.
2. **Validação de algoritmos de investigação**: centrado na investigação em **aprendizagem por imitação e aprendizagem por reforço**, com suporte para gravar dados de operação humana através de VR para treinar o robô; um caso típico: a partir de 50 clipes de vídeo de operação de 15 segundos, 2 horas de treino bastam para dominar tarefas como dobrar roupa, inserir uma chave e separar materiais.
3. **Prototipagem industrial leve**: validação de baixo custo de soluções de automação, adequada a cenários como **manuseamento de materiais, montagem de precisão e separação de peças**, entregando as funções centrais de um braço robótico de nível industrial a um custo da ordem dos milhares de yuan, para uma validação rápida de protótipos.

### 4. Vantagens do Produto

- **Relação qualidade-preço extrema**: a versão básica começa em cerca de $100, e a conceção de código aberto reduz os custos de aquisição e de desenvolvimento secundário, tornando-o adequado para implementação em lote por particulares, laboratórios e pequenas e médias empresas.
- **Código aberto em toda a cadeia**: o hardware, o software e os tutoriais são todos totalmente abertos, sem barreiras técnicas, suportando personalização e extensão de funcionalidades livres para se adequar rapidamente a muitos cenários.
- **Amigo do desenvolvimento de IA**: com o apoio do ecossistema LeRobot, chama modelos pré-treinados e conjuntos de dados com um clique, simplificando todo o fluxo desde a recolha de dados e o treino de políticas até à implementação, e acelerando a divulgação dos algoritmos de inteligência corporizada.

### 5. Especificações do Produto

| **Especificação** | **Detalhes** |
|-|-|
| Graus de liberdade | 6 eixos (rotação / inclinação do ombro, flexão do cotovelo, flexão / rotação do punho, abertura/fecho da pinça) |
| Material estrutural | Peças impressas em 3D (PLA+) |
| Motores de acionamento | 12 \* servomotores Feetech STS3215 (alimentação de 12V)  <br/>Braço follower STS3215-C018 relação de engrenagem: 1/345  <br/>Braço leader STS3215-C001 relação de engrenagem: 1/345 (ombro), STS3215-C044 1/191 (cotovelo), STS3215-C046 1/147 (punho) |
| Capacidade de carga | Carga máxima no efetuador final 200g (pinça fechada) |
| Precisão de posicionamento repetível | ±1.5mm (afetada pela calibração e pela folga do motor) |
| Raio de trabalho | Alcance máximo do efetuador final 350mm |
| Requisitos de energia | Leader: adaptador de 5V 6A; Follower: adaptador de 12V 5A (para exigências de binário elevado) |
| Interface de comunicação | Ligação direta USB-C ao PC (transferência de comandos de controlo) |
| Sistema de visão | Câmara (1080P@30FPS, FOV86° sem distorção, ou foco fixo 1080P@60FPS FOV100°) |
| Tipo de pinça | Pinça PLA+, pinça TPU, pinça de duas maxilas paralelas suportada, abertura de 0-50mm, força de preensão máxima 5N |
| Estrutura de controlo | Biblioteca LeRobot baseada em Python, que fornece uma API de controlo de motores (lerobot.control) |
| Modelos pré-treinados | Suporta algoritmos de aprendizagem por imitação como ACT (Action Chunking Transformer) e Diffusion Policy |
| Modelo leve | Modelo de visão-linguagem-ação SmolVLA (450M parâmetros): ・Inferência em tempo real na CPU (corre num MacBook) ・Resposta assíncrona 30% mais rápida ・Apenas 64 tokens visuais por fotograma ・Visualização de estado: monitorização em tempo real com a biblioteca rerun |
| Peso total | ≈1.2kg (incluindo motores e cabos) |
| Dimensões montado | Diâmetro da base 120mm, altura (completamente estendido) 650mm |
| Temperatura de funcionamento | 0℃–40℃ (limite do servomotor) |
| Nível de ruído | <45dB (funcionamento sem carga) |
| Tutorial para principiantes | Sim |
| GITHUB oficial | Sim |

![A imagem mostra diagramas de dimensões dos braços Leader e Follower do braço robótico SO-ARM101, juntamente com o nome do produto, o material, as dimensões e outras informações. Os diagramas de dimensões rotulam o tamanho de cada peça, por exemplo o braço Leader tem 525mm de comprimento e o braço Follower tem 532mm de comprimento. O material do produto é PLA+ com otimização topológica e as dimensões do produto são 111x239x525mm (Leader) e 111x173x532mm (Follower). Esta imagem corresponde à secção Especificações do Produto do documento e apresenta visualmente as especificações dimensionais do braço.](../en/images/d01-01.png)

| **Item / nome do pacote** | **Função / descrição** |
|-|-|
| Biblioteca LeRobot | Versão: ≥0.1.0 Estrutura de controlo central: • API Python (lerobot.control) ・Planeamento de movimento em tempo real ・Processamento de fluxos de dados de sensores |
| PyTorch | Versão: ≥2.0 Motor de inferência de aprendizagem profunda (suporta modelos como o SmolVLA) |
| Transformers | Versão: ≥4.40.0 Biblioteca de modelos Hugging Face (carrega ACT/Diffusion Policy pré-treinados) |
| rerun | Versão: ≥0.16.0 Ferramenta de visualização do estado do robô em tempo real (renderização 3D de ângulos de junta / trajetórias) |
| ROS 2 | Versão: Humble/Foxy Opcional: interface de controlador ROS2 (pacote soarm100_ros) |
| ACT | Action Chunking Transformer, previsão de ações de sequência longa (por exemplo tarefas de preensão contínua) |
| Diffusion Policy | Política de difusão, controlo robusto em espaços de ação de elevada dimensão (manipulação resistente a perturbações) |
| SmolVLA | Modelo de visão-linguagem-ação, execução de instruções multimodais (por exemplo "agarra o bloco vermelho") ・450M parâmetros, funciona em CPU/GPU |

| **Categoria de função** | **Descrição da função** |
|-|-|
| Controlo ao nível das juntas | ・Controlo independente de ângulo / velocidade em 6 eixos (intervalo de ±180°) ・Proteção de limite suave das juntas ・Feedback em tempo real da temperatura / tensão do motor |
| Controlo no espaço cartesiano | ・Posicionamento do efetuador final por coordenadas XYZ (precisão ±1.5mm) ・Ajuste da orientação por ângulos de Euler (Roll/Pitch/Yaw) |
| Operação da pinça | ・Ajuste de abertura de 0-50mm contínuo ・Ajuste dinâmico da força de preensão (0.1-5N) ・Preensão adaptativa à espessura do objeto |
| Modo Leader/Follower | ・Ensino manual com o braço Leader → imitação em tempo real pelo braço Follower ・Gravação / reprodução de dados de ações |

| **Categoria de função** | **Descrição da função** |
|-|-|
| Aprendizagem por imitação | ・Gravação de dados de demonstração humana → treino de modelos ACT/Diffusion Policy ・Suporte para transferência de políticas multitarefa (por exemplo empilhar blocos → separar objetos) |
| Interação multimodal | ・O modelo SmolVLA interpreta instruções em linguagem natural (por exemplo "agarra o bloco azul") ・Execução visão-ação ponta a ponta |
| Interface de aprendizagem por reforço | ・Ambiente compatível com Gymnasium ・Funções de recompensa personalizadas (por exemplo tempo de conclusão da tarefa / otimização de energia) |
| Sistema de calibração | ・Calibração do ponto zero Leader/Follower ・Calibração mão-olho câmara-braço ・Compensação automática do binário das juntas |
| Gestão de fluxos de dados | ・Gravação / reprodução de conjuntos de dados em formato .h5 ・Sincronização na nuvem do Hugging Face Hub ・Alinhamento temporal dos dados dos sensores |
| Monitorização em tempo real | ・Visualização com rerun dos ângulos das juntas / trajetória do efetuador final ・Alarmes de anomalia do motor (sobreaquecimento / bloqueio) ・Diagnóstico da latência de comunicação |
| Integração com ROS 2 | ・Publicar estados das juntas (/joint_states) ・Subscrever comandos de controlo (/arm_controller) ・Transferência de fluxo de nuvem de pontos (/depth_points) |
| Implementação multiplataforma | • Linux/Windows/macOS (API Python) ・Contentorização Docker ・Controlo remoto por Web (interface FastAPI) |
