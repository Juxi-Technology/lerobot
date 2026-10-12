[English](../en/so-arm101-tutorial.md) | [简体中文](../zh-hans/so-arm101-tutorial.md) | [繁體中文](../zh-hant/so-arm101-tutorial.md) | [Deutsch](../de/so-arm101-tutorial.md) | [Español](../es/so-arm101-tutorial.md) | [Français](../fr/so-arm101-tutorial.md) | [Italiano](../it/so-arm101-tutorial.md) | [日本語](../ja/so-arm101-tutorial.md) | [한국어](../ko/so-arm101-tutorial.md) | Português (BR) | [Português (PT)](../pt-pt/so-arm101-tutorial.md)

<title>Tutorial do braço robótico SO-ARM101</title>

# Visão geral do produto

O SO-ARM101 é um **braço robótico de 6 graus de liberdade de baixo custo e totalmente de código aberto** desenvolvido pela equipe LeRobot, da Hugging Face, projetado para introdução educacional, validação de pesquisa e prototipagem industrial leve. Com alta flexibilidade e um ecossistema de código aberto completo, ele reduz a barreira para aplicar inteligência incorporada e tecnologia de robótica.

### 1. Design de hardware: alto desempenho, modular, fácil de montar e personalizar

- **Material estrutural**: a estrutura principal combina peças impressas em 3D com componentes de sustentação reforçados, com passagem de cabos e design de juntas otimizados para evitar interferência de movimento, equilibrando leveza e durabilidade; os usuários podem imprimir peças de reposição ou de extensão por conta própria.
- **Configuração de acionamento**: o braço Follower conta com **6 servos de alto torque com encoder magnético de 12V 30KG**, combinados com feedback de encoder magnético de 360° e um algoritmo de controle PID — movimento suave e sem tremores, alta precisão de posicionamento repetido, potência forte e movimento preciso.
- **Sistema de visão**: vem de fábrica com um **sistema de visão inteligente de câmera dupla**; a câmera da extremidade captura detalhes da preensão de perto, enquanto a câmera global cobre o ambiente de trabalho. A fusão dos dados das duas câmeras constrói um modelo 3D e fornece um rico suporte de dados para o aprendizado por imitação.
- **Conexão de controle**: equipado com uma placa driver de servo que se conecta diretamente a um PC ou Raspberry Pi por uma interface USB-C — plug and play, o que simplifica o processo de conexão de hardware e permite montar o ambiente de controle rapidamente.

### 2. Ecossistema de software: integrado profundamente ao LeRobot, desenvolvimento de IA sem barreiras

- **Compatibilidade com o framework principal**: profundamente adaptado ao **framework de ML para robôs de código aberto LeRobot** da Hugging Face, baseado em PyTorch, com modelos pré-treinados, datasets multiuso e um ambiente de simulação integrados, e compatível com datasets de código aberto conhecidos, como o Stanford ALOHA.
- **Comunicação de baixa latência**: usa o **motor de fluxo de dados distribuído DORA** para interação de baixa latência entre hardware e algoritmos; o Python roda 17 vezes mais rápido que o ROS2, e o recarregamento a quente de código é suportado, para você ajustar as policies em tempo real sem reiniciar.
- **Código aberto em toda a pilha**: os arquivos de impressão 3D do hardware, o código de controle do software, os scripts de treinamento de IA e todo o conjunto de tutoriais são **totalmente de código aberto**; os usuários podem modificá-los e desenvolvê-los livremente para implementar rapidamente extensões de recursos personalizadas.

### 3. Cenários de aplicação principais: adequação a todos os cenários, da introdução à implantação

