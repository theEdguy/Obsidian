---
id: 3caacc72-fffc-471a-a237-e76b05448c74
title: "Vorversion"
date: 2026-06-23
tags:
  - software_engineering
  - projektmanagement
  - prototyping
  - entwicklung
  - draft
source: "software_engineering_kapitel_06"
---

# [[Vorversion]]

- **Kernkonzept:** Eine [[Vorversion]] (auch [[Prototyp]] oder [[Proof_of_Concept]]) ist eine frühe, funktionsfähige Implementierung zentraler [[Funktionalität|Funktionalitäten]] eines [[Softwareprojekt|Softwareprojekts]], die innerhalb von 1-3 Monaten oder 1-2 [[Iteration|Iterationen]] umgesetzt wird. Sie dient der Validierung von [[Architektur]]-Entscheidungen und [[Anforderung|Anforderungen]] sowie als Grundlage für die weitere [[Planung]] und [[Entwicklung]].
- **Nutzen & Zweck:** Die [[Vorversion]] reduziert [[Risiko|Risiken]] durch praktische Erprobung von [[Technologie|Technologien]] und [[Designentscheidung|Designentscheidungen]], vertieft das Problemverständnis und macht die [[Komplexität]] der Aufgabe sichtbar. Sie ermöglicht frühes Feedback von [[Stakeholder|Stakeholdern]], schafft [[Planungssicherheit]] und fixiert [[Architektur]]-Entscheidungen, bevor größere [[Ressource|Ressourcen]] investiert werden. Dadurch werden Unsicherheiten in der frühen Projektphase minimiert.
- **Abgrenzung & Grenzen:** Die [[Vorversion]] ist kein fertiges Produkt und oft mit [[Technische_Schuld|technischer Schuld]] behaftet. Sie eignet sich nicht für [[Projekt|Projekte]] mit klar definierten [[Anforderung|Anforderungen]] und geringer [[Komplexität]], bei denen eine direkte Umsetzung effizienter ist. Im Gegensatz zu einem [[Prototyp|Prototypen]], der oft nur einzelne Aspekte klärt, zielt die [[Vorversion]] auf eine breitere, aber noch unvollständige Umsetzung der Kern[[Funktionalität|funktionalitäten]] ab. Bei extrem kurzen Zeitvorgaben oder starren Rahmenbedingungen kann die Erstellung einer [[Vorversion]] zu aufwendig sein.
- **Beispiel / Code:** ```java
// Beispiel: Vereinfachte Mitgliederverwaltung als Vorversion (Kernfunktionalität)
public class Mitglied {
    private String name;
    private String adresse;
    
    public Mitglied(String name, String adresse) {
        this.name = name;
        this.adresse = adresse;
    }
    
    public void adresseAendern(String neueAdresse) {
        this.adresse = neueAdresse;
        System.out.println("Adresse geändert: " + neueAdresse);
    }
}

public class Mitgliederverwaltung {
    private List<Mitglied> mitglieder = new ArrayList<>();
    
    public void mitgliedHinzufuegen(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }
    
    public void mitgliederAnzeigen() {
        mitglieder.forEach(m -> System.out.println(m.name + ": " + m.adresse));
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b2a
- **Vorgänger / Parent:** [[Evaluierungsphase]]
- **Folgezettel / Unterzettel:**
  - [[Kernfunktionalität]]
  - [[Architektur_fixieren]]
- **Querverweise:** keine
