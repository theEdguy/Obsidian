---
id: b4992fd7-a117-46ba-aa35-0f6ff87b5215
title: "Analyse-Objektmodell"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - objektorientierung
  - domänenmodellierung
  - modellierung
  - draft
source: "software_engineering_kapitel_06"
---

# [[Analyse-Objektmodell]]

- **Kernkonzept:** Das [[Analyse-Objektmodell]] ist ein zentrales [[Artefakt]] der [[objektorientierten_Analyse|objektorientierten Analyse]], das die [[Problemdomäne]] durch [[Kernkonzept|Kernkonzepte]], deren [[Attribut|Attribute]], [[Beziehung|Beziehungen]] und [[Verantwortlichkeit|Verantwortlichkeiten]] abbildet. Es dient der [[Strukturierung]] des [[Problemraums]] und visualisiert sowohl strukturelle [[Zusammenhang|Zusammenhänge]] als auch dynamische [[Aspekt|Aspekte]] des zu lösenden Problems, ohne [[Lösungsraum|Lösungsdetails]] vorwegzunehmen.
- **Nutzen & Zweck:** Das [[Analyse-Objektmodell]] schafft ein gemeinsames [[Verständnis]] der [[Problemdomäne]] zwischen [[Entwickler|Entwicklern]], [[Auftraggeber|Auftraggebern]] und [[Stakeholder|Stakeholdern]]. Es reduziert die [[Komplexität]] durch systematische Erfassung realer [[Entität|Entitäten]], deren [[Eigenschaft|Eigenschaften]] und [[Interaktion|Interaktionen]], wodurch [[Missverständnis|Missverständnisse]] minimiert und die Grundlage für eine konsistente [[Softwareentwicklung]] gelegt wird. Insbesondere bereitet es die spätere [[Designphase|Design-]] und [[Implementierungsphase|Implementierungsphase]] vor, indem es [[Kernkonzept|Kernkonzepte]] und deren [[Zusammenhang|Zusammenhänge]] frühzeitig identifiziert und dokumentiert. Dadurch wird die [[Kohäsion]] des [[Systems]] gestärkt und die [[Wartbarkeit]] verbessert.
- **Abgrenzung & Grenzen:** Das [[Analyse-Objektmodell]] ist nicht sinnvoll einsetzbar, wenn die [[Problemdomäne]] trivial oder bereits vollständig verstanden ist, da der Modellierungsaufwand dann unverhältnismäßig hoch wäre. Es unterscheidet sich vom [[Design-Modell]] durch den expliziten Verzicht auf [[Technische_Detail|technische Details]] wie [[Datenbankstruktur|Datenbankstrukturen]], [[Framework|Framework-spezifische]] [[Klasse|Klassen]] oder [[Implementierungsdetail|Implementierungsdetails]]. Im Gegensatz zu [[Use-Case|Use-Case-Beschreibungen]] oder [[Datenflussdiagramm|Datenflussdiagrammen]] bietet es keine funktionale [[Übersicht]], sondern eine strukturelle und konzeptionelle [[Repräsentation]] der [[Problemdomäne]]. Alternativmodelle wie [[Datenmodell|Datenmodelle]] fokussieren sich auf persistente [[Datenstruktur|Datenstrukturen]], während das [[Analyse-Objektmodell]] die [[Domänenlogik]] und [[Geschäftsregel|Geschäftsregeln]] in den Vordergrund stellt.
- **Beispiel / Code:** ```uml
@startuml
class Mitglied {
  -name: String
  -adresse: String
  -status: [[MitgliedStatus|Status]]
  
  +adresseAendern(neueAdresse: String)
  +statusAbfragen(): [[MitgliedStatus|Status]]
}

class Abteilung {
  -name: String
}

class Verein {
  -mitglieder: List<[[Mitglied|Mitglieder]]>
  
  +mitgliedHinzufuegen(neuesMitglied: [[Mitglied]])
  +mitgliederListeErstellen(): List<[[Mitglied|Mitglieder]]>
}

Mitglied "1" -- "*" Abteilung: gehört zu >
Verein "1" *-- "*" Mitglied: verwaltet >

enum MitgliedStatus {
  AKTIV
  PASSIV
  EHRENMITGLIED
}
@enduml
```

```java
// Beispiel: Analyse-Objektmodell für eine Mitgliederverwaltung (vereinfacht)
class Mitglied {
    private String name;
    private String adresse;
    private MitgliedStatus status;
    
    public void adresseAendern(String neueAdresse) {
        this.adresse = neueAdresse;
    }
    
    public MitgliedStatus statusAbfragen() {
        return this.status;
    }
}

class Verein {
    private List<Mitglied> mitglieder;
    
    public void mitgliedHinzufuegen(Mitglied neuesMitglied) {
        mitglieder.add(neuesMitglied);
    }
    
    public List<Mitglied> mitgliederListeErstellen() {
        return new ArrayList<>(mitglieder);
    }
}

enum MitgliedStatus {
    AKTIV, PASSIV, EHRENMITGLIED
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a5a
- **Vorgänger / Parent:** [[Analysemodellierung]]
- **Folgezettel / Unterzettel:**
  - [[Klassen_identifizieren]]
  - [[Beziehungen_definieren]]
  - [[Zustandsänderungen_modellieren]]
- **Querverweise:** keine
