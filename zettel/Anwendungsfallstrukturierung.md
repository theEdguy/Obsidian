---
id: 51187926-c9d6-4aa0-8085-eb2fc44a8367
title: "Anwendungsfallstrukturierung"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - modellierung
  - draft
source: "software_engineering_kapitel_08"
---

# [[Anwendungsfallstrukturierung]]

- **Kernkonzept:** Anwendungsfallstrukturierung ist ein zentrales Konzept der objektorientierten Analyse und Modellierung, bei dem Use Cases identifiziert, gegliedert und in Beziehung zueinander gesetzt werden, um die funktionalen Anforderungen eines Systems systematisch zu erfassen und zu organisieren.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Komplexität von Software-Systemen beherrschbar zu machen, indem es eine klare Struktur für die funktionalen Anforderungen schafft. Es löst das Problem, dass ungeordnete oder unvollständige Anforderungen zu Missverständnissen, Lücken in der Implementierung oder inkonsistenten Systemverhalten führen. Durch die Strukturierung wird die Kommunikation zwischen Stakeholdern verbessert, die Traceability von Anforderungen sichergestellt und die Grundlage für eine systematische Umsetzung gelegt.
- **Abgrenzung & Grenzen:** Anwendungsfallstrukturierung sollte nicht genutzt werden, wenn das System sehr einfach ist oder keine klaren funktionalen Anforderungen hat, da der Aufwand dann unverhältnismäßig hoch wäre. Sie unterscheidet sich von rein textuellen Anforderungsdokumenten durch ihre visuelle und relationale Darstellung, die Abhängigkeiten und Wechselwirkungen zwischen Use Cases verdeutlicht. Alternativen wie User Stories (z. B. in Scrum) sind weniger formal und eignen sich eher für agile, iterative Entwicklungsprozesse, während Anwendungsfallstrukturierung eine umfassendere und detailliertere Analyse ermöglicht.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache Use-Case-Strukturierung in UML-ähnlicher Notation (als Text)
// Akteur: Mitglied
// Use Case: Mitglied verwalten
//   - Unter-Use Cases:
//     1. Mitglied anlegen
//     2. Mitglied bearbeiten
//     3. Mitglied löschen
//     4. Mitgliedsdaten abfragen
// Beziehungen:
//   - <<include>> Mitglied anlegen -> Adresse validieren
//   - <<extend>> Mitglied löschen -> Benachrichtigung senden (optional)
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 8
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Use_Case_Hierarchie]]
  - [[Use_Case_Beziehungen]]
- **Querverweise:**
  - [[Use_Case]]
  - [[Anwendungsfallanalyse]]
