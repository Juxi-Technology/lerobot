[English](../en/03-calibration.md) | [简体中文](../zh-hans/03-calibration.md) | [繁體中文](../zh-hant/03-calibration.md) | [Deutsch](../de/03-calibration.md) | [Español](../es/03-calibration.md) | [Français](../fr/03-calibration.md) | [Italiano](../it/03-calibration.md) | [日本語](../ja/03-calibration.md) | [한국어](../ko/03-calibration.md) | [Português (BR)](../pt-br/03-calibration.md) | Português (PT)

# 3 · Ligar e calibrar

> **Anterior:** [02 Instalar e executar](02-install.md)
> **Seguinte:** [04 Teleoperação](04-teleoperation.md)

A calibração regista o ponto zero e o curso de cada articulação. Faça-a uma vez por braço; repita-a depois de desmontar ou se o ficheiro de calibração se perder.

## Antes de começar

- Ambos os braços montados, com os IDs atribuídos aos servos.
- Ambos os braços ligados à corrente.
- Um cabo USB por braço, em **duas portas USB separadas** — um hub partilhado pode enumerá-los de forma pouco fiável.

### Linux: permissões da porta série

```bash
sudo usermod -aG dialout $USER
```

Depois **termine a sessão e volte a iniciá-la**. Sem isto, o LeLab encontra o braço, mas todas as leituras falham com um erro de permissão. O Windows e o macOS não precisam de nada.

## Qual braço é qual

| Braço | Nome no LeRobot | Designação no LeLab |
|---|---|---|
| O que move à mão | `so101_leader` | **teleop** |
| O que segue | `so101_follower` | **robot** |

Calibre primeiro o leader. Trocá-los é a razão habitual para um braço acabado de calibrar se comportar de forma estranha.

## O processo

Abra o separador **Calibration** e avance um braço de cada vez:

1. **Escolha o dispositivo** — leader (teleop) ou follower (robot).
2. **Escolha a porta série.** O LeLab lista os dispositivos série USB que deteta. Para os distinguir, desligue um braço e veja qual a entrada que desaparece. A escolha é memorizada.
3. **Escolha um perfil de calibração** — um existente ou um novo. O perfil contém as posições zero guardadas; se este braço já foi calibrado antes, reutilize o seu perfil.
4. **Siga os passos guiados.** O LeLab percorre cada articulação pela ordem; desloque a articulação até à posição pedida e confirme. Sem indicações no teclado.
5. **Repita para o outro braço** — com o seu próprio perfil e porta.

> Cada perfil pertence a um braço físico. Trocar os dois braços obriga a recalibrar.

## Câmaras

As câmaras são configuradas no mesmo separador. O nome de cada câmara (`front`, `wrist`, …) é a chave que a política vê, por isso use nomes que reconheça num registo de treino.

As câmaras podem ser montadas antes ou depois da calibração; a calibração não depende delas. Mantenha a associação estável — trocar qual câmara física se chama `wrist` entre a gravação e a inferência faz uma política treinada comportar-se de forma absurda.

### Rotação

Se uma câmara estiver montada ao contrário ou de lado, defina a sua **Rotation**: 0°, 90°, 180° ou 270° no sentido dos ponteiros do relógio. Uma câmara de punho ao contrário é 180°.

A rotação é guardada por câmara e aplicada à pré-visualização da configuração, à pré-visualização da teleoperação, aos fotogramas gravados e à inferência. Os perfis sem definição de rotação são tratados como 0°.

- **90° e 270° trocam as dimensões de saída.** Uma captura de 640 × 480 passa a 480 × 640.
- **As dimensões da imagem do checkpoint não revelam a orientação.** 0° e 180° produzem dimensões idênticas, mas imagens opostas. Antes da inferência, defina a rotação usada durante a gravação — ver [página 6](06-train-and-inference.md).

## O que é guardado

| Ficheiro | Conteúdo |
|---|---|
| `~/.cache/huggingface/lerobot/calibration/teleoperators/so101_leader/*.json` | Perfis do leader |
| `~/.cache/huggingface/lerobot/calibration/robots/so101_follower/*.json` | Perfis do follower |
| `~/.cache/huggingface/lerobot/ports/leader_port.txt` | Porta série do leader |
| `~/.cache/huggingface/lerobot/ports/follower_port.txt` | Porta série do follower |

Estes ficheiros ficam em `~/.cache/`, por isso as ferramentas de limpeza de cache podem eliminá-los. Se um braço calibrado voltar a pedir calibração, verifique aqui — ver [Resolução de problemas](07-troubleshooting.md).

---

> **Seguinte:** [04 Teleoperação](04-teleoperation.md)
