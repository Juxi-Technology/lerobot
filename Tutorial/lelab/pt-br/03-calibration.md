[English](../en/03-calibration.md) | [简体中文](../zh-hans/03-calibration.md) | [繁體中文](../zh-hant/03-calibration.md) | [Deutsch](../de/03-calibration.md) | [Español](../es/03-calibration.md) | [Français](../fr/03-calibration.md) | [Italiano](../it/03-calibration.md) | [日本語](../ja/03-calibration.md) | [한국어](../ko/03-calibration.md) | Português (BR) | [Português (PT)](../pt-pt/03-calibration.md)

# 3 · Conectar e calibrar

> **Anterior:** [02 Instalar e executar](02-install.md)
> **Próximo:** [04 Teleoperação](04-teleoperation.md)

A calibração registra o ponto zero e a faixa de curso de cada junta. Faça isso uma vez por braço; refaça após desmontagem ou se o arquivo de calibração for perdido.

## Antes de começar

- Os dois braços montados, com os servos configurados com seus IDs.
- Os dois braços ligados.
- Um cabo USB por braço, em **duas portas USB separadas** — um hub compartilhado às vezes os enumera de forma instável.

### Linux: permissões de porta serial

```bash
sudo usermod -aG dialout $USER
```

Depois **saia da sessão e entre de novo**. Sem isso, o LeLab encontra o braço, mas toda leitura falha com erro de permissão. O Windows e o macOS não precisam de nada.

## Qual braço é qual

| Braço | Nome no LeRobot | O LeLab chama de |
|---|---|---|
| O que você move com a mão | `so101_leader` | **teleop** |
| O que acompanha | `so101_follower` | **robot** |

Calibre o leader primeiro. Trocar os dois é o motivo mais comum de um braço recém-calibrado se comportar de forma estranha.

## O fluxo

Abra a aba **Calibration** e faça um braço de cada vez:

1. **Escolha o dispositivo** — leader (teleop) ou follower (robot).
2. **Escolha a porta serial.** O LeLab lista os dispositivos seriais USB que enxerga. Para diferenciá-los, desconecte um braço e veja qual entrada desaparece. A escolha fica salva.
3. **Escolha um perfil de calibração** — um existente, ou um novo. O perfil guarda as posições zero salvas; se este braço já foi calibrado antes, reutilize seu perfil.
4. **Siga os passos guiados.** O LeLab percorre cada junta em ordem; mova a junta até a posição pedida e confirme. Sem prompts de teclado.
5. **Repita para o outro braço** — com seu próprio perfil e porta.

> Cada perfil pertence a um braço físico. Trocar os dois braços significa recalibrar.

## Câmeras

As câmeras são configuradas na mesma aba. O nome de cada câmera (`front`, `wrist`, …) é a chave que a policy vê, então use nomes que você reconheça em um log de treinamento.

As câmeras podem ser montadas antes ou depois da calibração; a calibração não depende delas. Mantenha a associação estável — trocar qual câmera física se chama `wrist` entre a gravação e a inferência faz uma policy treinada se comportar de forma sem sentido.

### Rotação

Se uma câmera estiver montada de cabeça para baixo ou de lado, defina sua **Rotation**: 0°, 90°, 180° ou 270° no sentido horário. Uma câmera de pulso de cabeça para baixo é 180°.

A rotação é salva por câmera e aplicada à prévia de configuração, à prévia de teleoperação, aos quadros gravados e à inferência. Perfis sem configuração de rotação são tratados como 0°.

- **90° e 270° trocam as dimensões de saída.** Uma captura de 640 × 480 se torna 480 × 640.
- **As dimensões da imagem do checkpoint não revelam a orientação.** 0° e 180° produzem dimensões idênticas, mas imagens opostas. Antes da inferência, defina a rotação usada durante a gravação — veja a [página 6](06-train-and-inference.md).

## O que é salvo

| Arquivo | Conteúdo |
|---|---|
| `~/.cache/huggingface/lerobot/calibration/teleoperators/so101_leader/*.json` | Perfis do leader |
| `~/.cache/huggingface/lerobot/calibration/robots/so101_follower/*.json` | Perfis do follower |
| `~/.cache/huggingface/lerobot/ports/leader_port.txt` | Porta serial do leader |
| `~/.cache/huggingface/lerobot/ports/follower_port.txt` | Porta serial do follower |

Eles ficam em `~/.cache/`, então ferramentas de limpeza de cache podem apagá-los. Se um braço calibrado pedir para ser calibrado de novo, verifique aqui — veja [Solução de problemas](07-troubleshooting.md).

---

> **Próximo:** [04 Teleoperação](04-teleoperation.md)
