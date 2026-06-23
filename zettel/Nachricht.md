---
id: 435a3527-83dc-4bb5-9391-9aed7b1bf2c0
title: "Nachricht"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_09"
---

# [[Nachricht]]

- **Kernkonzept:** Eine 'Nachricht' im Kontext der UML-Modellierung und Software-Engineering bezeichnet ein Kommunikationselement, das den Informationsaustausch zwischen Objekten oder Akteuren in einem System beschreibt. Sie repräsentiert eine Interaktion, die eine Aktion auslöst oder Daten übermittelt.
- **Nutzen & Zweck:** Das Konzept der 'Nachricht' existiert, um die dynamischen Abläufe und Interaktionen innerhalb eines Softwaresystems formal abzubilden. Es löst das Problem, wie Objekte miteinander kommunizieren und welche Operationen durch diese Kommunikation angestoßen werden. Dadurch wird die Grundlage für die Erstellung von System-Sequenz-Diagrammen und die Identifikation von Schnittstellen geschaffen, was essenziell für das Verständnis der Systemdynamik und die spätere Implementierung ist.
- **Abgrenzung & Grenzen:** Eine 'Nachricht' sollte nicht genutzt werden, wenn es um die statische Struktur eines Systems geht, wie z. B. die Definition von Klassen oder Attributen. Sie unterscheidet sich von Konzepten wie 'Operation' oder 'Methode', da diese die Implementierung einer Aktion beschreiben, während eine 'Nachricht' den Akt der Kommunikation selbst darstellt. Zudem ist sie kein Ersatz für Zustandsübergänge, die das Verhalten eines einzelnen Objekts über die Zeit modellieren. Nachrichten sind auch nicht geeignet, um nicht-funktionale Anforderungen wie Performance oder Sicherheit abzubilden.
- **Beispiel / Code:** ```java
// Beispiel für eine Nachricht in einem Sequenzdiagramm (pseudocode-artig)
Mitglied mitglied = new Mitglied("Max Mustermann");
Abteilung abteilung = new Abteilung("Entwicklung");

// Nachricht: Ein Mitglied tritt einer Abteilung bei
mitglied.abteilungBeitreten(abteilung);

// Die Methode 'abteilungBeitreten' könnte intern eine Nachricht an die Abteilung senden
abteilung.neuesMitgliedHinzufuegen(mitglied);
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3
- **Vorgänger / Parent:** [[System-Sequenz-Diagramm]]
- **Folgezettel / Unterzettel:**
  - [[Synchrone_Nachricht]]
  - [[Asynchrone_Nachricht]]
- **Querverweise:**
  - [[UML]]
  - [[Kommunikationsmodell]]
