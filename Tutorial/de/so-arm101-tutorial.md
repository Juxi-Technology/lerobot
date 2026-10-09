[English](../en/so-arm101-tutorial.md) | [简体中文](../zh-hans/so-arm101-tutorial.md) | [繁體中文](../zh-hant/so-arm101-tutorial.md) | Deutsch | [Español](../es/so-arm101-tutorial.md) | [Français](../fr/so-arm101-tutorial.md) | [Italiano](../it/so-arm101-tutorial.md) | [日本語](../ja/so-arm101-tutorial.md) | [한국어](../ko/so-arm101-tutorial.md) | [Português (BR)](../pt-br/so-arm101-tutorial.md) | [Português (PT)](../pt-pt/so-arm101-tutorial.md)

<title>SO-ARM101 Roboterarm-Tutorial</title>

# Produktübersicht

Der SO-ARM101 ist ein **kostengünstiger, vollständig quelloffener Roboterarm mit 6 Freiheitsgraden**, entwickelt vom LeRobot-Team bei Hugging Face für den Einstieg in die Ausbildung, die Forschungsvalidierung und das leichte industrielle Prototyping. Mit hoher Flexibilität und einem vollständigen Open-Source-Ökosystem senkt er die Hürden für die Anwendung von verkörperter Intelligenz und Robotertechnik.

### 1. Hardware-Design: leistungsstark, modular, einfach zu montieren und anzupassen

- **Strukturmaterial**: Die Kernstruktur kombiniert 3D-gedruckte Teile mit verstärkten tragenden Komponenten; optimierte Kabelführung und Gelenkkonstruktion vermeiden Bewegungskonflikte und bringen geringes Gewicht und Haltbarkeit in Einklang; Ersatz- oder Erweiterungsteile können Nutzer selbst drucken.
- **Antriebskonfiguration**: Der Follower-Arm trägt **6 magnetische Encoder-Servos mit 12 V und 30 kg Drehmoment**, kombiniert mit 360°-Magnetencoder-Rückmeldung und einem PID-Regelalgorithmus – seidige, ruckelfreie Bewegung, hohe Wiederholgenauigkeit, starke Leistung und präzise Bewegung.
- **Visionsystem**: standardmäßig mit einem **intelligenten Dual-Kamera-Visionssystem** ausgestattet; die Endeffektor-Kamera erfasst Nahaufnahmen des Greifvorgangs, während die globale Kamera die Arbeitsumgebung abdeckt. Die Fusion der Daten beider Kameras erzeugt ein 3D-Modell und liefert umfangreiche Datenunterstützung für das Imitationslernen.
- **Steuerungsverbindung**: ausgestattet mit einem Servo-Treiberboard, das über eine USB-C-Schnittstelle direkt an einen PC oder Raspberry Pi angeschlossen wird – Plug-and-Play, was den Hardware-Anschluss vereinfacht und den schnellen Aufbau der Steuerungsumgebung ermöglicht.

### 2. Software-Ökosystem: tiefe Integration mit LeRobot, KI-Entwicklung ohne Hürden

- **Kompatibilität mit dem Kern-Framework**: tiefgehend an Hugging Faces **quelloffenes LeRobot-Framework für maschinelles Lernen bei Robotern** angepasst, auf PyTorch basierend, mit integrierten vorab trainierten Modellen, Datensätzen für verschiedene Szenarien und einer Simulationsumgebung sowie kompatibel mit bekannten Open-Source-Datensätzen wie Stanford ALOHA.
- **Kommunikation mit geringer Latenz**: nutzt die **verteilte Datenfluss-Engine DORA** für latenzarme Interaktion zwischen Hardware und Algorithmen; Python läuft 17-mal schneller als ROS2, und Hot-Code-Reloading wird unterstützt, sodass Sie Policies in Echtzeit anpassen können, ohne neu zu starten.
- **Full-Stack-Open-Source**: die 3D-Druckdateien der Hardware, der Steuerungscode der Software, die KI-Trainingsskripte und der gesamte Tutorialsatz sind **vollständig quelloffen**; Nutzer können sie frei verändern und weiterentwickeln, um schnell individuelle Funktionserweiterungen umzusetzen.

### 3. Zentrale Anwendungsszenarien: passend vom Einstieg bis zum Deployment

