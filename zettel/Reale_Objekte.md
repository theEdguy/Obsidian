---
id: 6df9ff23-f0b6-42e2-9cb2-5c0c5ab27079
title: "Reale Objekte"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Reale Objekte]]

- **Kernkonzept:** Reale Objekte bezeichnen konkrete, greifbare Instanzen in der Softwaremodellierung, die auf der untersten Ebene (M0) des Meta-Modells angesiedelt sind. Sie repräsentieren physische oder logische Entitäten wie Datenbankeinträge, Programmobjekte oder Nutzerdaten, die aus Modellen (M1) abgeleitet werden und in der realen Welt oder im System existieren.
- **Nutzen & Zweck:** Das Konzept der realen Objekte dient dazu, die Lücke zwischen abstrakten Modellen (z. B. UML-Klassendiagrammen) und der tatsächlichen Implementierung zu schließen. Es ermöglicht die Validierung von Modellen durch konkrete Beispiele und stellt sicher, dass die entworfenen Strukturen (Klassen, Attribute, Beziehungen) in der Praxis umsetzbar sind. Zudem unterstützt es die Kommunikation zwischen Entwicklern und Stakeholdern, indem es abstrakte Konzepte durch reale Instanzen veranschaulicht.
- **Abgrenzung & Grenzen:** Reale Objekte sollten nicht mit Modellen (M1) oder Meta-Modellen (M2) verwechselt werden, da sie keine abstrakten Beschreibungen, sondern konkrete Ausprägungen darstellen. Sie sind ungeeignet für die Definition von Systemstrukturen oder Regeln, da diese auf höheren Abstraktionsebenen (z. B. Klassendiagramme) erfolgen muss. Zudem sind reale Objekte domänenspezifisch und können nicht universell für alle Systeme gelten, was ihre Wiederverwendbarkeit einschränkt. Alternativen wie Instanzdiagramme bieten eine formalere Darstellung, sind jedoch weniger flexibel für ad-hoc-Analysen.
- **Beispiel / Code:** ```java
// Beispiel für ein reales Objekt (M0) als Instanz der Klasse 'Mitglied' (M1)
Mitglied mustermann = new Mitglied();
mustermann.setName("Max Mustermann");
mustermann.setAdresse("Musterstraße 1, 12345 Musterstadt");
mustermann.setLeistung(1051);

// Das Objekt 'mustermann' repräsentiert eine konkrete Instanz der Klasse 'Mitglied'
// und entspricht einem realen Datensatz in einer Datenbank oder einem Programm.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 5a4
- **Vorgänger / Parent:** [[MOF-Schichten]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
