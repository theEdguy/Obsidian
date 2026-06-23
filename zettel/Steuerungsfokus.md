---
id: 24752c8b-cdea-4d22-97c0-8c8b42cf0630
title: "Steuerungsfokus"
date: 2026-06-23
tags:
  - software_engineering
  - uml-element
  - interaktion
  - draft
source: "software_engineering_kapitel_13"
---

# [[Steuerungsfokus]]

- **Kernkonzept:** Der Steuerungsfokus (Activation) in UML-Sequenzdiagrammen visualisiert den Zeitraum, in dem ein Objekt eine Methode ausführt oder auf eine Nachricht wartet. Er zeigt an, wann ein Objekt aktiv an der Interaktion beteiligt ist und Verantwortung für die Verarbeitung übernimmt.
- **Nutzen & Zweck:** Der Steuerungsfokus dient dazu, die zeitliche Abfolge und Dauer von Methodenaufrufen in einer Objektinteraktion klar darzustellen. Er löst das Problem, dass statische Diagramme ohne zeitliche Dimension schwer verständlich sind, indem er dynamische Abläufe wie Verschachtelung, Rekursion oder parallele Ausführung sichtbar macht. Dies erleichtert das Verständnis von Kontrollflüssen und hilft bei der Identifikation von Engpässen oder ineffizienten Aufrufstrukturen.
- **Abgrenzung & Grenzen:** Der Steuerungsfokus sollte nicht genutzt werden, wenn die zeitliche Abfolge von Interaktionen irrelevant ist oder wenn das Diagramm bereits durch zu viele Details überladen ist. Im Gegensatz zu Kommunikationsdiagrammen, die die strukturelle Verbindung von Objekten betonen, liegt der Fokus hier auf der zeitlichen Dimension – was bei rein logischen oder räumlichen Beziehungen weniger aussagekräftig ist. Für einfache Abläufe ohne verschachtelte Aufrufe kann der Steuerungsfokus zudem redundant wirken und die Lesbarkeit beeinträchtigen.
- **Beispiel / Code:** ```java
// Beispiel: Sequenzdiagramm-Ausschnitt mit Steuerungsfokus (textuelle Notation)
participant Kunde
participant BestellSystem
participant Lager

Kunde -> BestellSystem: bestelleArtikel(artikelId)
activate BestellSystem  // Steuerungsfokus beginnt
    BestellSystem -> Lager: prüfeVerfügbarkeit(artikelId)
    activate Lager        // Verschachtelter Steuerungsfokus
    Lager --> BestellSystem: verfügbar
    deactivate Lager      // Steuerungsfokus endet
    BestellSystem -> Lager: reserviereArtikel(artikelId)
deactivate BestellSystem  // Steuerungsfokus endet
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1b
- **Vorgänger / Parent:** [[Sequenzdiagramm]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
