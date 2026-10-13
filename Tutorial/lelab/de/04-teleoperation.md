[English](../en/04-teleoperation.md) | [简体中文](../zh-hans/04-teleoperation.md) | [繁體中文](../zh-hant/04-teleoperation.md) | Deutsch | [Español](../es/04-teleoperation.md) | [Français](../fr/04-teleoperation.md) | [Italiano](../it/04-teleoperation.md) | [日本語](../ja/04-teleoperation.md) | [한국어](../ko/04-teleoperation.md) | [Português (BR)](../pt-br/04-teleoperation.md) | [Português (PT)](../pt-pt/04-teleoperation.md)

# 4 · Teleoperation

> **Zurück:** [03 Verbinden und kalibrieren](03-calibration.md)
> **Weiter:** [05 Ein Dataset aufzeichnen](05-record-dataset.md)

Sie bewegen den leader-Arm von Hand; der follower kopiert die Bewegung. So zeichnen Sie Demonstrationen auf, und es ist der schnellste Weg, die Kalibrierung zu bestätigen.

## Ausführen

1. Öffnen Sie den Tab **Teleoperation**.
2. Bestätigen Sie die Ports und das Kalibrierungsprofil — LeLab merkt sich diese aus der Kalibrierung.
3. Starten Sie die Teleoperation.
4. Bewegen Sie den leader-Arm.

Der Tab streamt die Gelenkpositionen, während er läuft. Drücken Sie Stopp, wenn Sie fertig sind.

**Stopp ist das, was den follower parkt.** Den Tab zu schließen oder den Prozess zu beenden lässt den Arm, wo er ist.

## Was zu prüfen ist

| Prüfung | Warum |
|---|---|
| Der follower folgt flüssig, ohne Verzögerung oder Zittern | Eine grobe Nachführung ergibt unbrauchbare Trainingsdaten |
| Der Bereich des follower entspricht dem des leader | Zu früh anhalten oder an einen Anschlag stoßen bedeutet, dass ein Gelenk falsch kalibriert ist — gehen Sie zurück zu [Seite 3](03-calibration.md) |
| Beide Arme bewegen sich in dieselbe Richtung | Ein invertierter follower bedeutet, dass ein Gelenk in die falsche Richtung kalibriert wurde |
| An den Extremen kollidiert nichts | Fahren Sie den gesamten Bereich ab, den Sie nutzen wollen |

Wenn die Bewegung falsch, aber nicht kaputt ist — Versatz, ein invertiertes Gelenk, zu kurzer Weg — kalibrieren Sie neu, statt zu kompensieren. Ein falsch kalibrierter Arm erzeugt ein Dataset, das die Policy das Falsche lehrt.

## Kameras

Wenn Kameras konfiguriert sind, zeigt die Teleoperations-Ansicht ihre Vorschauen.

- Handgelenkkamera: Zeigt sie den Greifer und was er gleich greifen soll?
- Feste Kamera: Zeigt sie den gesamten Arbeitsbereich?
- Ist eines der Bilder seitlich oder kopfüber? Korrigieren Sie die **Rotation** im [Kalibrierungs-Tab](03-calibration.md) vor der Aufzeichnung.

Frames, die während der Teleoperation aufgezeichnet werden, sind das Einzige, was die Policy je sieht.

---

> **Weiter:** [05 Ein Dataset aufzeichnen](05-record-dataset.md)