1. **Introdução à educação em robótica**: oferece um tutorial ponta a ponta, da montagem do braço e programação básica até a implantação da policy de IA, com uma interface de operação visual e código de exemplo, para que iniciantes dominem rapidamente o controle de robôs e as habilidades de aplicação de IA.
2. **Validação de algoritmos em pesquisa**: focado em pesquisa de **aprendizado por imitação e aprendizado por reforço**, com suporte para gravar dados de operação humana via VR para treinar o robô; um caso típico: com base em 50 clipes de vídeo de operação de 15 segundos, 2 horas de treinamento bastam para dominar tarefas como dobrar roupas, inserir uma chave e separar materiais.
3. **Prototipagem industrial leve**: validação de baixo custo de soluções de automação, adequada a cenários como **movimentação de materiais, montagem de precisão e triagem de peças**, entregando as funções principais de um braço robótico de nível industrial a um custo da faixa de mil yuans, para validação rápida de protótipos.

### 4. Vantagens do produto

- **Custo-benefício extremo**: a versão básica começa em cerca de US$ 100, e o design de código aberto reduz os custos de aquisição e desenvolvimento secundário, tornando-o adequado à implantação em lote por indivíduos, laboratórios e pequenas e médias empresas.
- **Código aberto em toda a cadeia**: hardware, software e tutoriais são totalmente abertos, sem barreiras técnicas, permitindo personalização e extensão de recursos livremente para atender rapidamente a muitos cenários.
- **Amigável ao desenvolvimento de IA**: com o respaldo do ecossistema LeRobot, chama modelos pré-treinados e datasets com um clique, simplificando todo o fluxo, da coleta de dados e treinamento da policy até a implantação, e acelerando a adoção de algoritmos de inteligência incorporada.

### 5. Especificações do produto

| **Especificação** | **Detalhes** |
|-|-|
| Graus de liberdade | 6 eixos (rotação / inclinação do ombro, flexão do cotovelo, flexão / rotação do punho, abertura/fechamento da garra) |
| Material estrutural | Peças impressas em 3D (PLA+) |
| Motores de acionamento | 12 \* servomotores Feetech STS3215 (alimentação de 12V)  <br/>Relação de engrenagem do braço Follower STS3215-C018: 1/345  <br/>Relação de engrenagem do braço Leader STS3215-C001: 1/345 (ombro), STS3215-C044 1/191 (cotovelo), STS3215-C046 1/147 (punho) |
| Capacidade de carga útil | Carga útil máxima na extremidade 200g (garra fechada) |
| Precisão de posicionamento repetido | ±1,5mm (afetada pela calibração e pela folga do motor) |
| Raio de trabalho | Alcance máximo da extremidade 350mm |
| Requisitos de energia | Leader: adaptador 5V 6A; Follower: adaptador 12V 5A (para demandas de alto torque) |
| Interface de comunicação | Conexão direta USB-C ao PC (transferência de comandos de controle) |
| Sistema de visão | Câmera (1080P@30FPS, FOV 86° sem distorção, ou foco fixo 1080P@60FPS FOV 100°) |
| Tipo de garra | Garra PLA+, garra TPU, garra de dois dedos paralelos, abertura de 0-50mm, força máxima de preensão 5N |
| Framework de controle | Biblioteca LeRobot baseada em Python, que fornece uma API de controle de motor (lerobot.control) |
| Modelos pré-treinados | Suporta algoritmos de aprendizado por imitação como ACT (Action Chunking Transformer) e Diffusion Policy |
| Modelo leve | Modelo de visão-linguagem-ação SmolVLA (450M parâmetros): ・Inferência em tempo real na CPU (roda em MacBook) ・Resposta assíncrona 30% mais rápida ・Apenas 64 tokens visuais por quadro ・Visualização de estado: monitoramento em tempo real com a biblioteca rerun |
| Peso total | ≈1,2kg (incluindo motores e cabos) |
| Dimensões montadas | Diâmetro da base 120mm, altura (totalmente estendido) 650mm |
| Temperatura de operação | 0℃–40℃ (limite do servomotor) |
| Nível de ruído | <45dB (operação sem carga) |
| Tutorial para iniciantes | Sim |
| GITHUB oficial | Sim |

![A imagem mostra diagramas de dimensões dos braços Leader e Follower do braço robótico SO-ARM101, junto com o nome do produto, o material, as dimensões e outras informações. Os diagramas de dimensões indicam o tamanho de cada peça, por exemplo, o braço Leader tem 525mm de comprimento e o braço Follower tem 532mm de comprimento. O material do produto é PLA+ com otimização topológica e as dimensões do produto são 111x239x525mm (Leader) e 111x173x532mm (Follower). Esta imagem corresponde à seção Especificações do produto do documento e apresenta visualmente as especificações dimensionais do braço.](../en/images/d01-01.png)

