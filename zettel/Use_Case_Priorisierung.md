---
id: 079ecea4-04cf-4960-89c3-e748f616b58a
title: "Use Case Priorisierung"
date: 2026-06-23
tags:
  - software_engineering
  - priorisierung
  - planung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Priorisierung]]

- **Kernkonzept:** Use Case Priorisierung ist ein systematischer Prozess, bei dem Use Cases nach ihrer Wichtigkeit und ihrem Einfluss auf die Systemarchitektur oder das Projektziel bewertet und eingestuft werden, um die Entwicklungsreihenfolge festzulegen.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die begrenzten Ressourcen eines Projekts effizient einzusetzen, indem kritische oder architekturbestimmende Use Cases frühzeitig identifiziert und umgesetzt werden. Es löst das Problem der unstrukturierten Entwicklung, reduziert Risiken durch Fokussierung auf zentrale Anforderungen und ermöglicht eine zielgerichtete Planung der Software-Entwicklung.
- **Abgrenzung & Grenzen:** Use Case Priorisierung sollte nicht genutzt werden, wenn alle Anforderungen gleich kritisch sind oder keine architektonischen Abhängigkeiten bestehen. Es unterscheidet sich von rein sequenziellen oder willkürlichen Entwicklungsansätzen, da es explizit die Bedeutung und Auswirkungen jedes Use Cases bewertet. Alternativen wie Backlog-Priorisierung in Scrum betrachten oft nur kurzfristige Ziele, während Use Case Priorisierung langfristige Architekturentscheidungen einbezieht.
- **Beispiel / Code:** ```java
// Beispiel für eine priorisierte Use-Case-Liste in einem Projektplan
public enum UseCasePriority {
    HIGH(1, "Architekturkritisch oder risikoreich"),
    MEDIUM(2, "Wichtig für Kernfunktionen"),
    LOW(3, "Erweiterungen oder optionale Features");
    
    private final int value;
    private final String description;
    
    UseCasePriority(int value, String description) {
        this.value = value;
        this.description = description;
    }
}

// Priorisierte Use Cases im System
List<UseCase> useCases = List.of(
    new UseCase("Mitglieder verwalten", UseCasePriority.HIGH),
    new UseCase("Rechnungen generieren", UseCasePriority.MEDIUM),
    new UseCase("Statistiken anzeigen", UseCasePriority.LOW)
);
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d
- **Vorgänger / Parent:** [[Use_Case]]
- **Folgezettel / Unterzettel:**
  - [[Prioritätsstufen]]
- **Querverweise:**
  - [[Use_Case]]
  - [[Projektplanung]]
