---
id: f359fd18-ebe3-4ac9-b779-d5825038fdfa
title: "Pin"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - uml
  - datenfluss
  - draft
source: "software_engineering_kapitel_08"
---

# [[Pin]]

- **Kernkonzept:** Ein Pin in UML-Aktivitätsdiagrammen ist ein fortgeschrittenes Modellierungselement, das den Datenfluss zwischen Aktionen präzise steuert, indem es Ein- und Ausgabeparameter einer Aktion als explizite Knoten darstellt. Pins ermöglichen die Spezifikation von Datentypen und Multiplizitäten für die übergebenen Daten.
- **Nutzen & Zweck:** Pins lösen das Problem der unklaren oder impliziten Datenübergabe zwischen Aktionen in Aktivitätsdiagrammen. Sie schaffen Transparenz über die erforderlichen Eingabedaten und die produzierten Ausgabedaten einer Aktion, was die Nachvollziehbarkeit und Präzision der Modellierung erhöht. Besonders in komplexen Abläufen mit vielen Datenflüssen verhindern Pins Missverständnisse und unterstützen die Konsistenzprüfung zwischen verschiedenen Modellierungsebenen.
- **Abgrenzung & Grenzen:** Pins sollten nicht genutzt werden, wenn der Datenfluss trivial oder offensichtlich ist, da sie die Komplexität des Diagramms unnötig erhöhen. Alternativen wie einfache Objektknoten oder textuelle Beschreibungen reichen oft aus, um den Datenfluss in einfachen Szenarien darzustellen. Pins unterscheiden sich von Objektknoten durch ihre direkte Bindung an Aktionen und die Möglichkeit, Datentypen und Multiplizitäten explizit zu definieren. Sie sind weniger geeignet für die Modellierung von Kontrollflüssen oder nicht-datenbezogenen Abhängigkeiten.
- **Beispiel / Code:** ```java
// Beispiel: Aktivitätsdiagramm mit Pins (konzeptionell als UML-Notation)
// Aktion: "Mitglied anlegen"
// Eingabe-Pin: "Mitgliedsdaten" (Typ: Mitglied, Multiplizität: 1)
// Ausgabe-Pin: "Mitglieds-ID" (Typ: Integer, Multiplizität: 1)

// UML-Notation (textuell):
Aktion MitgliedAnlegen {
    Eingabe-Pin Mitgliedsdaten : Mitglied [1];
    Ausgabe-Pin MitgliedsID : Integer [1];
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a5b
- **Vorgänger / Parent:** [[Objektknoten]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
