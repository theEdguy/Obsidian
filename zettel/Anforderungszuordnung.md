---
id: 341d8f21-0171-469f-a65c-537ca76ab3c4
title: "Anforderungszuordnung"
date: 2026-06-23
tags:
  - software_engineering
  - anforderungen
  - zuordnung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Anforderungszuordnung]]

- **Kernkonzept:** Anforderungszuordnung bezeichnet die systematische Verknüpfung jeder funktionalen und nicht-funktionalen Anforderung an ein Softwaresystem mit mindestens einem Use Case, um deren Erfüllung und Relevanz im Entwicklungsprozess sicherzustellen.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Traceability zwischen Anforderungen und der Systemgestaltung herzustellen. Es löst das Problem, dass Anforderungen im Entwicklungsprozess verloren gehen oder ihre Umsetzung nicht nachvollziehbar ist. Durch die Zuordnung wird gewährleistet, dass jede Anforderung in der Architektur, Implementierung und im Testing berücksichtigt wird, was die Vollständigkeit und Konsistenz des Systems erhöht.
- **Abgrenzung & Grenzen:** Anforderungszuordnung sollte nicht genutzt werden, wenn das Projekt zu klein oder trivial ist, sodass der Aufwand der Dokumentation den Nutzen übersteigt. Es unterscheidet sich von unstrukturierten Anforderungslisten, da es eine explizite Verbindung zu Use Cases herstellt und nicht nur eine isolierte Sammlung von Anforderungen darstellt. Alternativen wie User Stories (in agilen Methoden) fokussieren sich stärker auf Nutzerwert und sind weniger formal, bieten aber keine vergleichbare systematische Nachverfolgbarkeit.
- **Beispiel / Code:** ```java
// Beispiel: Use-Case-Beschreibung mit Anforderungsreferenzen
UseCase MitgliederVerwalten = new UseCase(
    name: "Mitglieder verwalten",
    systemgrenze: "MyClub",
    akteure: ["Vereinsmanager", "Mail Client"],
    prioritaet: 1,
    anforderungen: ["F1.1", "F1.2", "F2.1"], // Explizite Zuordnung der Anforderungen
    beschreibung: "Der Vereinsmanager kann Mitgliederdaten bearbeiten, Abteilungswechsel verwalten und Austritte erfassen."
);
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a3
- **Vorgänger / Parent:** [[Use_Case_Analyse]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case]]
  - [[Anforderungsmanagement]]
