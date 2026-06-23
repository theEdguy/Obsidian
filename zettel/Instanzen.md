---
id: 72fdda9a-e9f2-42f9-86bb-a7041d4d0997
title: "Instanzen"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - draft
source: "software_engineering_kapitel_03"
---

# [[Instanzen]]

- **Kernkonzept:** Instanzen sind konkrete Ausprägungen einer Klasse in der objektorientierten Programmierung und Modellierung. Sie repräsentieren individuelle Objekte mit spezifischen Attributwerten, die nach den Vorgaben der Klasse strukturiert sind und deren Verhalten teilen.
- **Nutzen & Zweck:** Instanzen ermöglichen die Abbildung realer oder abstrakter Entitäten als eigenständige Objekte mit individuellen Zuständen und Verhaltensweisen. Sie lösen das Problem, gleichartige Strukturen (Klassen) in konkrete, unterscheidbare Einheiten zu überführen, um Daten und Funktionen im System dynamisch zu verarbeiten. Dadurch wird die Modellierung komplexer Systeme mit vielen ähnlichen, aber nicht identischen Objekten praktikabel.
- **Abgrenzung & Grenzen:** Instanzen sollten nicht genutzt werden, wenn es um die Beschreibung allgemeiner Strukturen oder Vorlagen geht – hierfür sind Klassen zuständig. Im Gegensatz zu statischen Datenstrukturen (z. B. Arrays oder Records) sind Instanzen ungeeignet, wenn keine individuellen Zustände oder Verhaltensweisen benötigt werden. Zudem kann der Overhead durch Objektidentität und dynamische Speicherverwaltung in performancekritischen Systemen nachteilig sein. Alternativen wie primitive Datentypen oder funktionale Ansätze kommen infrage, wenn keine Objektorientierung erforderlich ist.
- **Beispiel / Code:** ```java
// Definition einer Klasse
class Mitglied {
    private String name;
    private String adresse;
    
    public Mitglied(String name, String adresse) {
        this.name = name;
        this.adresse = adresse;
    }
    
    public String getName() {
        return name;
    }
}

// Erstellung von Instanzen (konkrete Objekte)
Mitglied mitglied1 = new Mitglied("Anna Schmidt", "Musterstraße 1");
Mitglied mitglied2 = new Mitglied("Peter Müller", "Beispielweg 2");
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1a
- **Vorgänger / Parent:** [[Klassen]]
- **Folgezettel / Unterzettel:**
  - [[Objektidentität]]
- **Querverweise:**
  - [[Objekte]]
