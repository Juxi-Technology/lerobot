[English](../en/04-teleoperation.md) | [简体中文](../zh-hans/04-teleoperation.md) | [繁體中文](../zh-hant/04-teleoperation.md) | [Deutsch](../de/04-teleoperation.md) | Español | [Français](../fr/04-teleoperation.md) | [Italiano](../it/04-teleoperation.md) | [日本語](../ja/04-teleoperation.md) | [한국어](../ko/04-teleoperation.md) | [Português (BR)](../pt-br/04-teleoperation.md) | [Português (PT)](../pt-pt/04-teleoperation.md)

# 4 · Teleoperación

> **Anterior:** [03 Conectar y calibrar](03-calibration.md)
> **Siguiente:** [05 Grabar un dataset](05-record-dataset.md)

Mueves el brazo leader a mano; el follower copia el movimiento. Así es como grabas demostraciones, y la forma más rápida de confirmar la calibración.

## Ejecutarlo

1. Abre la pestaña **Teleoperation**.
2. Confirma los puertos y el perfil de calibración — LeLab los recuerda de la calibración.
3. Inicia la teleoperación.
4. Mueve el brazo leader.

La pestaña transmite las posiciones articulares mientras se ejecuta. Pulsa detener cuando termines.

**Detener es lo que aparca el follower.** Cerrar la pestaña o matar el proceso deja el brazo donde está.

## Qué comprobar

| Comprobación | Por qué |
|---|---|
| El follower sigue con suavidad, sin retraso ni vibración | Un seguimiento tosco se convierte en datos de entrenamiento inutilizables |
| El rango del follower coincide con el del leader | Quedarse corto o tocar un límite significa que una articulación está mal calibrada — vuelve a la [página 3](03-calibration.md) |
| Ambos brazos se mueven en la misma dirección | Un follower invertido significa que una articulación se calibró en la dirección equivocada |
| Nada choca en los extremos | Recorre todo el rango que piensas usar |

Si el movimiento es incorrecto pero no está roto — desfase, una articulación invertida, recorrido corto — recalibra en lugar de compensar. Un brazo mal calibrado produce un dataset que entrena a la política para hacer lo incorrecto.

## Cámaras

Si hay cámaras configuradas, la vista de teleoperación muestra sus vistas previas.

- Cámara de muñeca: ¿muestra la pinza y lo que está a punto de agarrar?
- Cámara fija: ¿muestra todo el espacio de trabajo?
- ¿Alguna imagen está de lado o boca abajo? Corrige la **rotation** en la [pestaña de calibración](03-calibration.md) antes de grabar.

Los fotogramas grabados durante la teleoperación son lo único que la política llega a ver.

---

> **Siguiente:** [05 Grabar un dataset](05-record-dataset.md)
