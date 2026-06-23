---
id: 45d96552-c86e-43bb-bf03-f9010e8ca25d
title: "Abbruch"
date: 2026-06-23
tags:
  - software_engineering
  - uml-fragment
  - kontrollfluss
  - draft
source: "software_engineering_kapitel_13"
---

# [[Abbruch]]

- **Kernkonzept:** Ein 'Abbruch' in UML-Interaktionsdiagrammen ist ein Fragment, das den vorzeitigen Abbruch eines Ablaufs innerhalb eines Sequenzdiagramms darstellt, sobald eine bestimmte Bedingung erfüllt ist. Es beendet die Ausführung des umschließenden Fragments oder der gesamten Interaktion sofort.
- **Nutzen & Zweck:** Das Abbruch-Fragment existiert, um Ausnahme- oder Fehlerfälle in dynamischen Abläufen modellieren zu können, bei denen eine weitere Ausführung des Prozesses nicht sinnvoll oder möglich ist. Es löst das Problem, komplexe Abbruchlogik übersichtlich und standardisiert in Sequenzdiagrammen abzubilden, ohne den Kontrollfluss unnötig zu verkomplizieren. Dadurch wird die Lesbarkeit und Präzision der Modellierung erhöht.
- **Abgrenzung & Grenzen:** Ein Abbruch sollte nicht genutzt werden, wenn der Ablauf regulär fortgesetzt werden kann oder alternative Pfade existieren, die keine sofortige Beendigung erfordern. Im Gegensatz zu 'opt' (optional) oder 'alt' (alternativ) beendet ein Abbruch-Fragment die Interaktion vollständig und nicht nur einen Teilzweig. Es unterscheidet sich von 'break', das nur das umschließende Fragment verlässt, während 'Abbruch' die gesamte Interaktion terminiert. Bei einfachen Bedingungen ohne kritische Fehler ist ein alternatives Fragment wie 'opt' oft besser geeignet.
- **Beispiel / Code:** ```java
// Beispiel für ein Abbruch-Fragment in einem Sequenzdiagramm (pseudocode-artige Darstellung)
interaction BestellungAufgeben() {
    Kunde -> Bestellsystem: bestellungAufgeben(artikel)
    alt [artikelVerfuegbar]
        Bestellsystem -> Lager: pruefeBestand(artikel)
        Lager -> Bestellsystem: bestandOk()
        Bestellsystem -> Zahlungssystem: verarbeiteZahlung()
    else [artikelNichtVerfuegbar]
        break [abbruchBedingung: "Artikel nicht vorrätig"]
        Bestellsystem -> Kunde: benachrichtigeFehler("Artikel nicht verfügbar")
    end
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1c5
- **Vorgänger / Parent:** [[Nachrichtenfragment]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
