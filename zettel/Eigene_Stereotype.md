---
id: c0ffc668-e0d5-4231-b181-e0546219225b
title: "Eigene Stereotype"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Eigene Stereotype]]

- **Kernkonzept:** Eigene Stereotype in UML sind benutzerdefinierte Erweiterungen des UML-Meta-Modells, die spezifische Modellierungselemente mit besonderer Semantik oder Domänenbezügen kennzeichnen. Sie ermöglichen die Anpassung der UML an fachliche oder technische Anforderungen, ohne die Standardnotation zu verändern.
- **Nutzen & Zweck:** Eigene Stereotype lösen das Problem der begrenzten Ausdrucksmöglichkeiten der Standard-UML für domänenspezifische oder projektbezogene Anforderungen. Sie erlauben die präzise Kennzeichnung von Modellelementen (z. B. Klassen, Attribute) mit zusätzlicher Bedeutung, wie spezielle Rollen, Verantwortlichkeiten oder technische Eigenschaften, und verbessern so die Lesbarkeit und Konsistenz von Modellen in komplexen Projekten.
- **Abgrenzung & Grenzen:** Eigene Stereotype sollten nicht genutzt werden, wenn Standard-UML-Elemente die Anforderungen bereits ausreichend abdecken, da sie die Komplexität erhöhen und Spezialwissen erfordern. Sie unterscheiden sich von vordefinierten Stereotypen (z. B. <<interface>>) durch ihre projektspezifische Definition und sollten sparsam eingesetzt werden, um die Verständlichkeit für externe Betrachter nicht zu beeinträchtigen. Alternativen sind die Nutzung von Properties oder Kommentaren, falls keine formale Erweiterung nötig ist.
- **Beispiel / Code:** ```java
// UML-Klassendiagramm mit eigenem Stereotyp <<Database>>
<<Database>>
class Mitglied {
    +tableName: String [1]
    -mitgliedId: Integer
    +name: String
    -adresse: Anschrift
    ~{static} SQLFile: String
}
```

// Erklärung: Der Stereotyp <<Database>> kennzeichnet die Klasse als Datenbanktabelle,
// während das Property {static} das Attribut SQLFile als klassenbezogen markiert.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4d1
- **Vorgänger / Parent:** [[Stereotype]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
