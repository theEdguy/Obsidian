---
id: 30d972f6-ff79-4152-9af1-77b531ad8bb8
title: "UML_Instanzdiagramm"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - softwarearchitektur
  - draft
source: "software_engineering_kapitel_04"
---

# [[UML_Instanzdiagramm]]

- **Kernkonzept:** Ein [[Diagrammtyp]] der [[UML]], der konkrete [[Instanz|Instanzen]] von [[Klasse|Klassen]] und deren [[Beziehung|Beziehungen]] zur [[Laufzeit]] als [[Momentaufnahme]] darstellt. Es visualisiert [[Objekt|Objekte]] mit ihren aktuellen [[Attributwert|Attributwerten]] und dient der Abbildung konkreter Ausprägungen eines [[UML_Klassendiagramm|Klassendiagramms]] in spezifischen Szenarien.
- **Nutzen & Zweck:** UML-Instanzdiagramme helfen, die dynamischen Aspekte eines [[System|Systems]] zu veranschaulichen, indem sie konkrete [[Objekt|Objekte]], deren [[Zustand|Zustände]] und [[Beziehung|Beziehungen]] untereinander abbilden. Sie lösen das Problem, abstrakte [[Klasse|Klassenmodelle]] in konkrete Szenarien zu überführen, und unterstützen damit [[Testfall|Testfälle]], [[Debugging]]-Prozesse sowie die Kommunikation zwischen [[Entwickler|Entwicklern]] und [[Stakeholder|Stakeholdern]]. Durch die Darstellung realer oder hypothetischer [[Objektgraph|Objektkonstellationen]] vertiefen sie das Verständnis für die [[Systemstruktur]] und [[Interaktion|Interaktionen]] innerhalb des [[System|Systems]]. Besonders nützlich sind sie für die [[Dokumentation]] von [[Laufzeitverhalten]] und die [[Fehlersuche]] in komplexen [[Objektgraph|Objektgraphen]].
- **Abgrenzung & Grenzen:** Instanzdiagramme sind kein Ersatz für [[UML_Klassendiagramm|Klassendiagramme]], da sie keine allgemeine [[Systemstruktur]] oder statische [[Architektur]] abbilden. Sie zeigen lediglich [[Momentaufnahme|Momentaufnahmen]] spezifischer [[Objekt|Objektkonstellationen]] und eignen sich nicht für die Modellierung von [[Vererbung|Vererbungshierarchien]], [[Schnittstelle|Schnittstellen]] oder generischen [[Beziehung|Beziehungen]]. Für die Darstellung von [[Systemverhalten]] über die Zeit sind stattdessen [[UML_Sequenzdiagramm|Sequenzdiagramme]] oder [[UML_Zustandsdiagramm|Zustandsdiagramme]] zu verwenden. Zudem sind sie ungeeignet für die Abbildung von [[Meta-Modell|Meta-Modellen]] oder abstrakten Konzepten, die keine konkreten [[Instanz|Instanzen]] besitzen. Instanzdiagramme sollten auch nicht zur Definition von [[Entwurfsmuster|Mustern]] oder [[Softwarearchitektur|Architekturprinzipien]] genutzt werden, da sie auf die Visualisierung von [[Laufzeit|Laufzeitaspekten]] beschränkt sind.
- **Beispiel / Code:** ```uml
object :Spieler {
    name = "Max Mustermann"
    nummer = 10
}

object :Mitglied {
    name = "Erika Beispiel"
    adresse = ("76131 Karlsruhe", "Musterstraße 1")
    leistung = 1051
}

object :Team {
    name = "Herrenliga A"
    mitglieder = {:Mitglied, ...}
}

:Mitglied -- :Spieler
:Team -- :Mitglied
```

```java
// Textuelle Darstellung eines UML-Instanzdiagramms
Mitglied aMitglied:Verein::Mitglied
name = 'Thomas Fuchß'
adresse = ('76131 Karlsruhe', 'Musterstraße 1')
leistung = 1051

Team aTeam:Verein::Team
name = 'Herrenliga A'
mitglieder = {aMitglied, ...}
```

// Grafische UML-Notation (Beschreibung):
// - Rechteck mit unterstrichenem Objektnamen (z. B. `aMitglied:Mitglied`)
// - Attribute mit konkreten Werten (z. B. `name = 'Thomas Fuchß'`)
// - Gestrichelte Linien für [[Link|Links]] zwischen [[Objekt|Objekten]] (z. B. zwischen `aTeam` und `aMitglied`)

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 6
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[UML-Klassendiagramm]]
  - [[Meta-Modell]]
