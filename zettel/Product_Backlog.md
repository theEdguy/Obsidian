---
id: c3ff463d-fcaf-4675-96b8-d4332bf21370
title: "Product_Backlog"
date: 2026-06-23
tags:
  - software_engineering
  - agile_methoden
  - requirements_engineering
  - product_backlog
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Product_Backlog]]

- **Kernkonzept:** Das [[Product_Backlog]] ist eine priorisierte, dynamische Liste aller bekannten [[Anforderung|Anforderungen]], [[Feature|Features]], Verbesserungen und Fehlerbehebungen in [[Scrum]]. Es wird kontinuierlich gepflegt (Backlog Grooming/[[Backlog_Refinement]]) und dient als zentrale Quelle für die [[Sprint]]-Planung und Umsetzung von [[Produktinkrement|Produktinkrementen]].
- **Nutzen & Zweck:** Das [[Product_Backlog]] löst das Problem unklarer oder verstreuter [[Anforderung|Anforderungen]] in der [[Agile_Entwicklung|agilen Produktentwicklung]]. Es schafft Transparenz über den [[Projektumfang]] und alle anstehenden [[Aufgabe|Aufgaben]], ermöglicht eine flexible Priorisierung basierend auf [[Geschäftswert]] und [[Risiko]] und unterstützt das [[Entwicklungsteam]] dabei, sich auf die wichtigsten [[Feature|Features]] zu konzentrieren. Durch die kontinuierliche Pflege (Backlog Refinement) wird sichergestellt, dass das Team stets an den aktuell relevantesten [[Aufgabe|Aufgaben]] arbeitet und [[Änderung|Änderungen]] schnell integriert werden können. Es dient als einzige Quelle der Wahrheit für [[Anforderung|Anforderungen]] und fördert die [[Zusammenarbeit]] zwischen [[Product_Owner]], [[Scrum_Master]] und Entwicklungsteam.
- **Abgrenzung & Grenzen:** Das [[Product_Backlog]] sollte nicht genutzt werden, wenn ein [[Projekt]] starre, unveränderliche [[Anforderung|Anforderungen]] hat oder ein klassisches [[Wasserfallmodell]] verfolgt, da es auf Flexibilität und iterative [[Anpassung|Anpassungen]] ausgelegt ist. Im Gegensatz zu einem klassischen [[Lastenheft]], das oft statisch und detailliert ist, bleibt das [[Product_Backlog]] bewusst unvollständig und wird erst im Laufe der Zeit verfeinert. Es eignet sich nicht für [[Projekt|Projekte]] mit sehr kurzen Laufzeiten oder minimaler Komplexität, da der Pflegeaufwand dann unverhältnismäßig hoch wäre. Alternativen wie [[Kanban]]-Boards können sinnvoller sein, wenn die [[Anforderung|Anforderungen]] weniger priorisiert und eher flussorientiert abgearbeitet werden sollen. Zudem ersetzt es keine detaillierten [[Spezifikation|Spezifikationen]] und kann bei unklaren [[Anforderung|Anforderungen]] zu häufigen Änderungen führen, was die [[Planungssicherheit]] beeinträchtigen kann.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache Product-Backlog-Eintragsstruktur in Java
public class ProductBacklogItem {
    private String id;
    private String title;
    private String description;
    private int priority; // 1 (höchste) bis 3 (niedrigste)
    private String status; // z.B. "To Do", "In Progress", "Done"
    private List<String> acceptanceCriteria;
    
    public ProductBacklogItem(String id, String title, String description, int priority) {
        this.id = id;
        this.title = title;
        this.description = description;
        this.priority = priority;
        this.status = "To Do";
        this.acceptanceCriteria = new ArrayList<>();
    }
    
    public void addAcceptanceCriterion(String criterion) {
        acceptanceCriteria.add(criterion);
    }
    
    // Getter und Setter...
}

// Beispielhafte Nutzung
ProductBacklogItem item = new ProductBacklogItem(
    "PBI-1", 
    "Mitgliederverwaltung erweitern", 
    "Als Vereinsmanager möchte ich Mitgliederdaten bearbeiten können, um aktuelle Informationen zu pflegen.", 
    1
);
item.addAcceptanceCriterion("Der Vereinsmanager kann Mitgliederdaten anlegen, ändern und löschen.");
item.addAcceptanceCriterion("Bei Abteilungswechsel wird eine Benachrichtigungsmail an [[Stakeholder|Stakeholder]] versendet.");
```

**Hinweis:** In der Praxis werden [[Product_Backlog|Product-Backlog-Einträge]] oft als [[User_Story|User Stories]] formuliert und mit [[Akzeptanzkriterium|Akzeptanzkriterien]] sowie [[Aufwandsschätzung|Aufwandsschätzungen]] (z. B. in [[Story_Point|Story Points]]) versehen. Tools wie [[Jira]] oder [[Azure_DevOps]] unterstützen die Verwaltung und Priorisierung.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9c1
- **Vorgänger / Parent:** [[Scrum-Artefakte]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Scrum-Artefakte]]
  - [[Scrum]]
