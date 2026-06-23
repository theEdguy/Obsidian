---
id: d6c57397-fd52-4637-9641-4333a9233023
title: "Requirements_Engineering"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - prozess
  - anforderungen
  - draft
source: "software_engineering_kapitel_06"
---

# [[Requirements_Engineering]]

- **Kernkonzept:** [[Requirements_Engineering]] ist der [[Prozess]] der systematischen [[Erhebung]], [[Analyse]], [[Dokumentation]] und [[Validierung]] sowie [[Verwaltung]] von [[Anforderung|Anforderungen]] an ein [[Software-System]]. Es zielt darauf ab, die [[Bedürfnisse]] und [[Erwartung|Erwartungen]] aller [[Stakeholder]] präzise zu verstehen und in umsetzbare [[Spezifikation|Spezifikationen]] zu überführen.
- **Nutzen & Zweck:** [[Requirements_Engineering]] stellt sicher, dass das [[Software-System]] die [[Bedürfnisse]] der [[Stakeholder]] erfüllt und vermeidet [[Missverständnis|Missverständnisse]] oder [[Fehlentwicklung|Fehlentwicklungen]] durch unklare, widersprüchliche oder unvollständige [[Anforderung|Anforderungen]]. Es löst das zentrale [[Problem]] der [[Softwareentwicklung]], indem es eine gemeinsame Grundlage für [[Entwickler]], [[Auftraggeber]] und [[Nutzer]] schafft. Dadurch werden [[Priorisierung|Prioritäten]] gesetzt, die [[Machbarkeit]] eines [[Projekt|Projekts]] realistisch bewertet und [[Kosten]] sowie [[Zeitverzögerung|Zeitverzögerungen]] reduziert. Zudem ermöglicht es die frühzeitige Erkennung von [[Risiko|Risiken]] und die systematische Einbindung aller [[Stakeholder]] in den [[Anforderungsprozess]].
- **Abgrenzung & Grenzen:** [[Requirements_Engineering]] ist kein Ersatz für direkte [[Kommunikation]] mit [[Stakeholder|Stakeholdern]] und erfordert [[Iteration|Iterationen]], da sich [[Anforderung|Anforderungen]] oft ändern. Es sollte nicht eingesetzt werden, wenn die [[Anforderung|Anforderungen]] bereits vollständig und eindeutig definiert sind oder bei sehr kleinen, trivialen [[Projekt|Projekten]], bei denen der Aufwand den [[Nutzen]] übersteigt. Im Gegensatz zu ad-hoc-[[Anforderungserhebung|Anforderungserhebungen]] zeichnet es sich durch eine strukturierte [[Vorgehensweise]] aus, die systematische Einbindung aller [[Stakeholder]] und die Verwendung formaler [[Methode|Methoden]] wie [[Use-Case-Modellierung]] oder [[Metrik|Metriken]] zur Bewertung nicht-funktionaler [[Anforderung|Anforderungen]] umfasst. Während [[agile_Entwicklung|agile Ansätze]] [[Anforderung|Anforderungen]] iterativ entwickeln, legt [[Requirements_Engineering]] stärkeren Fokus auf eine initiale, umfassende [[Analysephase]]. Nicht alle [[Anforderung|Anforderungen]] lassen sich formalisieren, insbesondere wenn sie subjektive oder kontextabhängige [[Kriterium|Kriterien]] betreffen.
- **Beispiel / Code:** ```java
// Beispiel für eine funktionale Anforderung in tabellarischer Form (als Java-Klasse modelliert)
public class Requirement {
    private String id;          // Referenznummer (z. B. "F1.1")
    private String description; // Beschreibung (z. B. "[[Benutzerauthentifizierung|Benutzerauthentifizierung]] unterstützen")
    private Category category;  // Kategorie (z. B. sichtbar, versteckt, optional)
    private Priority priority;  // Priorität (z. B. [[Must-have|must]], [[Should-have|should]], [[Could-have|could]])
    
    public Requirement(String id, String description, Category category, Priority priority) {
        this.id = id;
        this.description = description;
        this.category = category;
        this.priority = priority;
    }
    
    // Getter und Setter...
}

// Beispiel für eine nicht-funktionale Anforderung mit Metrik
public class NonFunctionalRequirement {
    private String id;          // Referenznummer (z. B. "A1.7")
    private String constraint;  // Constraint (z. B. "[[Datenverschlüsselung]] mit AES-256")
    private Metric metric;      // Metrik (z. B. "[[Verschlüsselungsstärke]]: 256 Bit")
    
    public NonFunctionalRequirement(String id, String constraint, Metric metric) {
        this.id = id;
        this.constraint = constraint;
        this.metric = metric;
    }
}
```

// Beispiel für eine einfache funktionale Anforderung (aus der ursprünglichen Notiz):
// Funktionale [[Anforderung]]: Das System muss [[Benutzerauthentifizierung|Benutzerauthentifizierung]] unterstützen.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a
- **Vorgänger / Parent:** [[Software-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Funktionale_Anforderungen]]
  - [[Nicht-funktionale_Anforderungen]]
  - [[Technische_Anforderungen]]
  - [[Use-Case-Modellierung]]
  - [[Analysemodellierung]]
- **Querverweise:** keine
