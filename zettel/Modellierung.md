---
id: 25ae4cd8-da9d-443e-87db-75b9c6d8ce46
title: "Modellierung"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - design
  - sprache
  - draft
source: "software_engineering_kapitel_06"
---

# [[Modellierung]]

- **Kernkonzept:** Modellierung im [[Software_Engineering]] bezeichnet den Prozess der abstrakten Darstellung von [[System|Systemen]], [[Struktur|Strukturen]] oder [[Prozess|Prozessen]] mittels standardisierter Notationen wie [[UML]], um komplexe Sachverhalte vereinfacht und präzise zu beschreiben. Sie dient als Grundlage für [[Analyse]], [[Design]] und Kommunikation in der Softwareentwicklung und umfasst insbesondere die [[UML-Modellierung]], eine standardisierte grafische [[Sprache]] zur Spezifikation, Konstruktion, Dokumentation und Visualisierung von [[Software-System|Software-Systemen]], vor allem im [[Objektorientierte_Programmierung|objektorientierten]] Bereich.
- **Nutzen & Zweck:** Modellierung löst das Problem der Komplexitätsbewältigung in der Softwareentwicklung, indem sie eine visuelle und strukturierte Repräsentation von [[Anforderung|Anforderungen]], [[Systemarchitektur|Systemarchitekturen]] und Beziehungen schafft. Sie ermöglicht frühzeitige [[Fehlererkennung]], verbessert die Zusammenarbeit zwischen [[Stakeholder|Stakeholdern]] und dient als Blaupause für die Implementierung, wodurch Entwicklungsrisiken reduziert und die [[Wartbarkeit]] erhöht werden. Die [[UML-Modellierung]] stellt dabei eine einheitliche [[Sprache]] für die Kommunikation zwischen [[Entwickler|Entwicklern]], [[Architekt|Architekten]] und Stakeholdern bereit, beseitigt Mehrdeutigkeiten in [[Anforderung|Anforderungen]] und [[Designentscheidung|Designentscheidungen]] und macht die [[Analyse]], das [[Design]] sowie die Dokumentation effizienter und weniger fehleranfällig. Durch die Verwendung verschiedener [[Diagrammtyp|Diagrammtypen]] können sowohl strukturelle als auch verhaltensbezogene Aspekte eines [[System|Systems]] dargestellt werden, was die [[Kohäsion]] und [[Lose_Kopplung|lose Kopplung]] im [[Design]] fördert.
- **Abgrenzung & Grenzen:** Modellierung sollte nicht eingesetzt werden, wenn der Aufwand für die Erstellung und Pflege der [[Modell|Modelle]] den Nutzen übersteigt, z. B. bei trivialen oder kurzlebigen [[System|Systemen]]. Sie unterscheidet sich von direkter Implementierung durch ihren Fokus auf Abstraktion und Vorwegnahme von [[Designentscheidung|Designentscheidungen]], was bei [[Agile_Softwareentwicklung|agilen Projekten]] mit sich ändernden [[Anforderung|Anforderungen]] hinderlich sein kann. Alternativen wie [[Prototyping]] oder [[Code-First-Ansatz|Code-First-Ansätze]] eignen sich besser für explorative oder hochdynamische Entwicklungsprozesse. Die [[UML-Modellierung]] ist zudem weniger geeignet für nicht-objektorientierte [[System|Systeme]] oder Projekte, die stark auf [[Funktionale_Programmierung|funktionale Programmierung]] setzen. Übermäßige Modellierung ("[[Analysis_Paralysis]]") kann die Entwicklung verlangsamen. Bei sehr kleinen oder trivialen Projekten können informelle Skizzen oder textuelle Beschreibungen ausreichen. Domänenspezifische [[Sprache|Sprachen]] ([[DSL]]) oder [[Agile_Softwareentwicklung|agile Methoden]] wie [[User_Story|User Stories]] bieten oft bessere Unterstützung für spezifische Geschäftslogik oder iterative [[Anforderung|Anforderungen]].
- **Beispiel / Code:** ```java
// Beispiel einer binären Assoziation in UML-ähnlicher Notation (Klassendiagramm)
// Modellierung einer Beziehung zwischen [[Mitglied]] und [[Disziplin]] mit Navigierbarkeit
class Mitglied {
    private List<Disziplin> disziplinen;
    private String name;
    private String adresse;
    private List<Mitgliedsbeitrag> beitraege;

    public void disziplinHinzufuegen(Disziplin disziplin) {
        disziplinen.add(disziplin);
    }

    public void adresseAendern(String neueAdresse) {
        this.adresse = neueAdresse;
    }

    public void beitragHinzufuegen(Mitgliedsbeitrag beitrag) {
        beitraege.add(beitrag);
    }
}

class Disziplin {
    // Disziplin kennt keine Mitglieder (nicht navigierbar)
}

// Assoziationsklasse zur Modellierung zusätzlicher Attribute
class Ausuebung {
    private Mitglied mitglied;
    private Disziplin disziplin;
    private LocalDate seit;
    private int ranking;
}

class Mitgliedsbeitrag {
    private double betrag;
    private LocalDate faelligkeitsdatum;
}
```

// Entsprechendes UML-Klassendiagramm:
// [Mitglied] 1 -- * [Disziplin] (navigierbar von Mitglied zu Disziplin)
// [Mitglied] 1 -- * [Mitgliedsbeitrag]
// [Mitglied] 1 -- * [Ausuebung] * -- 1 [Disziplin]
// - name: String
// - adresse: String
// + adresseAendern(neueAdresse: String)
// + disziplinHinzufuegen(disziplin: Disziplin)
// + beitragHinzufuegen(beitrag: Mitgliedsbeitrag)

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d
- **Vorgänger / Parent:** [[Software-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Use-Case-Diagramme]]
  - [[Klassendiagramme]]
  - [[Aktivitätsdiagramme]]
  - [[Sequenzdiagramme]]
  - [[Zustandsdiagramme]]
- **Querverweise:** keine
