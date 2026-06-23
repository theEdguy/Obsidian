---
id: 941699d8-2c4a-42d2-b48f-9813448a7b34
title: "Alternative"
date: 2026-06-23
tags:
  - software_engineering
  - uml-fragment
  - kontrollfluss
  - draft
source: "software_engineering_kapitel_13"
---

# [[Alternative]]

- **Kernkonzept:** Das UML-Fragment 'Alternative' (alt) beschreibt in Interaktionsdiagrammen, insbesondere Sequenzdiagrammen, alternative Ablaufpfade, die abhängig von Bedingungen ausgeführt werden. Es ermöglicht die Modellierung von Verzweigungen im Kontrollfluss, ähnlich einer if-else-Struktur in der Programmierung.
- **Nutzen & Zweck:** Das 'Alternative'-Fragment existiert, um komplexe Entscheidungslogik in dynamischen Systemabläufen abzubilden. Es löst das Problem, dass Interaktionsdiagramme ohne Verzweigungen nur lineare Abläufe darstellen könnten, was für reale Anwendungsfälle oft unzureichend ist. Durch die explizite Modellierung von Alternativen wird die Kommunikation zwischen Entwicklern und Stakeholdern verbessert, da unterschiedliche Szenarien visuell klar getrennt werden.
- **Abgrenzung & Grenzen:** Das 'Alternative'-Fragment sollte nicht genutzt werden, wenn der Kontrollfluss ausschließlich linear verläuft oder wenn die Bedingungen für die Verzweigung trivial sind. Es unterscheidet sich von anderen Fragmenten wie 'Option' (opt), das nur einen einzigen optionalen Pfad darstellt, oder 'Schleife' (loop), das Wiederholungen abbildet. 'Alternative' ist zudem ungeeignet für parallele Abläufe, die besser mit dem 'Parallel'-Fragment (par) modelliert werden. Bei zu vielen verschachtelten Alternativen kann das Diagramm unübersichtlich werden – hier sind kleinere, aufgeteilte Diagramme vorzuziehen.
- **Beispiel / Code:** ```java
// Beispiel für ein Sequenzdiagramm mit 'Alternative'-Fragment (pseudocode-ähnliche Notation)
participant Nutzer
participant System

Nutzer -> System: login(benutzername, passwort)
alt [Anmeldung erfolgreich]
    System -> Nutzer: zeigeDashboard()
else [Anmeldung fehlgeschlagen]
    System -> Nutzer: zeigeFehlermeldung("Ungültige Daten")
end
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1c1
- **Vorgänger / Parent:** [[Nachrichtenfragment]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
