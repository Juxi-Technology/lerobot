[English](../en/index.md) | [简体中文](../zh-hans/index.md) | [繁體中文](../zh-hant/index.md) | [Deutsch](../de/index.md) | [Español](../es/index.md) | [Français](../fr/index.md) | [Italiano](../it/index.md) | [日本語](../ja/index.md) | [한국어](../ko/index.md) | [Português (BR)](../pt-br/index.md) | Português (PT)

# Índice

## **Clique nos dois ícones no canto superior esquerdo para expandir a lista completa de capítulos**

![A imagem mostra um ícone formado por um ponto e três linhas paralelas. Este ícone aparece num documento que apresenta o LeRobot, cujo contexto o descreve como a estrutura de software de robôs inteligentes corporizados de código aberto da HuggingFace, que reduz a barreira à recolha de dados, ao treino de algoritmos e à implementação de inferência para aprendizagem por reforço e aprendizagem por imitação (VLA), sendo a aprendizagem por imitação (VLA) o foco principal. Este ícone pode representar a estrutura de software LeRobot ou uma funcionalidade relacionada.](../en/images/d02-01.png)

![A imagem mostra um ícone de reprodução, um triângulo branco, situado no canto inferior esquerdo da moldura. Este ícone está relacionado com a apresentação do LeRobot no documento, que é a estrutura de software de robôs inteligentes corporizados de código aberto da HuggingFace, que reduz a barreira à recolha de dados, ao treino de algoritmos e à implementação de inferência para aprendizagem por reforço e aprendizagem por imitação (VLA), sendo a aprendizagem por imitação (VLA) o foco principal. Este ícone pode indicar conteúdo de vídeo ou de demonstração para ajudar os utilizadores a compreender o material sobre o LeRobot.](../en/images/d02-02.png)

![A imagem mostra o texto "Speedrunning Embodied Intelligence VLA" sobre um fundo com um gradiente claro. Na moldura, uma mão segura um objeto branco enquanto outra mão opera um braço robótico com cablagem vermelha. Surge um balão de fala com a palavra "Grab!" no canto inferior direito. A imagem está relacionada com a apresentação do LeRobot no documento, uma estrutura de software de robôs inteligentes corporizados que reduz a barreira à aprendizagem por imitação (VLA); esta imagem poderá destinar-se a apresentar visualmente a utilização de VLA na manipulação robótica e o seu papel na aprendizagem por imitação.](../en/images/d02-03.png)

## O que é a Inteligência Corporizada?

Inteligência com um corpo. Liga a IA a diversas entidades físicas de hardware, tais como:

Cães robóticos quadrúpedes, robôs humanoides bípedes, robôs com rodas e pernas, drones, carros autónomos

## O que é o LeRobot?

O LeRobot é a `estrutura de software de robôs inteligentes corporizados` de código aberto da HuggingFace

Endereço GitHub: https://github.com/huggingface/lerobot

Reduz a barreira à **recolha de dados, ao treino de algoritmos e à implementação de inferência** para aprendizagem por reforço e **aprendizagem por imitação (VLA)**, sendo a **aprendizagem por imitação (VLA)** o foco principal

- Que robôs podem ser desenvolvidos com o LeRobot?

Desde o braço robótico SO-ARM 101 da classe dos milhares de yuan e o carrinho LeKiwi, até ao braço AgileX piper da casa dos dez milhares de yuan, ao braço Huaxinjing StarAI e à mão dextra Hope-JR, e ainda ao robô humanoide Unitree G1 da casa das centenas de milhares de yuan. O LeRobot tornou-se o padrão para a recolha de dados e o treino de algoritmos no setor da inteligência corporizada.

Também pode adaptar o seu próprio robô à estrutura LeRobot.

- Conjuntos de dados e modelos LeRobot

O LeRobot define o seu próprio formato de conjunto de dados de aprendizagem por imitação. Pode ver, utilizar, descarregar e treinar com todos os conjuntos de dados e modelos públicos no HuggingFace, e também pode carregar os seus próprios conjuntos de dados para o HuggingFace.

## O que é o Braço Robótico SO-ARM 101?

Este tutorial toma como exemplo o braço robótico SO-ARM 101; utiliza peças estruturais impressas em 3D e servos Feetech, a um custo muito baixo.

Trata-se de um corpo de inteligência corporizada que até um estudante sem recursos pode pagar, e é um dos corpos oficialmente recomendados pelo LeRobot.

O braço é composto por dois braços: um braço Leader e um braço Follower. Cada braço tem 5 graus de liberdade mais 1 grau de liberdade da pinça.

## Que Configuração de Computador Preciso

Um portátil Windows comum consegue fazer tudo até ao treino.

Um Mac comum consegue fazer tudo.

Uma máquina Ubuntu com uma GPU NVIDIA consegue fazer tudo.

Neste tutorial utilizamos uma [plataforma de GPU na nuvem](https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1) para treinar os modelos, por isso o seu próprio computador não precisa de uma configuração de topo.

## O que é a **Aprendizagem por Imitação e o VLA**?

Um humano arrasta o robô para demonstrar e recolher um conjunto de dados. Esse conjunto de dados é depois usado para treinar um algoritmo de aprendizagem por imitação, que é finalmente implementado no robô, permitindo-lhe imitar autonomamente as ações humanas e generalizar para o ambiente real. Não é necessária teleoperação nem controlo remoto.

Por exemplo, no vídeo acima, um humano arrasta o braço robótico SO-ARM para agarrar um lagostim-de-água-doce, mergulhá-lo em tempero e deixá-lo cair em óleo quente, e o braço acaba por executar esta ação sozinho. Mesmo com um lagostim novo, consegue reagir e completar a ação em qualquer momento.

A aprendizagem por imitação tem também um nome moderno e de vanguarda: VLA (modelo de grande dimensão Visão-Linguagem-Ação). É também o campo de investigação em inteligência corporizada que atualmente cresce mais depressa, atrai o investimento mais cobiçado, assiste à competição China-EUA mais feroz, desfruta do ecossistema de código aberto mais próspero, atrai intensa atenção dos media e cativa inúmeros estudantes de mestrado e doutoramento.

Os algoritmos que o LeRobot adapta principalmente são os de aprendizagem por imitação, tais como ACT, Diffusion Policy, SmolVLA, Pi0, Pi0.5, Wall-OSS e outros.

A aprendizagem por imitação neste tutorial é exclusivamente VLA.
