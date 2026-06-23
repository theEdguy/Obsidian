---
id: 2b32070c-5da0-4d01-adfb-91a6262084b9
title: "Generalisierung"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - vererbung
  - entwurf
  - akteure
  - uml
  - draft
source: "software_engineering_kapitel_07"
---

# [[Generalisierung]]

- **Kernkonzept:** Die [[Generalisierung]] beschreibt die Beziehung zwischen einer [[Oberklasse]] und ihren [[Unterklasse|Unterklassen]] (oder zwischen [[Akteur|Akteuren]] in der [[UML]]), bei der gemeinsame [[Eigenschaft|Eigenschaften]] und [[Verhalten]] in der [[Oberklasse]] (oder dem allgemeineren [[Akteur]]) zusammengefasst werden. Sie ist ein zentrales Konzept der [[Vererbung]] und dient der [[Abstraktion]] sowie der Strukturierung von [[Modell]]en und [[Code]].
- **Nutzen & Zweck:** Die [[Generalisierung]] reduziert [[Redundanz]] und fördert die [[Wiederverwendbarkeit]] von [[Code]] und [[Modell]]en, indem gemeinsame [[Schnittstelle|Schnittstellen]] und [[Verhalten]] in der [[Oberklasse]] oder dem übergeordneten [[Akteur]] definiert werden. Dies erleichtert die [[Erweiterbarkeit]] und [[Wartbarkeit]] von [[Software]] und [[System]]en, da Änderungen nur an einer zentralen Stelle vorgenommen werden müssen. Im Kontext der [[UML]] ermöglicht die Akteur-Generalisierung eine konsistente Modellierung ähnlicher [[Akteur|Akteure]] mit gemeinsamen Interaktionen, ohne diese mehrfach definieren zu müssen.
- **Abgrenzung & Grenzen:** Die [[Generalisierung]] sollte nicht genutzt werden, wenn [[Unterklasse|Unterklassen]] oder [[Akteur|Akteure]] keine gemeinsamen [[Eigenschaft|Eigenschaften]] oder [[Verhalten]] teilen, da dies zu unnötiger Komplexität oder dem [[Fragile_Base_Class_Problem]] führen kann. Übermäßige [[Generalisierung]] kann zudem die [[Kohäsion]] verringern und die [[Lesbarkeit]] des [[Code]]s oder [[Modell]]s beeinträchtigen. Alternativ können einfache [[Assoziation|Assoziationen]] oder [[Komposition]] verwendet werden, wenn keine Vererbungsbeziehung besteht. Im Kontext der [[UML]] ist die Akteur-Generalisierung von <<include>>- oder <<extend>>-Beziehungen zwischen [[Use_Case|Use Cases]] abzugrenzen, da sie sich auf die Hierarchie von [[Akteur|Akteuren]] und nicht auf die Struktur von [[Anwendungsfall|Anwendungsfällen]] bezieht.
- **Beispiel / Code:** ```java
// Generalisierung in der Objektorientierung: Team als Oberklasse
public abstract class Team {
    protected String name;
    
    public abstract int leistungsprognose(Date datum);
}

// Spezialisierung: DDDTeam als Unterklasse
public class DDDTeam extends Team {
    @Override
    public int leistungsprognose(Date datum) {
        return 42;
    }
}
```

```java
// UML-Notation für Akteur-Generalisierung (Modellierung, kein ausführbarer Code)
@startuml
actor Benutzer
actor Administrator --|> Benutzer

Benutzer --> (Use Case 1)
Administrator --> (Use Case 2)
@enduml
```

Im ersten Beispiel erbt die [[Unterklasse]] `DDDTeam` die [[Eigenschaft]] `name` und die [[Schnittstelle]] `leistungsprognose` von der [[Oberklasse]] `Team`. Im zweiten Beispiel erbt der [[Akteur]] *Administrator* alle Beziehungen des [[Akteur|Akteurs]] *Benutzer* und kann zusätzlich spezifische [[Use_Case|Use Cases]] ausführen.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b2a
- **Vorgänger / Parent:** [[Use_Case_Akteure]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Akteur]]
  - [[Vererbung]]
