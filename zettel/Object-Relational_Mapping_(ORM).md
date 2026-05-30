---
id: 6405bcb0-bf1f-406b-97d5-d1cb60cc8c9b
title: "Object-Relational_Mapping_(ORM)"
date: 2026-05-30
tags:
  - software_engineering
  - datenbank
  - persistenz
  - draft
source: "SWE Slides (Folien 376-388)"
---

# [[Object-Relational_Mapping_(ORM)]]

- **Kernkonzept:** [[Object-Relational_Mapping_(ORM)|ORM]] ist eine Technik, die [[Datenbanktabelle|Datenbanktabellen]] auf [[Klasse|Klassen]] und [[Datenbankzeile|Datenbankzeilen]] auf [[Objekt|Objekte]] abbildet. Sie ermöglicht die [[Manipulation]] von [[Datenbank]]-Daten mit [[Objektorientierte_Programmierung|objektorientierten]] Mitteln.
- **Nutzen & Zweck:** Es löst das [[Problem]] der [[Impedanzfehlanpassung]] zwischen [[Relationale_Datenbank|relationalen Datenbanken]] und [[Objektorientierte_Programmierung|objektorientierten Programmiersprachen]], indem es eine [[Abstraktionsschicht]] für den [[Datenbankzugriff]] bereitstellt.
- **Abgrenzung & Grenzen:** Nicht geeignet für Anwendungen mit sehr spezifischen [[Datenbankanforderung|Datenbankanforderungen]] oder hohen [[Performance]]-Anforderungen, da [[ORM]]-Frameworks oft [[Overhead]] verursachen. Alternativen wie [[Native_Queries]] oder [[Stored_Procedures]] können hier besser performen.
- **Beispiel / Code:** ```java
// Beispiel für eine ORM-Annotation (JPA/Hibernate)
@Entity
@Table(name = "members")
public class Member {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String name;
    // Getter und Setter
}
```
