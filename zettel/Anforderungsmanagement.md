---
id: b5d805f7-c2bb-428f-ba77-71130ddc6c65
title: "Anforderungsmanagement"
date: 2026-06-23
tags:
  - software_engineering
  - anforderungen
  - management
  - draft
source: "software_engineering_kapitel_07"
---

# [[Anforderungsmanagement]]

- **Kernkonzept:** Anforderungsmanagement ist ein systematischer Prozess zur Identifikation, Dokumentation, Priorisierung und Verwaltung von funktionalen und nicht-funktionalen Anforderungen an ein Softwaresystem, um eine zielgerichtete und bedarfsgerechte Entwicklung zu ermöglichen.
- **Nutzen & Zweck:** Anforderungsmanagement existiert, um die Komplexität von Softwareprojekten beherrschbar zu machen, indem es klare Vorgaben für Entwicklung, Test und Evaluation schafft. Es löst das Problem unklarer, widersprüchlicher oder unvollständiger Anforderungen, die zu Fehlentwicklungen, Nacharbeit oder Projektmisserfolg führen können. Durch strukturierte Erfassung und Bewertung von Anforderungen wird sichergestellt, dass alle Stakeholder ein gemeinsames Verständnis des Systems entwickeln und die Entwicklung an den tatsächlichen Bedürfnissen ausgerichtet wird.
- **Abgrenzung & Grenzen:** Anforderungsmanagement sollte nicht genutzt werden, wenn das Projekt trivial ist oder keine klaren Stakeholder-Anforderungen existieren, da der Aufwand dann unverhältnismäßig hoch wäre. Es unterscheidet sich von ad-hoc-Anforderungserfassung durch seine Systematik und Nachverfolgbarkeit. Alternativen wie User Stories (z. B. in Scrum) sind weniger formal und eignen sich eher für agile Projekte mit sich schnell ändernden Anforderungen, während Anforderungsmanagement klassisch in planungsintensiven Projekten (z. B. nach dem V-Modell) eingesetzt wird.
- **Beispiel / Code:** ```java
// Beispiel für eine strukturierte Anforderungsdokumentation in einem Use-Case-Format
public class UseCase {
    private String name = "Mitglieder verwalten";
    private String systemgrenze = "MyClub";
    private List<String> akteure = Arrays.asList("Vereinsmanager", "Mail Client");
    private int prioritaet = 1;
    private List<String> requirements = Arrays.asList("F1.1", "F1.2", "F2.1");
    private String beschreibung = "Der Vereinsmanager kann Mitglieder anlegen, bearbeiten oder löschen. " +
                              "Bei Abteilungswechseln werden Abteilungsleiter und Mitglieder per E-Mail informiert.";
    
    public void dokumentiereAnforderung() {
        System.out.println("Use Case: " + name);
        System.out.println("Anforderungen: " + String.join(", ", requirements));
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 10
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Anforderungsidentifikation]]
  - [[Anforderungsklassifikation]]
  - [[Anforderungsdokumentation]]
  - [[Anforderungsvalidierung]]
- **Querverweise:**
  - [[Use_Case]]
  - [[Software-Engineering-Prozess]]
