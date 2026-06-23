---
id: 2f3e0d8b-ffce-4b64-a867-0861b4bead87
title: "Scrum-Artefakte"
date: 2026-06-23
tags:
  - software_engineering
  - artefakt
  - agile
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Scrum-Artefakte]]

- **Kernkonzept:** Scrum-Artefakte sind zentrale [[Arbeitsergebnis|Arbeitsergebnisse]] im [[Scrum|Scrum-Framework]], die Transparenz über den [[Projektfortschritt]] und die Planung schaffen. Dazu zählen [[Product_Backlog]], [[Sprint_Backlog]] und [[Increment]], die jeweils spezifische Informationen für das [[agile_Entwicklungsteam|agile Team]] bereitstellen und die [[Selbstorganisation]] sowie [[Anpassungsfähigkeit]] fördern.
- **Nutzen & Zweck:** Scrum-Artefakte lösen das Problem mangelnder Transparenz und Nachverfolgbarkeit in [[agile_Entwicklung|agilen Projekten]]. Sie ermöglichen eine klare Kommunikation zwischen [[Entwicklungsteam|Team]], [[Product_Owner]] und [[Stakeholder|Stakeholdern]], indem sie den aktuellen Stand der Arbeit, Prioritäten und [[Projektfortschritt|Fortschritt]] dokumentieren. Dadurch wird die [[Selbstorganisation]] des Teams gefördert, die Planung und Umsetzung unterstützt sowie kontinuierliche Verbesserung durch Sichtbarmachung von Abhängigkeiten und Prioritäten ermöglicht. Die Artefakte dienen als Grundlage für [[Retrospektive|Retrospektiven]] und [[Sprint_Review|Sprint-Reviews]], um den [[Prozess]] iterativ zu optimieren.
- **Abgrenzung & Grenzen:** Scrum-Artefakte sollten nicht in stark regulierten oder dokumentationsintensiven Umgebungen genutzt werden, in denen detaillierte [[Spezifikation|Spezifikationen]] vorab erforderlich sind, da ihre Flexibilität und iterative Natur dort zu Unsicherheit führen können. Im Gegensatz zu klassischen [[Projektmanagement]]-Artefakten wie [[Lastenheft|Lastenheften]] oder [[Gantt-Diagramm|Gantt-Charts]] bieten sie weniger statische Vorab-Planung und sind nicht für langfristige Vorhersagen geeignet. Zudem eignen sie sich nicht für Projekte mit festen, unveränderlichen Anforderungen, da sie auf iterative [[Anpassung]] ausgelegt sind. Scrum-Artefakte ersetzen keine technische Dokumentation oder [[Softwarearchitektur|Architekturpläne]], sondern ergänzen diese, indem sie den Fokus auf aktuelle Prioritäten und [[Implementierung]] legen.
- **Beispiel / Code:** ```java
// Beispiel für ein Product Backlog-Item (PBI) als User Story mit erweiterten Attributen
public class ProductBacklogItem {
    private String id;
    private String title; // Kurze Zusammenfassung der User Story
    private String description; // "Als [Rolle] möchte ich [Funktion], um [Nutzen] zu erreichen."
    private int priority; // Priorisierung nach Business Value
    private String acceptanceCriteria; // Akzeptanzkriterien für die Umsetzung
    private String status; // z. B. "To Do", "In Progress", "Done"
    private List<String> dependencies; // Abhängigkeiten zu anderen PBIs
    private Estimation estimation; // Aufwandsschätzung (z. B. Story Points)

    public ProductBacklogItem(String id, String title, String description, int priority) {
        this.id = id;
        this.title = title;
        this.description = description;
        this.priority = priority;
        this.status = "To Do";
        this.dependencies = new ArrayList<>();
    }

    // Getter und Setter
    public void setAcceptanceCriteria(String criteria) {
        this.acceptanceCriteria = criteria;
    }

    public void addDependency(String pbiId) {
        this.dependencies.add(pbiId);
    }

    public void setEstimation(Estimation estimation) {
        this.estimation = estimation;
    }
}

// Beispiel für eine Aufwandsschätzung (Story Points oder Zeit)
public enum Estimation {
    ONE, TWO, THREE, FIVE, EIGHT, THIRTEEN, TWENTY_ONE
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9c
- **Vorgänger / Parent:** [[Scrum]]
- **Folgezettel / Unterzettel:**
  - [[Product_Backlog]]
  - [[Sprint_Backlog]]
  - [[Increment]]
- **Querverweise:**
  - [[Scrum]]
