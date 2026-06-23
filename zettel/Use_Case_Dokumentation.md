---
id: 66fdc091-436f-4531-ab8d-e3f40bc20a25
title: "Use Case Dokumentation"
date: 2026-06-23
tags:
  - software_engineering
  - dokumentation
  - use_case
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Dokumentation]]

- **Kernkonzept:** Use Case Dokumentation ist eine strukturierte Beschreibung von Anwendungsfällen, die die Interaktionen zwischen Akteuren und einem System aus Nutzerperspektive darlegt. Sie dient der systematischen Erfassung und Kommunikation von funktionalen und nicht-funktionalen Anforderungen.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Anforderungen an ein Softwaresystem klar, verständlich und nachvollziehbar zu erfassen. Es löst das Problem der unklaren oder unvollständigen Anforderungsdefinition, indem es Entwicklern, Designern und Stakeholdern eine gemeinsame Basis für die Architektur, Implementierung und Validierung bietet. Use Cases helfen, zentrale Systemfunktionen frühzeitig zu identifizieren und priorisieren, wodurch Risiken reduziert und die Projektstruktur verbessert werden.
- **Abgrenzung & Grenzen:** Use Case Dokumentation sollte nicht genutzt werden, wenn es um die detaillierte technische Umsetzung oder algorithmische Logik geht, da sie sich auf die Nutzerinteraktion und Systemfunktionen konzentriert. Alternativen wie User Stories (im agilen Kontext) sind weniger formal und eignen sich besser für iterative, flexible Entwicklungsprozesse. Zudem sind Use Cases ungeeignet, um zeitliche Abfolgen oder Workflows abzubilden, da sie keine Sequenzinformationen enthalten. Für technische Spezifikationen oder Datenmodellierung sind andere Methoden wie UML-Klassendiagramme oder ER-Diagramme besser geeignet.
- **Beispiel / Code:** ```java
// Beispiel für eine Use-Case-Beschreibung in strukturierter Form (kein Code, sondern Dokumentation)
UseCase {
    name: "Mitglieder verwalten",
    systemgrenze: "MyClub",
    akteure: ["Vereinsmanager", "Mail Client"],
    prioritaet: 1,
    vorbedingung: "MyClub ist installiert und der Vereinsmanager ist authentisiert.",
    referenzen: ["F1.1", "F1.2", "F2.1"],
    beschreibung: "Der Vereinsmanager kann Mitglieder anlegen, bearbeiten oder löschen. 
                  Bei Änderungen der Abteilungszugehörigkeit werden Mitglied und Abteilungsleiter per E-Mail informiert.",
    offenePunkte: ["Soll das Mitglied über jede Änderung per E-Mail informiert werden?"]
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2c1
- **Vorgänger / Parent:** [[Anforderungsdokumentation]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case]]
  - [[Anforderungsdokumentation]]
