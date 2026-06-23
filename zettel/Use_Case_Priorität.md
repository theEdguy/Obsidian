---
id: b363e28b-ac7f-4e9f-88f7-6ce404fdcf29
title: "Use Case Priorität"
date: 2026-06-23
tags:
  - software_engineering
  - priorisierung
  - planung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Priorität]]

- **Kernkonzept:** Use Case Priorität ist ein Bewertungskriterium, das die Wichtigkeit und Dringlichkeit eines Use Cases im Softwareentwicklungsprozess festlegt. Sie hilft, zentrale und risikobehaftete Anwendungsfälle frühzeitig zu identifizieren und deren Umsetzung zu steuern.
- **Nutzen & Zweck:** Die Priorisierung von Use Cases löst das Problem der Ressourcenknappheit und unklarer Entwicklungsziele, indem sie eine strukturierte Entscheidungsgrundlage schafft. Sie ermöglicht es, kritische Systemfunktionen oder architekturrelevante Anwendungsfälle vorrangig zu behandeln, um Risiken zu minimieren und die Projektplanung zu optimieren. Ohne Priorisierung besteht die Gefahr, dass unwichtige oder nachgelagerte Funktionen vorrangig umgesetzt werden, was zu Verzögerungen oder Fehlentwicklungen führen kann.
- **Abgrenzung & Grenzen:** Use Case Priorität sollte nicht genutzt werden, wenn alle Anforderungen gleich wichtig sind oder keine strategische Reihenfolge der Umsetzung erforderlich ist, z. B. in sehr kleinen Projekten mit wenigen Anwendungsfällen. Sie unterscheidet sich von reinen Aufwandsschätzungen (wie Story Points in Agile), da sie nicht den Entwicklungsaufwand, sondern die strategische Bedeutung bewertet. Zudem ist sie kein Ersatz für detaillierte Risikoanalysen, sondern ergänzt diese durch eine priorisierte Umsetzungsreihenfolge. Bei unklaren oder sich häufig ändernden Anforderungen kann eine starre Priorisierung kontraproduktiv sein.
- **Beispiel / Code:** ```java
// Beispiel für eine priorisierte Use-Case-Liste in einem Projektmanagement-Tool
public enum Priority {
    HIGH(1, "Sehr wichtig: Architekturrelevant oder risikobehaftet"),
    MEDIUM(2, "Wichtig: Funktionalität mit mittlerer Priorität"),
    LOW(3, "Weniger wichtig: Nachgelagerte oder optionale Funktionen");
    
    private final int value;
    private final String description;
    
    Priority(int value, String description) {
        this.value = value;
        this.description = description;
    }
}

public class UseCase {
    private String name;
    private Priority priority;
    private String[] associatedRequirements;
    
    public UseCase(String name, Priority priority, String[] requirements) {
        this.name = name;
        this.priority = priority;
        this.associatedRequirements = requirements;
    }
    
    // Getter und weitere Methoden...
}

// Nutzung:
UseCase mitgliederVerwalten = new UseCase(
    "Mitglieder verwalten", 
    Priority.HIGH, 
    new String[]{"F1.1", "F1.2", "F2.1"}
);
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b4
- **Vorgänger / Parent:** [[Use_Case_Struktur]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Priorisierung]]
  - [[Use_Case]]