1. **Einstieg in die Robotik-Ausbildung**: bietet ein End-to-End-Tutorial von der Armmontage und grundlegenden Programmierung bis zum Deployment von KI-Policies, mit visueller Bedienoberfläche und Beispielcode, sodass Anfänger schnell Robotersteuerung und KI-Anwendung beherrschen.
2. **Validierung von Forschungsalgorithmen**: ausgerichtet auf Forschung zu **Imitationslernen und bestärkendem Lernen**, mit Unterstützung für die Aufzeichnung menschlicher Bediendaten per VR zum Trainieren des Roboters; ein typischer Fall: Auf Basis von 50 Clips mit je 15 Sekunden Bedienvideo genügen 2 Stunden Training, um Aufgaben wie Wäschefalten, Schlüssel-Einstecken und Materialsortieren zu erlernen.
3. **Leichtes industrielles Prototyping**: kostengünstige Validierung von Automatisierungslösungen für Szenarien wie **Materialtransport, Präzisionsmontage und Teilesortierung**; liefert die Kernfunktionen eines industrietauglichen Roboterarms zum Preis der Tausende-Yuan-Klasse für schnelle Prototypenvalidierung.

### 4. Produktvorteile

- **Extremes Preis-Leistungs-Verhältnis**: Die Basisversion beginnt bei etwa 100 $, und das Open-Source-Design senkt Beschaffungs- und Weiterentwicklungskosten, was ihn für den Serieneinsatz durch Einzelpersonen, Labore und kleine bis mittlere Unternehmen geeignet macht.
- **Open Source über die gesamte Kette**: Hardware, Software und Tutorials sind vollständig offen, ohne technische Hürden, und unterstützen freie Anpassung und Funktionserweiterung, um viele Szenarien schnell abzudecken.
- **KI-Entwicklung freundlich**: gestützt auf das LeRobot-Ökosystem ruft er vorab trainierte Modelle und Datensätze mit einem Klick ab, vereinfacht den gesamten Ablauf von der Datenerfassung und dem Policy-Training bis zum Deployment und beschleunigt die Einführung von Algorithmen der verkörperten Intelligenz.

### 5. Produktspezifikationen

| **Spezifikation** | **Details** |
|-|-|
| Freiheitsgrade | 6 Achsen (Schulterdrehung / -neigung, Ellbogenbeugung, Handgelenkbeugung / -drehung, Greifer öffnen/schließen) |
| Strukturmaterial | 3D-gedruckte Teile (PLA+) |
| Antriebsmotoren | 12 \* Feetech STS3215-Servomotoren (12-V-Versorgung)  <br/>Follower-Arm STS3215-C018 Übersetzungsverhältnis: 1/345  <br/>Leader-Arm STS3215-C001 Übersetzungsverhältnis: 1/345 (Schulter), STS3215-C044 1/191 (Ellbogen), STS3215-C046 1/147 (Handgelenk) |
| Nutzlast | Maximale Endeffektor-Nutzlast 200 g (Greifer geschlossen) |
| Wiederholgenauigkeit | ±1,5 mm (abhängig von Kalibrierung und Motor-Spiel) |
| Arbeitsradius | Maximale Endeffektor-Reichweite 350 mm |
| Stromversorgung | Leader: 5 V 6 A Netzteil; Follower: 12 V 5 A Netzteil (für hohe Drehmomentanforderungen) |
| Kommunikationsschnittstelle | USB-C-Direktverbindung zum PC (Übertragung von Steuerbefehlen) |
| Visionsystem | Kamera (1080P@30FPS, FOV86° verzerrungsfrei, oder Festbrennweite 1080P@60FPS FOV100°) |
| Greifertyp | PLA+-Greifer, TPU-Greifer, zweifingeriger Parallelgreifer unterstützt, Öffnungsbereich 0-50 mm, maximale Greifkraft 5 N |
| Steuerungsframework | Python-basierte LeRobot-Bibliothek mit einer Motorsteuerungs-API (lerobot.control) |
| Vorab trainierte Modelle | Unterstützt Imitationslern-Algorithmen wie ACT (Action Chunking Transformer) und Diffusion Policy |
| Leichtgewichtiges Modell | SmolVLA-Vision-Language-Action-Modell (450 Mio. Parameter): ・Echtzeit-CPU-Inferenz (läuft auf MacBook) ・30 % schnellere asynchrone Antwort ・Nur 64 visuelle Tokens pro Frame ・Zustandsvisualisierung: Echtzeitüberwachung mit der rerun-Bibliothek |
| Gesamtgewicht | ≈1,2 kg (einschließlich Motoren und Kabel) |
| Montierte Abmessungen | Basisdurchmesser 120 mm, Höhe (voll ausgefahren) 650 mm |
| Betriebstemperatur | 0℃–40℃ (Servomotor-Grenzwert) |
| Geräuschpegel | <45 dB (Leerlaufbetrieb) |
| Anfänger-Tutorial | Ja |
| Offizielles GITHUB | Ja |

