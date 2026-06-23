---
id: 05be4bc1-ed0d-41e8-bd9f-deb71b378924
title: "Kategorisierung"
date: 2026-06-23
tags:
  - software_engineering
  - kategorisierung
  - anforderungen
  - draft
source: "software_engineering_kapitel_07"
---

# [[Kategorisierung]]

- **Kernkonzept:** Kategorisierung im Kontext von Use Cases bezeichnet die systematische Einordnung und Priorisierung von Anforderungen und Use Cases nach ihrer Wichtigkeit und ihrem Einfluss auf die Systemarchitektur. Dies erfolgt typischerweise durch Bewertungskriterien wie 'sehr wichtig', 'wichtig' oder 'weniger wichtig'.
- **Nutzen & Zweck:** Die Kategorisierung löst das Problem der Komplexitätsbewältigung in der Softwareentwicklung, indem sie eine strukturierte Übersicht über Anforderungen schafft. Sie ermöglicht es, zentrale und risikobehaftete Use Cases frühzeitig zu identifizieren und deren Umsetzung zu priorisieren. Dadurch wird sichergestellt, dass die Architektur des Systems stabil bleibt und kritische Funktionalitäten rechtzeitig entwickelt werden. Zudem unterstützt sie die Ressourcenplanung und Risikominimierung im Entwicklungsprozess.
- **Abgrenzung & Grenzen:** Kategorisierung sollte nicht genutzt werden, wenn Anforderungen noch unklar oder zu vage formuliert sind, da dies zu falschen Priorisierungen führen kann. Sie unterscheidet sich von reinen Auflistungen von Anforderungen, da sie nicht nur eine Sammlung, sondern eine bewertende Einordnung vornimmt. Alternativen wie detaillierte Anforderungsdokumentationen ohne Priorisierung bieten keine strukturierte Entscheidungsgrundlage für die Entwicklung. Zudem ist Kategorisierung kein Ersatz für detaillierte Use-Case-Beschreibungen, sondern dient als vorbereitender Schritt.
- **Beispiel / Code:** ```java
// Beispiel für eine priorisierte Use-Case-Liste in einem Softwareprojekt
public enum Priority {
    HIGH,    // Sehr wichtig (1)
    MEDIUM,  // Wichtig (2)
    LOW      // Weniger wichtig (3)
}

public class UseCase {
    private String name;
    private Priority priority;
    private List<String> requirements;
    
    public UseCase(String name, Priority priority, List<String> requirements) {
        this.name = name;
        this.priority = priority;
        this.requirements = requirements;
    }
    
    // Getter und weitere Methoden...
}

// Anwendung:
List<UseCase> useCases = new ArrayList<>();
useCases.add(new UseCase("Mitglieder verwalten", Priority.HIGH, List.of("F1.1", "F1.2")));
useCases.add(new UseCase("Statistiken generieren", Priority.MEDIUM, List.of("F3.1")));
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2b2
- **Vorgänger / Parent:** [[Anforderungsklassifikation]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Anforderungsklassifikation]]
