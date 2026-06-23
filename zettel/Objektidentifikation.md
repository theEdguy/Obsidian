---
id: 608a9ba5-80e9-4ebf-8099-fa80fc1901d0
title: "Objektidentifikation"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Objektidentifikation]]

- **Kernkonzept:** Objektidentifikation ist ein zentraler Schritt in der objektorientierten Analyse, bei dem Konzepte und Entitäten der Problemdomäne als Objekte modelliert werden, um die Strukturen und Zusammenhänge des Anwendungsbereichs systematisch zu erfassen.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem, die relevanten Elemente eines Systems und deren Beziehungen frühzeitig zu erkennen, bevor technische Lösungen entworfen werden. Es ermöglicht eine klare Trennung zwischen Problemdomäne und Implementierung, indem es die Grundlage für das Analyse-Objektmodell schafft und Missverständnisse zwischen Stakeholdern reduziert.
- **Abgrenzung & Grenzen:** Objektidentifikation sollte nicht angewendet werden, wenn bereits eine detaillierte technische Lösung im Vordergrund steht, da es sich auf die Problemdomäne konzentriert. Es unterscheidet sich von Datenmodellierung oder Datenbankdesign, da es keine Attribute oder technische Realisierung vorwegnimmt, sondern ausschließlich Konzepte und deren Beziehungen betrachtet. Zudem ist es ungeeignet für nicht-objektorientierte Ansätze wie funktionale Programmierung.
- **Beispiel / Code:** ```java
// Beispiel: Objekte aus dem Use Case 'Mitglieder verwalten'
class Mitglied {
    private String name;
    private MitgliedStatus status;
    private List<Abteilung> abteilungen;
    
    public void abteilungVerlassen(Abteilung abteilung) {
        abteilungen.remove(abteilung);
        if (abteilungen.isEmpty()) {
            this.status = MitgliedStatus.PASSIV;
        }
    }
}

class Abteilung {
    private String name;
    private List<Mitglied> mitglieder;
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2a
- **Vorgänger / Parent:** [[Objektorientierte_Analyse]]
- **Folgezettel / Unterzettel:**
  - [[Klassenkandidat]]
  - [[Attribut_vs._Konzept]]
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Fachkonzept]]