![Das Bild zeigt Maßzeichnungen der Leader- und Follower-Arme des Roboterarms SO-ARM101 zusammen mit Produktname, Material, Abmessungen und weiteren Informationen. Die Maßzeichnungen beschriften die Größe jedes Teils, zum Beispiel ist der Leader-Arm 525 mm und der Follower-Arm 532 mm lang. Das Produktmaterial ist topologisch optimiertes PLA+, und die Produktabmessungen betragen 111x239x525 mm (Leader) und 111x173x532 mm (Follower). Dieses Bild entspricht dem Abschnitt Produktspezifikationen des Dokuments und veranschaulicht die Abmessungsspezifikationen des Arms.](../en/images/d01-01.png)

| **Element / Paketname** | **Funktion / Beschreibung** |
|-|-|
| LeRobot-Bibliothek | Version: ≥0.1.0 Kern-Steuerungsframework: • Python-API (lerobot.control) ・Echtzeit-Bewegungsplanung ・Verarbeitung von Sensordatenströmen |
| PyTorch | Version: ≥2.0 Deep-Learning-Inferenz-Engine (unterstützt Modelle wie SmolVLA) |
| Transformers | Version: ≥4.40.0 Hugging-Face-Modellbibliothek (lädt vorab trainierte ACT/Diffusion Policy) |
| rerun | Version: ≥0.16.0 Werkzeug zur Echtzeit-Visualisierung des Roboterzustands (3D-Rendering von Gelenkwinkel / Trajektorie) |
| ROS 2 | Version: Humble/Foxy Optional: ROS2-Treiberschnittstelle (Paket soarm100_ros) |
| ACT | Action Chunking Transformer, Vorhersage langer Aktionssequenzen (z. B. kontinuierliche Greifaufgaben) |
| Diffusion Policy | Diffusions-Policy, robuste Regelung in hochdimensionalen Aktionsräumen (störungsresistente Manipulation) |
| SmolVLA | Vision-Language-Action-Modell, multimodale Instruktionsausführung (z. B. „greif den roten Block“) ・450 Mio. Parameter, läuft auf CPU/GPU |

| **Funktionskategorie** | **Funktionsbeschreibung** |
|-|-|
| Gelenkregelung | ・Unabhängige Winkel- / Geschwindigkeitsregelung für 6 Achsen (±180°-Bereich) ・Weiche Gelenkbegrenzung (Soft-Limit) ・Echtzeit-Rückmeldung von Motortemperatur / -spannung |
| Steuerung im kartesischen Raum | ・Positionierung des Endeffektors in XYZ-Koordinaten (Genauigkeit ±1,5 mm) ・Euler-Winkel-Ausrichtung (Roll/Pitch/Yaw) |
| Greiferbedienung | ・Stufenlose Öffnungseinstellung von 0-50 mm ・Dynamische Anpassung der Greifkraft (0,1-5 N) ・An die Objektdicke angepasstes Greifen |
| Leader/Follower-Modus | ・Manuelles Anlernen am Leader-Arm → Echtzeit-Nachahmung am Follower-Arm ・Aufzeichnung / Wiedergabe der Aktionsdaten |

| **Funktionskategorie** | **Funktionsbeschreibung** |
|-|-|
| Imitationslernen | ・Aufzeichnung menschlicher Demonstrationsdaten → Training von ACT/Diffusion-Policy-Modellen ・Unterstützung der Übertragung von Multi-Task-Policies (z. B. Bausteine stapeln → Objekte sortieren) |
| Multimodale Interaktion | ・Das SmolVLA-Modell interpretiert natürlichsprachliche Anweisungen (z. B. „greif den blauen Block“) ・End-to-End-Vision-Action-Ausführung |
| Schnittstelle für bestärkendes Lernen | ・Gymnasium-kompatible Umgebung ・Benutzerdefinierte Belohnungsfunktionen (z. B. Aufgabenabschlusszeit / Energieoptimierung) |
| Kalibrierungssystem | ・Nullpunkt-Kalibrierung von Leader/Follower ・Hand-Auge-Kalibrierung von Kamera und Arm ・Automatische Gelenk-Drehmomentkompensation |
| Verwaltung von Datenströmen | ・Aufzeichnung / Wiedergabe von Datensätzen im .h5-Format ・Cloud-Synchronisierung mit dem Hugging Face Hub ・Zeitstempel-Abgleich der Sensordaten |
| Echtzeitüberwachung | ・rerun-Visualisierung von Gelenkwinkeln / Endeffektor-Trajektorie ・Alarme bei Motoranomalien (Überhitzung / Blockierung) ・Diagnose der Kommunikationslatenz |
| ROS-2-Integration | ・Gelenkzustände veröffentlichen (/joint_states) ・Steuerbefehle abonnieren (/arm_controller) ・Übertragung von Punktwolkenströmen (/depth_points) |
| Plattformübergreifendes Deployment | • Linux/Windows/macOS (Python-API) ・Docker-Containerisierung ・Web-Fernsteuerung (FastAPI-Schnittstelle) |
