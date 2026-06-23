---
id: b93bb7e8-9787-4df8-a9d8-cdd1f94ae788
title: "Substantivmethode"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Substantivmethode]]

- **Kernkonzept:** Die Substantivmethode ist ein analytisches Verfahren im Software-Engineering, bei dem Substantive in Use-Case-Beschreibungen und Anforderungen identifiziert werden, um Kandidaten für Konzepte und Entitäten der Problemdomäne zu ermitteln. Sie dient als systematischer Ansatz zur Objektfindung in der Analysephase.
- **Nutzen & Zweck:** Die Substantivmethode existiert, um die Identifikation relevanter Objekte und Konzepte in der Problemdomäne zu strukturieren und zu beschleunigen. Sie löst das Problem, dass Entwickler ohne methodische Unterstützung wichtige Entitäten übersehen oder falsch klassifizieren könnten. Durch die Fokussierung auf sprachliche Elemente (Substantive) wird eine vollständige und nachvollziehbare Grundlage für das Analyse-Objektmodell geschaffen, was die spätere Modellierung und Implementierung erleichtert.
- **Abgrenzung & Grenzen:** Die Substantivmethode sollte nicht isoliert angewendet werden, da nicht jedes Substantiv ein relevantes Konzept darstellt (z. B. abstrakte Begriffe, Quantitäten oder Attribute). Sie unterscheidet sich von der Checklistenmethode, die auf vordefinierte Kategorien (wie Rollen, Ereignisse) setzt, indem sie sprachliche Muster nutzt. Die Methode ist ungeeignet, wenn Use-Case-Beschreibungen unvollständig oder mehrdeutig sind, da dies zu falschen oder redundanten Konzepten führen kann. Zudem ersetzt sie keine domänenspezifische Expertise oder iterative Validierung der Ergebnisse.
- **Beispiel / Code:** ```java
// Beispiel: Substantive aus einem Use-Case extrahieren (pseudocode)
// Use-Case-Beschreibung: "Ein Mitglied meldet sich für einen Kurs an und erhält eine Bestätigungsmail."

List<String> substantive = extractSubstantive("Mitglied", "Kurs", "Bestätigungsmail");

// Kandidaten für Konzepte/Entitäten:
class Mitglied {
    private String name;
    private List<Kurs> angemeldeteKurse;
}

class Kurs {
    private String bezeichnung;
    private List<Mitglied> teilnehmer;
}

class Bestätigungsmail {
    private String inhalt;
    private Mitglied empfänger;
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2a1b
- **Vorgänger / Parent:** [[Klassenkandidat]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Fachkonzept]]
