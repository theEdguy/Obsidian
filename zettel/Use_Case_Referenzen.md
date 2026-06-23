---
id: 68fe30e6-9b34-4d58-bfc4-8e93ecccac28
title: "Use Case Referenzen"
date: 2026-06-23
tags:
  - software_engineering
  - referenzen
  - anforderungen
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Referenzen]]

- **Kernkonzept:** Use Case Referenzen sind Verweise innerhalb eines Use Cases auf spezifische funktionale oder nicht-funktionale Anforderungen, die durch den Use Case erfüllt werden. Sie dienen der systematischen Zuordnung und Nachverfolgbarkeit von Anforderungen im Entwicklungsprozess.
- **Nutzen & Zweck:** Das Konzept der Use Case Referenzen löst das Problem der mangelnden Transparenz und Nachvollziehbarkeit zwischen Anforderungen und deren Umsetzung. Es ermöglicht Entwicklern, Testern und Stakeholdern, klar zu erkennen, welche Anforderungen durch welche Use Cases abgedeckt werden. Dadurch wird die Konsistenz zwischen Anforderungsdokumentation und Systemdesign sichergestellt und die Risiken von Lücken oder Redundanzen minimiert.
- **Abgrenzung & Grenzen:** Use Case Referenzen sollten nicht genutzt werden, wenn Anforderungen nicht klar definiert oder stark dynamisch sind, da dies zu ständigen Anpassungen führt. Alternativ können informelle Verweise oder Kommentare in frühen Projektphasen sinnvoller sein. Im Gegensatz zu reinen textuellen Beschreibungen bieten Referenzen jedoch eine strukturierte und verknüpfbare Methode, die besonders in komplexen Projekten mit vielen Anforderungen vorteilhaft ist. Sie ersetzen keine detaillierte Anforderungsanalyse, sondern ergänzen diese.
- **Beispiel / Code:** ```java
// Beispiel für einen Use Case mit Referenzen auf Anforderungen
UseCase mitgliederVerwalten = new UseCase(
    "Mitglieder verwalten",
    "MyClub",
    List.of("Vereinsmanager", "Mail Client"),
    1,
    List.of("F1.1", "F1.2", "F2.1"), // Referenzen auf Anforderungen
    "Der Vereinsmanager kann Mitgliederdaten bearbeiten, neue Mitglieder anlegen oder Austritte verwalten."
);
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b7
- **Vorgänger / Parent:** [[Use_Case_Struktur]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case]]
  - [[Anforderungsmanagement]]
