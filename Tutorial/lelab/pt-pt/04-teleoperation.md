[English](../en/04-teleoperation.md) | [简体中文](../zh-hans/04-teleoperation.md) | [繁體中文](../zh-hant/04-teleoperation.md) | [Deutsch](../de/04-teleoperation.md) | [Español](../es/04-teleoperation.md) | [Français](../fr/04-teleoperation.md) | [Italiano](../it/04-teleoperation.md) | [日本語](../ja/04-teleoperation.md) | [한국어](../ko/04-teleoperation.md) | [Português (BR)](../pt-br/04-teleoperation.md) | Português (PT)

# 4 · Teleoperação

> **Anterior:** [03 Ligar e calibrar](03-calibration.md)
> **Seguinte:** [05 Gravar um conjunto de dados](05-record-dataset.md)

Move o braço leader à mão; o follower copia o movimento. É assim que grava demonstrações, e a forma mais rápida de confirmar a calibração.

## Como executar

1. Abra o separador **Teleoperation**.
2. Confirme as portas e o perfil de calibração — o LeLab memoriza-os desde a calibração.
3. Inicie a teleoperação.
4. Mova o braço leader.

O separador transmite as posições das articulações enquanto decorre. Carregue em parar quando terminar.

**É o parar que estaciona o follower.** Fechar o separador ou terminar o processo deixa o braço onde está.

## O que verificar

| Verificação | Porquê |
|---|---|
| O follower segue com suavidade, sem atraso nem tremores | Um seguimento irregular dá dados de treino inutilizáveis |
| O alcance do follower corresponde ao do leader | Ficar aquém ou bater num limite significa que uma articulação está mal calibrada — volte à [página 3](03-calibration.md) |
| Os dois braços movem-se no mesmo sentido | Um follower invertido significa que uma articulação foi calibrada no sentido errado |
| Nada colide nos extremos | Percorra todo o curso que pretende utilizar |

Se o movimento estiver errado mas não avariado — desviado, uma articulação invertida, curso insuficiente — recalibre em vez de compensar. Um braço mal calibrado produz um conjunto de dados que treina a política para fazer a coisa errada.

## Câmaras

Se tiver câmaras configuradas, a vista de teleoperação mostra as respetivas pré-visualizações.

- Câmara de punho: mostra a garra e o que ela está prestes a agarrar?
- Câmara fixa: mostra todo o espaço de trabalho?
- Alguma das imagens está de lado ou ao contrário? Corrija a **rotação** no [separador de calibração](03-calibration.md) antes de gravar.

Os fotogramas gravados durante a teleoperação são a única coisa que a política alguma vez vê.

---

> **Seguinte:** [05 Gravar um conjunto de dados](05-record-dataset.md)
