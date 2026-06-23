---
id: 5b51aedb-5317-480c-a738-4b0773c7e52a
title: "Analyse-Use-Case-Modell"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - anforderungen
  - draft
source: "software_engineering_kapitel_06"
---

# [[Analyse-Use-Case-Modell]]

- **Kernkonzept:** Das Analyse-Use-Case-Modell ist eine Methode zur strukturierten Erfassung und Beschreibung der funktionalen Anforderungen an ein Softwaresystem aus der Perspektive der Anwender. Es bildet zentrale Abläufe (Geschäftsvorfälle) in Form von Szenarien ab und setzt diese zueinander in Beziehung, um den Problemraum zu definieren.
- **Nutzen & Zweck:** Das Analyse-Use-Case-Modell existiert, um die Anforderungen eines Systems klar und verständlich zu dokumentieren, bevor mit der technischen Umsetzung begonnen wird. Es löst das Problem, dass Entwickler, Auftraggeber und Stakeholder unterschiedliche Vorstellungen von der zu realisierenden Funktionalität haben, indem es die Kernprozesse des Systems aus Anwendersicht formalisiert. Dadurch wird die Kommunikation verbessert, Missverständnisse reduziert und eine solide Grundlage für die weitere Analyse und das Design geschaffen.
- **Abgrenzung & Grenzen:** Das Analyse-Use-Case-Modell sollte nicht genutzt werden, wenn es um die detaillierte technische Spezifikation oder die Implementierung von Systemkomponenten geht, da es sich auf die funktionale Sicht der Anwender konzentriert und keine Lösungsdetails beschreibt. Es unterscheidet sich von Alternativen wie User Stories (agile Entwicklung) durch seinen formaleren Ansatz und die stärkere Betonung von Szenarien und Beziehungen zwischen Use Cases. Für nicht-funktionale Anforderungen oder technische Constraints sind andere Methoden wie das Lastenheft oder Qualitätsmetriken besser geeignet.
- **Beispiel / Code:** ```java
// Beispiel: Use-Case-Diagramm (UML-Notation) als textuelle Beschreibung
@startuml
actor Mitglied
actor Administrator

usecase "Mitgliedsdaten ändern" as UC1
usecase "Mitglied anlegen" as UC2
usecase "Beitragszahlung erfassen" as UC3

Mitglied --> UC1
Mitglied --> UC2
Administrator --> UC1
Administrator --> UC2
Administrator --> UC3

UC1 .> UC3 : <<include>>
@enduml
```

// Alternativ: Kurze textuelle Beschreibung eines Use Cases
**Use Case:** Mitgliedsdaten ändern
**Akteur:** Mitglied, Administrator
**Beschreibung:**
1. Der Akteur wählt die Option "Mitgliedsdaten ändern".
2. Das System zeigt die aktuellen Daten des Mitglieds an.
3. Der Akteur ändert die gewünschten Daten (z. B. Adresse, E-Mail).
4. Das System validiert die Eingaben und speichert die Änderungen.
5. Das System bestätigt die erfolgreiche Aktualisierung.
**Ausnahmen:**
- Ungültige Eingaben: Das System zeigt eine Fehlermeldung an und fordert zur Korrektur auf.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a4a
- **Vorgänger / Parent:** [[Use-Case-Modellierung]]
- **Folgezettel / Unterzettel:**
  - [[Akteure_definieren]]
  - [[Szenarien_beschreiben]]
  - [[Use-Case-Diagramme_erstellen]]
- **Querverweise:** keine
