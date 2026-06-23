---
id: f5db32d5-d77a-4dd0-96a6-377bd74b0bb0
title: "Listenkfeld"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Listenkfeld]]

- **Kernkonzept:** Ein Listenkfeld (List Compartment) in UML-Klassendiagrammen ist ein Bereich innerhalb einer Klasse, der strukturierte Informationen wie Attribute, Operationen oder andere Gruppierungen übersichtlich darstellt. Es dient der detaillierten Spezifikation von Klasseneigenschaften und -verhalten.
- **Nutzen & Zweck:** Das Listenkfeld ermöglicht eine klare und systematische Darstellung der internen Struktur einer Klasse, indem es Attribute und Operationen logisch gruppiert und deren Sichtbarkeit, Datentypen sowie weitere Eigenschaften präzise dokumentiert. Es löst das Problem der unübersichtlichen oder unstrukturierten Beschreibung von Klassenmerkmalen und fördert die Verständlichkeit sowie Wartbarkeit von Modellen, insbesondere in komplexen Software-Systemen.
- **Abgrenzung & Grenzen:** Ein Listenkfeld sollte nicht genutzt werden, wenn die Klasse keine internen Details preisgeben soll, beispielsweise bei reinen Schnittstellen (Interfaces) oder abstrakten Klassen mit Fokus auf externem Verhalten. Alternativ kann das Namensfeld (Name Compartment) allein ausreichen, wenn nur der Klassenname relevant ist. Zudem ist das Listenkfeld ungeeignet für die Darstellung dynamischer Aspekte wie Objektzustände oder Interaktionen, wofür stattdessen Instanzdiagramme oder Sequenzdiagramme verwendet werden sollten.
- **Beispiel / Code:** ```java
// UML-Klassendarstellung mit Listenkfeld
class Mitglied {
    // Namensfeld (Name Compartment)
    
    // Listenkfeld (Attribute)
    +name: String
    -alter: Date
    #adresse: Anschrift
    ~leistung: Integer = 1 {leistung > 0 and leistung < 1441}
    
    // Listenkfeld (Operationen)
    +leistungsprognose(datum: Date): Integer
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a2
- **Vorgänger / Parent:** [[Klassenkompartimente]]
- **Folgezettel / Unterzettel:**
  - [[Attribute]]
  - [[Operationen]]
- **Querverweise:** keine
