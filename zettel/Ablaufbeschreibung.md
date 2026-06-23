---
id: 314a2bc8-7c67-4cd6-b801-3a0d4142591b
title: "Ablaufbeschreibung"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - requirements_engineering
  - draft
source: "software_engineering_kapitel_09"
---

# [[Ablaufbeschreibung]]

- **Kernkonzept:** Eine Ablaufbeschreibung definiert die schrittweise Abfolge von Interaktionen und Systemoperationen innerhalb eines Use Cases, um die dynamischen Aspekte der Problemdomäne zu erfassen und zu strukturieren. Sie dient als Grundlage für die Identifikation von Objekten, Schnittstellen und Systemverhalten.
- **Nutzen & Zweck:** Die Ablaufbeschreibung löst das Problem, komplexe Prozesse und Interaktionen in der Problemdomäne verständlich und nachvollziehbar zu dokumentieren. Sie ermöglicht es, zentrale Abläufe zu analysieren, Systemoperationen zu identifizieren und Schnittstellen zwischen Akteuren und System zu definieren. Dadurch wird sichergestellt, dass die Anforderungen präzise erfasst und in spätere Designphasen überführt werden können.
- **Abgrenzung & Grenzen:** Eine Ablaufbeschreibung sollte nicht genutzt werden, wenn es um die detaillierte technische Umsetzung oder die Modellierung statischer Strukturen geht, wie z. B. Klassenhierarchien oder Datenbankschemata. Sie unterscheidet sich von statischen Modellen wie Klassendiagrammen, da sie sich auf das dynamische Verhalten konzentriert. Zudem ist sie keine Alternative zu formalen Spezifikationen wie Zustandsautomaten, sondern ergänzt diese durch eine narrative oder diagrammatische Darstellung von Interaktionsfolgen.
- **Beispiel / Code:** ```java
// Beispiel für eine Systemoperation in einem System-Sequenz-Diagramm (pseudocode)
public class MitgliedVerwaltung {
    // Systemoperation: Mitglied aus Abteilung entfernen
    public void abteilungVerlassen(Mitglied mitglied, Abteilung abteilung) {
        if (!mitglied.istInAbteilung(abteilung)) {
            throw new IllegalArgumentException("Mitglied gehört nicht der Abteilung an.");
        }
        abteilung.entferneMitglied(mitglied);
        if (mitglied.getAbteilungen().isEmpty()) {
            mitglied.setStatus("passiv");
            mitglied.sendeBenachrichtigung("Ihr Status wurde auf 'passiv' gesetzt.");
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b1
- **Vorgänger / Parent:** [[Use-Case-Beschreibung]]
- **Folgezettel / Unterzettel:**
  - [[Hauptszenario]]
  - [[Alternativszenario]]
  - [[Ausnahmeszenario]]
- **Querverweise:**
  - [[Textuelle_Analyse]]
  - [[Anforderungsdokumentation]]
