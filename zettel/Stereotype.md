---
id: a9915c4c-7612-4a7a-8969-992e7f682ed7
title: "Stereotype"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - erweiterung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Stereotype]]

- **Kernkonzept:** [[Stereotype|Stereotype]] sind Erweiterungsmechanismen des [[Meta-Modell|Meta-Modells]] in der [[UML]], die es ermöglichen, bestehende [[Modellelement|Modellelemente]] mit zusätzlichen, domänenspezifischen [[Eigenschaft|Eigenschaften]] und [[Bedingung|Bedingungen]] zu versehen. Sie definieren Unterklassen existierender Meta-Modell-Elemente und erweitern so die [[Ausdrucksstärke]] der [[Modellierungssprache]], ohne deren Grundstruktur zu verändern.
- **Nutzen & Zweck:** [[Stereotype|Stereotype]] lösen das Problem der begrenzten Standardausdrucksmöglichkeiten der [[UML]], indem sie eine flexible Anpassung an spezifische [[Domäne|Domänen]] oder technische [[Anforderung|Anforderungen]] ermöglichen. Sie schaffen Klarheit und Präzision in [[Modell|Modellen]], indem sie [[Modellelement|Modellelemente]] mit zusätzlichen [[Semantik|Semantiken]] versehen, die über die Standard-UML-Notation hinausgehen. Dadurch wird die [[Modellierung]] komplexer [[System|Systeme]] erleichtert, die [[Kommunikation]] im [[Entwicklerteam]] verbessert und die [[Wiederverwendbarkeit]] von [[Entwurfsmuster|Entwurfsmustern]] gefördert. Typische Anwendungsfälle umfassen [[Persistenz]], [[Sicherheit]], [[Verteilung]] oder domänenspezifische [[Architektur|Architekturen]].
- **Abgrenzung & Grenzen:** [[Stereotype|Stereotype]] sollten nicht genutzt werden, wenn die Standard-UML-Elemente bereits ausreichen, um das [[Modell]] klar und verständlich darzustellen. Übermäßiger Einsatz kann zu unübersichtlichen [[Modell|Modellen]] führen, die [[Komplexität]] erhöhen und die [[Lesbarkeit]] beeinträchtigen. Alternativen wie die Nutzung von [[Kommentar|Kommentaren]] oder die Definition eigener [[Meta-Modell|Meta-Modelle]] sind in solchen Fällen vorzuziehen. [[Stereotype|Stereotype]] unterscheiden sich von einfachen [[Anmerkung|Anmerkungen]] dadurch, dass sie formal in das [[Meta-Modell]] eingebunden sind und somit eine präzise, wiederverwendbare Erweiterung darstellen. Sie sollten nicht mit [[Profil|Profilen]] verwechselt werden, die eine Sammlung verwandter [[Stereotype|Stereotypen]] und [[Einschränkung|Einschränkungen]] kapseln.
- **Beispiel / Code:** ```java
// Beispiel für einen Stereotypen <<persistent>> in Java-Annotation
@Persistent(tableName = "Mitglied")
public class Mitglied {
    private String name;
    @Id
    private Integer mitgliedId;
}

// Beispiel für ein UML-Klassendiagramm mit Stereotypen
<<Database>>
class Mitglied {
    +tableName: String [1]
    -mitgliedId: Integer {id > 0}
    #adresse: [[Anschrift]]
    ~leistung: Integer = 1 {leistung > 0 and leistung < 1441}
    +leistungsprognose(datum: Date): Integer
}

<<metaclass>>
class Comp {
    // Definition eines eigenen Stereotyps für [[Komponente|Komponenten]]
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4d
- **Vorgänger / Parent:** [[UML-Klassendiagramm]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Eigene_Stereotype]]
