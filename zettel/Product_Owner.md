---
id: 15251101-e54e-48ab-9522-8bd0bfd74487
title: "Product Owner"
date: 2026-06-23
tags:
  - software_engineering
  - product_owner
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Product Owner]]

- **Kernkonzept:** Der Product Owner ist eine zentrale Rolle im Scrum-Framework, verantwortlich für die Maximierung des Wertes des Produkts und die Priorisierung der Anforderungen im Product Backlog. Er vertritt die Interessen der Stakeholder und stellt sicher, dass das Entwicklungsteam an den richtigen Aufgaben arbeitet.
- **Nutzen & Zweck:** Der Product Owner löst das Problem der unklaren oder widersprüchlichen Anforderungen in der Softwareentwicklung, indem er als einzige Instanz für die Priorisierung und Klarstellung der Produktvision fungiert. Dies ermöglicht eine zielgerichtete Entwicklung, reduziert Missverständnisse zwischen Stakeholdern und Entwicklungsteam und sorgt dafür, dass das Produkt kontinuierlich an den Bedürfnissen der Nutzer ausgerichtet wird.
- **Abgrenzung & Grenzen:** Der Product Owner sollte nicht genutzt werden, wenn keine agile Entwicklungsumgebung (wie Scrum) vorliegt oder wenn die Produktverantwortung bereits klar durch andere Rollen (z. B. Projektmanager in klassischen Vorgehensmodellen) abgedeckt ist. Im Gegensatz zu einem klassischen Projektmanager trifft der Product Owner keine Entscheidungen über Ressourcen oder Zeitpläne, sondern konzentriert sich ausschließlich auf die inhaltliche Ausrichtung des Produkts. Zudem ist die Rolle nicht geeignet, wenn keine klare Produktvision existiert oder die Stakeholder nicht bereit sind, Entscheidungsbefugnis an eine einzelne Person zu delegieren.
- **Beispiel / Code:** ```java
// Beispiel für ein Product Backlog Item (PBI) im JSON-Format, wie es vom Product Owner priorisiert wird
{
  "id": 123,
  "title": "Mitgliederverwaltung erweitern",
  "description": "Als Vereinsmanager möchte ich Mitgliederdaten bearbeiten können, um aktuelle Informationen zu pflegen.",
  "priority": "hoch",
  "acceptanceCriteria": [
    "Der Vereinsmanager kann Mitgliederdaten anlegen, bearbeiten und löschen.",
    "Bei Abteilungswechsel wird eine Benachrichtigungsmail versendet.",
    "Passive Mitglieder werden im System gekennzeichnet."
  ],
  "storyPoints": 5
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9a1
- **Vorgänger / Parent:** [[Scrum-Rollen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Scrum-Rollen]]
  - [[Scrum]]
