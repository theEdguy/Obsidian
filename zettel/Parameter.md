---
id: 80d8cb77-d4df-4ce8-acf6-985808c2752c
title: "Parameter"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - uml
  - datenfluss
  - draft
source: "software_engineering_kapitel_08"
---

# [[Parameter]]

- **Kernkonzept:** Parameter in Activity-Diagrammen der UML sind fortgeschrittene Modellierungselemente, die den Datenfluss zwischen Aktionen präzise steuern und Eingabe- sowie Ausgabewerte von Aktionen explizit darstellen. Sie ermöglichen die Definition von Schnittstellen für Aktivitäten und deren Teilaktionen.
- **Nutzen & Zweck:** Parameter lösen das Problem der unklaren Datenübergabe in komplexen Abläufen, indem sie den Datenfluss zwischen Aktionen formalisieren und dokumentieren. Sie erhöhen die Verständlichkeit und Wartbarkeit von Modellen, da sie Eingabe- und Ausgabewerte sichtbar machen und so die Schnittstellen zwischen Systemkomponenten oder Akteuren transparent gestalten. Dies ist besonders nützlich, um Abhängigkeiten in verteilten oder modularen Systemen zu modellieren.
- **Abgrenzung & Grenzen:** Parameter sollten nicht genutzt werden, wenn der Datenfluss trivial oder offensichtlich ist, da sie die Komplexität des Diagramms unnötig erhöhen. Alternativen wie einfache Objektknoten oder textuelle Beschreibungen reichen oft aus, um Datenflüsse in einfachen Szenarien darzustellen. Parameter unterscheiden sich von Pins dadurch, dass sie auf der Ebene der gesamten Aktivität definiert werden, während Pins spezifisch für einzelne Aktionen sind. Bei rein sequenziellen Abläufen ohne Datenabhängigkeiten sind Parameter überflüssig.
- **Beispiel / Code:** ```java
// Beispiel für eine Aktivität mit Parametern in UML-Notation (pseudocode)
activity MitgliedVerwalten {
    in parameter neuerMitgliedsantrag: Mitgliedsdaten;
    out parameter bestaetigung: Bestätigungsnachricht;
    
    action AntragPrüfen(in neuerMitgliedsantrag, out geprüfterAntrag);
    action MitgliedAnlegen(in geprüfterAntrag, out bestaetigung);
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a5a
- **Vorgänger / Parent:** [[Objektknoten]]
- **Folgezettel / Unterzettel:**
  - [[Pin]]
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
