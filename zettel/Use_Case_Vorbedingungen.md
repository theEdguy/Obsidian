---
id: f8305c0f-8c8a-4ebe-b734-091c6321eac9
title: "Use Case Vorbedingungen"
date: 2026-06-23
tags:
  - software_engineering
  - vorbedingungen
  - anforderungen
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Vorbedingungen]]

- **Kernkonzept:** Vorbedingungen in Use Cases definieren die notwendigen Zustände oder Voraussetzungen, die erfüllt sein müssen, bevor ein Use Case ausgeführt werden kann. Sie legen fest, unter welchen Bedingungen der Ablauf des Use Cases gültig und sinnvoll ist.
- **Nutzen & Zweck:** Vorbedingungen dienen dazu, die Konsistenz und Korrektheit von Use Cases sicherzustellen, indem sie klare Rahmenbedingungen für deren Ausführung schaffen. Sie verhindern Missverständnisse zwischen Entwicklern, Testern und Stakeholdern, indem sie explizit festhalten, welche Systemzustände oder Vorbereitungen erforderlich sind. Dadurch wird die Nachvollziehbarkeit erhöht und das Risiko von Fehlern in der Implementierung oder im Test reduziert.
- **Abgrenzung & Grenzen:** Vorbedingungen sollten nicht mit Nachbedingungen oder Schritten innerhalb des Use Cases verwechselt werden. Sie beschreiben keine Abläufe, sondern ausschließlich Voraussetzungen. Bei zu detaillierten oder technischen Vorbedingungen besteht die Gefahr, dass sie die Lesbarkeit des Use Cases beeinträchtigen oder zu stark in Implementierungsdetails abgleiten. Alternativen wie implizite Annahmen oder separate Dokumentation sind ungeeignet, wenn klare, überprüfbare Bedingungen benötigt werden.
- **Beispiel / Code:** ```java
// Beispiel für eine Vorbedingung in einem Use Case (textuelle Beschreibung)
UseCase: "Mitglied bearbeiten"
Systemgrenze: MyClub
Akteure: Vereinsmanager
Prio: 1
Vorbedingung: "MyClub ist korrekt installiert und der Vereinsmanager hat sich erfolgreich authentisiert."
Beschreibung: Der Vereinsmanager wählt ein Mitglied aus und bearbeitet dessen Daten.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b6
- **Vorgänger / Parent:** [[Use_Case_Struktur]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case]]
  - [[Anforderungsanalyse]]
