---
id: 666814e0-be31-4095-86da-6a922b5a1dd7
title: "High-Level Use Cases"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - übersicht
  - draft
source: "software_engineering_kapitel_07"
---

# [[High-Level Use Cases]]

- **Kernkonzept:** High-Level Use Cases sind grobe, übersichtliche Beschreibungen von Abläufen in einem Softwaresystem aus der Perspektive beteiligter Akteure. Sie fassen zentrale Funktionen zusammen, ohne auf technische Details einzugehen, und dienen als frühe Grundlage für die Anforderungsanalyse.
- **Nutzen & Zweck:** High-Level Use Cases ermöglichen ein schnelles Problemverständnis und eine strukturierte Erfassung von Anforderungen in frühen Projektphasen. Sie helfen, die Kernfunktionalitäten eines Systems zu identifizieren, Prioritäten zu setzen und eine gemeinsame Kommunikationsbasis zwischen Stakeholdern, Entwicklern und Designern zu schaffen, bevor detaillierte Spezifikationen erstellt werden.
- **Abgrenzung & Grenzen:** High-Level Use Cases sollten nicht genutzt werden, wenn detaillierte Abläufe, technische Implementierungsdetails oder komplexe Ausnahmefälle beschrieben werden müssen. Sie unterscheiden sich von erweiterten Use Cases durch ihre Kürze und Abstraktionsebene. Alternativen wie User Stories oder detaillierte Use-Case-Spezifikationen sind besser geeignet, wenn präzise Schritt-für-Schritt-Anleitungen oder technische Randbedingungen erforderlich sind.
- **Beispiel / Code:** ```java
// Beispiel: High-Level Use Case "Mitglieder verwalten"
UseCase MitgliederVerwalten {
    Name: "Mitglieder verwalten"
    Akteure: [Vereinsmanager, MailClient]
    Systemgrenze: MyClub
    Priorität: 1 (hoch)
    Beschreibung: "Der Vereinsmanager kann Mitglieder anlegen, bearbeiten oder löschen. 
                 Bei Änderungen der Abteilungszugehörigkeit werden betroffene Akteure per E-Mail informiert."
    Anforderungen: [F1.1, F1.2, F2.1]
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1
- **Vorgänger / Parent:** [[Use_Case_Analyse]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case]]
  - [[Anforderungsanalyse]]