| **Item / nome do pacote** | **Função / descrição** |
|-|-|
| Biblioteca LeRobot | Versão: ≥0.1.0 Framework de controle principal: • API Python (lerobot.control) ・Planejamento de movimento em tempo real ・Processamento de fluxo de dados de sensores |
| PyTorch | Versão: ≥2.0 Motor de inferência de aprendizado profundo (suporta modelos como SmolVLA) |
| Transformers | Versão: ≥4.40.0 Biblioteca de modelos Hugging Face (carrega ACT/Diffusion Policy pré-treinados) |
| rerun | Versão: ≥0.16.0 Ferramenta de visualização de estado do robô em tempo real (renderização de ângulo de junta / trajetória em 3D) |
| ROS 2 | Versão: Humble/Foxy Opcional: Interface de driver ROS2 (pacote soarm100_ros) |
| ACT | Action Chunking Transformer, previsão de ações de longa sequência (por exemplo, tarefas de preensão contínua) |
| Diffusion Policy | Política de difusão, controle robusto em espaços de ação de alta dimensão (manipulação resistente a perturbações) |
| SmolVLA | Modelo de visão-linguagem-ação, execução de instruções multimodais (por exemplo, "pegar o bloco vermelho") ・450M parâmetros, funciona em CPU/GPU |

| **Categoria de função** | **Descrição da função** |
|-|-|
| Controle em nível de junta | ・Controle independente de ângulo / velocidade em 6 eixos (faixa de ±180°) ・Proteção de limite flexível da junta ・Feedback em tempo real da temperatura / tensão do motor |
| Controle no espaço cartesiano | ・Posicionamento por coordenadas XYZ da extremidade (precisão ±1,5mm) ・Ajuste de orientação por ângulos de Euler (Roll/Pitch/Yaw) |
| Operação da garra | ・Ajuste contínuo de abertura de 0-50mm ・Ajuste dinâmico da força de preensão (0,1-5N) ・Preensão adaptável à espessura do objeto |
| Modo Leader/Follower | ・Ensino manual com o braço Leader → imitação em tempo real pelo braço Follower ・Gravação / reprodução de dados de ações |

| **Categoria de função** | **Descrição da função** |
|-|-|
| Aprendizado por imitação | ・Gravação de dados de demonstração humana → treinamento de modelos ACT/Diffusion Policy ・Suporte à transferência de policy multitarefa (por exemplo, empilhar blocos → separar objetos) |
| Interação multimodal | ・O modelo SmolVLA interpreta instruções em linguagem natural (por exemplo, "pegar o bloco azul") ・Execução ponta a ponta de visão-ação |
| Interface de aprendizado por reforço | ・Ambiente compatível com Gymnasium ・Funções de recompensa personalizadas (por exemplo, tempo de conclusão da tarefa / otimização de energia) |
| Sistema de calibração | ・Calibração de ponto zero Leader/Follower ・Calibração mão-olho entre câmera e braço ・Compensação automática de torque da junta |
| Gerenciamento de fluxo de dados | ・Gravação / reprodução de datasets em formato .h5 ・Sincronização na nuvem com o Hugging Face Hub ・Alinhamento de carimbo de tempo dos dados dos sensores |
| Monitoramento em tempo real | ・Visualização com rerun dos ângulos das juntas / trajetória da extremidade ・Alertas de anomalia do motor (superaquecimento / travamento) ・Diagnóstico de latência de comunicação |
| Integração com ROS 2 | ・Publicar estados das juntas (/joint_states) ・Assinar comandos de controle (/arm_controller) ・Transferência de fluxo de nuvem de pontos (/depth_points) |
| Implantação multiplataforma | • Linux/Windows/macOS (API Python) ・Containerização com Docker ・Controle remoto via web (interface FastAPI) |
