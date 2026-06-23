---
id: a11be98f-bb54-483f-b646-62c3f4dd8697
title: "Interaktionsfragment"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_09"
---

# [[Interaktionsfragment]]

- **Kernkonzept:** Ein Interaktionsfragment in der UML-Modellierung ist ein strukturiertes Element innerhalb eines Sequenzdiagramms, das spezielle Ablaufmuster wie Alternativen, Optionen oder Iterationen kapselt. Es dient zur Darstellung komplexer Kontrollflüsse zwischen Objekten oder Akteuren.
- **Nutzen & Zweck:** Interaktionsfragmente existieren, um nicht-lineare oder bedingte Abläufe in Systeminteraktionen präzise und übersichtlich abzubilden. Sie lösen das Problem, dass einfache Sequenzdiagramme ohne Fragmente keine Verzweigungen, Schleifen oder optionale Schritte darstellen können, was für die Modellierung realer Anwendungsfälle essenziell ist.
- **Abgrenzung & Grenzen:** Interaktionsfragmente sollten nicht genutzt werden, wenn der Ablauf streng linear und ohne Verzweigungen oder Wiederholungen verläuft – hier reichen einfache Nachrichtenfolgen. Alternativen wie Aktivitätsdiagramme eignen sich besser für komplexe Workflows mit vielen parallelen Pfaden, während Interaktionsfragmente auf die Interaktion zwischen wenigen Objekten fokussieren.
- **Beispiel / Code:** ```java
// Beispiel: UML-Sequenzdiagramm mit Interaktionsfragment (alt für Alternative)
// Pseudocode-Darstellung der Logik:
if (mitglied.istAktiv()) {
    mitglied.abteilungVerlassen(abteilung);
} else {
    system.fehlerMelden("Mitglied inaktiv");
}
```

// In UML-Notation würde das Fragment 'alt' die beiden Zweige umschließen.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1
- **Vorgänger / Parent:** [[System-Sequenz-Diagramm]]
- **Folgezettel / Unterzettel:**
  - [[Alternativfragment]]
  - [[Optionalfragment]]
  - [[Iterationsfragment]]
- **Querverweise:**
  - [[UML]]
  - [[Ablaufkontrolle]]
