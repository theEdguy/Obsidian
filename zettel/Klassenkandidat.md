---
id: e4a168fe-6d82-4ff4-99fa-1f1207cbea2d
title: "Klassenkandidat"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Klassenkandidat]]

- **Kernkonzept:** Ein Klassenkandidat ist ein identifiziertes Konzept oder Objekt aus der Problemdomäne, das als potenzielle Klasse im Analyse-Objektmodell einer Software betrachtet wird. Es repräsentiert eine Entität, die durch Substantive in Use-Case-Beschreibungen oder Checklisten ermittelt wird und strukturelle oder funktionale Bedeutung im System hat.
- **Nutzen & Zweck:** Das Konzept des Klassenkandidaten dient dazu, die Problemdomäne systematisch zu analysieren und die relevanten Strukturen und Zusammenhänge zu erfassen. Es hilft, die zentralen Objekte und deren Beziehungen frühzeitig zu identifizieren, um ein fundiertes Analyse-Objektmodell zu erstellen. Dadurch wird sichergestellt, dass die Softwarelösung die realen Anforderungen abbildet und nicht vorschnell technische Lösungen entwickelt werden.
- **Abgrenzung & Grenzen:** Ein Klassenkandidat sollte nicht mit Attributen verwechselt werden, die lediglich Eigenschaften von Objekten beschreiben. Während Attribute oft einfache Datentypen wie Zahlen oder Texte darstellen, repräsentieren Klassenkandidaten eigenständige Konzepte mit potenziell komplexen Zuständen und Verhalten. Zudem ist nicht jedes Substantiv aus Use-Case-Beschreibungen ein Klassenkandidat – es muss durch die Problemdomäne validiert werden. Alternativen wie Datenflussdiagramme oder reine Funktionsmodelle bieten keine vergleichbare Objektorientierung.
- **Beispiel / Code:** ```java
// Beispiel: Klassenkandidaten im Use Case 'Mitglieder verwalten'
class Mitglied {
    private String name;
    private MitgliedStatus status;
    private List<Abteilung> abteilungen;
    
    public void abteilungVerlassen(Abteilung abteilung) {
        // Logik zum Entfernen aus der Abteilung
    }
}

class Abteilung {
    private String name;
    private List<Mitglied> mitglieder;
}

// 'Mitglied' und 'Abteilung' sind Klassenkandidaten, während 'name' oder 'status' Attribute darstellen.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2a1
- **Vorgänger / Parent:** [[Objektidentifikation]]
- **Folgezettel / Unterzettel:**
  - [[Checklistenmethode]]
  - [[Substantivmethode]]
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Fachkonzept]]
