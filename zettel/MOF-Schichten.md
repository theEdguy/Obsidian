---
id: e9fa942b-4318-4dc2-85d9-c9bf06f778f5
title: "MOF-Schichten"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[MOF-Schichten]]

- **Kernkonzept:** MOF-Schichten (Meta-Object Facility) strukturieren Modellierungssprachen wie UML in vier hierarchische Ebenen, um die Definition, Erweiterung und Anwendung von Metamodellen und Modellen systematisch zu ermöglichen. Jede Schicht beschreibt die Regeln und Elemente der darunterliegenden Ebene.
- **Nutzen & Zweck:** Das MOF-Konzept löst das Problem der Konsistenz und Erweiterbarkeit von Modellierungssprachen, indem es eine klare Trennung zwischen Metamodellen (z. B. UML-Syntax) und konkreten Modellen (z. B. Klassendiagramme) schafft. Es ermöglicht die formale Definition von Sprachen, deren Anpassung an domänenspezifische Anforderungen und die Wiederverwendung von Modellierungselementen, ohne die Grundprinzipien der Sprache zu verletzen.
- **Abgrenzung & Grenzen:** MOF-Schichten sollten nicht genutzt werden, wenn einfache, informelle Modellierungsansätze ausreichen oder wenn der Overhead der Metamodellierung für kleine Projekte unverhältnismäßig ist. Alternativen wie ad-hoc-Diagramme oder domänenspezifische Sprachen (DSLs) ohne Meta-Modell-Unterstützung sind flexibler, aber weniger standardisiert und schwerer erweiterbar. MOF eignet sich nicht für Echtzeit- oder Low-Level-Systeme, die keine abstrakte Modellierung erfordern.
- **Beispiel / Code:** ```java
// Beispiel: MOF-Schichten in UML-Notation (vereinfacht)
// M3 (Meta-Meta-Modell): Definiert Elemente wie 'Klasse' oder 'Attribut'
MetaClass Klasse {
    name: String;
    attribute: Attribut[0..*];
}

// M2 (Meta-Modell): Instanz von M3, z. B. UML-Klassendiagramm-Syntax
class Mitglied {
    +name: String;
    -alter: int;
}

// M1 (Modell): Instanz von M2, konkretes Klassendiagramm
class VereinMitglied extends Mitglied {
    leistung: int = 0;
}

// M0 (Objektebene): Instanz von M1, reales Objekt
VereinMitglied thomas = new VereinMitglied("Thomas", 30, 1051);
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 5a
- **Vorgänger / Parent:** [[Meta-Modell]]
- **Folgezettel / Unterzettel:**
  - [[Meta-Meta-Modell]]
  - [[Meta-Modell]]
  - [[Modell]]
  - [[Reale_Objekte]]
- **Querverweise:** keine
