[English](../en/index.md) | [简体中文](../zh-hans/index.md) | [繁體中文](../zh-hant/index.md) | [Deutsch](../de/index.md) | [Español](../es/index.md) | [Français](../fr/index.md) | [Italiano](../it/index.md) | [日本語](../ja/index.md) | [한국어](../ko/index.md) | Português (BR) | [Português (PT)](../pt-pt/index.md)

# Conteúdo

## **Clique nos dois ícones no canto superior esquerdo para expandir a lista completa de capítulos**

![A imagem mostra um ícone formado por um ponto e três linhas paralelas. Esse ícone aparece em um documento que apresenta o LeRobot, cujo contexto descreve o LeRobot como o framework de software de robôs inteligentes incorporados de código aberto da HuggingFace, que reduz a barreira para coleta de dados, treinamento de algoritmos e implantação de inferência em aprendizado por reforço e aprendizado por imitação (VLA), com o aprendizado por imitação (VLA) como foco principal. Esse ícone pode representar o framework de software LeRobot ou um recurso relacionado.](../en/images/d02-01.png)

![A imagem mostra um ícone de botão de reprodução, um triângulo branco, localizado no canto inferior esquerdo do quadro. Esse ícone está relacionado à apresentação do LeRobot feita no documento, que é o framework de software de robôs inteligentes incorporados de código aberto da HuggingFace, que reduz a barreira para coleta de dados, treinamento de algoritmos e implantação de inferência em aprendizado por reforço e aprendizado por imitação (VLA), com o aprendizado por imitação (VLA) como foco principal. Esse ícone pode indicar conteúdo de vídeo ou demonstração para ajudar os usuários a entender o material do LeRobot.](../en/images/d02-02.png)

![A imagem mostra o texto "Speedrunning Embodied Intelligence VLA" sobre um fundo em degradê claro. No quadro, uma mão segura um objeto branco enquanto outra mão opera um braço robótico com fiação vermelha. Um balão de fala com o texto "Grab!" aparece no canto inferior direito. A imagem está relacionada à apresentação do LeRobot feita no documento, um framework de software de robôs inteligentes incorporados que reduz a barreira do aprendizado por imitação (VLA); essa figura pode ter o objetivo de apresentar visualmente o uso de VLA na manipulação robótica e seu papel no aprendizado por imitação.](../en/images/d02-03.png)

## O que é inteligência incorporada?

Inteligência com um corpo. Ela conecta a IA a diversas entidades físicas de hardware, como:

Cães robôs quadrúpedes, robôs humanoides bípedes, robôs com rodas e pernas, drones, carros autônomos

## O que é o LeRobot?

O LeRobot é o `framework de software de robôs inteligentes incorporados` de código aberto da HuggingFace

Endereço no GitHub: https://github.com/huggingface/lerobot

Ele reduz a barreira para **coleta de dados, treinamento de algoritmos e implantação de inferência** em aprendizado por reforço e **aprendizado por imitação (VLA)**, com o **aprendizado por imitação (VLA)** como foco principal

- Quais robôs podem ser desenvolvidos com o LeRobot?

Do braço robótico SO-ARM 101, da faixa de mil yuans, e do carrinho LeKiwi, passando pelo braço AgileX piper, da faixa de dezenas de milhares de yuans, pelo braço Huaxinjing StarAI e pela mão hábil Hope-JR, até o robô humanoide Unitree G1, da faixa de centenas de milhares de yuans. O LeRobot se tornou o padrão para coleta de dados e treinamento de algoritmos na indústria da inteligência incorporada.

Você também pode adaptar o seu próprio robô ao framework LeRobot.

- Datasets e modelos do LeRobot

O LeRobot define seu próprio formato de dataset de aprendizado por imitação. Você pode visualizar, usar, baixar e treinar com todos os datasets e modelos públicos no HuggingFace, e também pode enviar seus próprios datasets para o HuggingFace.

## O que é o braço robótico SO-ARM 101?

Este tutorial usa o braço robótico SO-ARM 101 como exemplo; ele utiliza peças estruturais impressas em 3D e servos Feetech, a um custo muito baixo.

Este é um corpo de inteligência incorporada que até um estudante sem dinheiro pode pagar, e é um dos corpos oficialmente recomendados pelo LeRobot.

O braço é composto por dois braços: um braço Leader e um braço Follower. Cada braço tem 5 graus de liberdade mais 1 grau de liberdade da garra.

## Qual configuração de computador eu preciso

Um notebook Windows comum dá conta de tudo até o treinamento.

Um Mac comum dá conta de tudo.

Uma máquina Ubuntu com GPU NVIDIA dá conta de tudo.

Neste tutorial usamos uma [plataforma de GPU na nuvem](https://featurize.cn?s=d7ce99f842414bfcaea5662a97581bd1) para treinar os modelos, então o seu próprio computador não precisa de uma configuração topo de linha.

## O que é **aprendizado por imitação e VLA**?

Uma pessoa arrasta o robô para demonstrar e coletar um dataset. Esse dataset é então usado para treinar um algoritmo de aprendizado por imitação, que por fim é implantado no robô, permitindo que ele imite as ações humanas de forma autônoma e generalize para o ambiente real. Não é preciso teleoperação nem controle remoto.

Por exemplo, no vídeo acima, uma pessoa arrasta o braço robótico SO-ARM para pegar um lagostim, mergulhá-lo no tempero e soltá-lo no óleo quente, e o braço acaba executando essa ação sozinho. Mesmo com um lagostim novo, ele consegue reagir e concluir a ação a qualquer momento.

O aprendizado por imitação também tem um nome moderno e de ponta: VLA (modelo grande de Visão-Linguagem-Ação). Esse também é o campo de pesquisa em inteligência incorporada que se desenvolve mais rápido hoje, atrai o investimento mais quente, tem a competição China-EUA mais acirrada, desfruta do ecossistema de código aberto mais próspero, atrai intensa atenção da mídia e atrai incontáveis estudantes de mestrado e doutorado.

Os algoritmos que o LeRobot adapta principalmente são de aprendizado por imitação, como ACT, Diffusion Policy, SmolVLA, Pi0, Pi0.5, Wall-OSS e outros.

O aprendizado por imitação neste tutorial é exclusivamente VLA.
