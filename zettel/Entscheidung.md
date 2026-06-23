---
id: 3b1dc0ba-50bf-462f-942f-58d2c14ae043
title: "Entscheidung"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_08"
---

# [[Entscheidung]]

- **Kernkonzept:** Eine Entscheidung in UML-Aktivitätsdiagrammen ist ein Kontrollknoten, der den Fluss basierend auf Bedingungen in alternative Pfade verzweigt. Sie ermöglicht die Modellierung von bedingten Abläufen und logischen Verzweigungen innerhalb eines Prozesses.
- **Nutzen & Zweck:** Das Konzept der Entscheidung löst das Problem, alternative Abläufe oder Bedingungen in einem Prozess darzustellen, ohne den Fluss unübersichtlich zu gestalten. Es ermöglicht die klare Trennung von Verzweigungen und die strukturierte Abbildung von Logik, z. B. in Use-Case-Szenarien oder Workflows, um komplexe Entscheidungsbäume nachvollziehbar zu modellieren.
- **Abgrenzung & Grenzen:** Entscheidungen sollten nicht genutzt werden, wenn der Ablauf linear und ohne Verzweigungen ist, da sie dann unnötige Komplexität einführen. Alternativ können einfache Bedingungen auch direkt in Textform oder durch Zustandsdiagramme dargestellt werden, falls die Logik zu trivial für eine grafische Modellierung ist. Im Gegensatz zu Splits/Joins, die parallele Abläufe abbilden, modellieren Entscheidungen exklusive Alternativen.
- **Beispiel / Code:** ```java
// Pseudocode zur Veranschaulichung einer Entscheidung in einem Aktivitätsdiagramm
if (mitgliedschaftGueltig) {
    mitgliedDatenAktualisieren();
} else {
    mitgliedschaftVerlaengern();
}
```

// UML-Aktivitätsdiagramm-Notation (textuell):
// [bedingung1] --> (Aktion1)
// [bedingung2] --> (Aktion2)
// Die Bedingungen werden in eckigen Klammern an die ausgehenden Kanten der Entscheidung angehängt.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a2
- **Vorgänger / Parent:** [[Aktivitätsdiagramm_Bausteine]]
- **Folgezettel / Unterzettel:**
  - [[Merge]]
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
