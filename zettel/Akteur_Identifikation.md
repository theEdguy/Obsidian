---
id: 6db6946e-acbf-4ec0-9aec-79b2f7544c6a
title: "Akteur Identifikation"
date: 2026-06-23
tags:
  - software_engineering
  - identifikation
  - akteure
  - draft
source: "software_engineering_kapitel_07"
---

# [[Akteur Identifikation]]

- **Kernkonzept:** Akteur Identifikation ist der Prozess, bei dem externe Entitäten (Nutzer, Fremdsysteme oder andere Systeme) ermittelt werden, die mit einem zu entwickelnden System interagieren oder von dessen Funktionen betroffen sind. Akteure sind nicht Teil des Systems selbst, sondern initiieren oder partizipieren an Use Cases.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Anforderungen an ein System systematisch aus der Perspektive der Beteiligten zu erfassen. Es löst das Problem, dass Entwickler ohne klare Akteur-Identifikation zentrale Interaktionspartner übersehen oder falsche Annahmen über deren Bedürfnisse treffen. Durch die Identifikation von Akteuren wird sichergestellt, dass alle relevanten Stakeholder und Systemschnittstellen berücksichtigt werden, was die Vollständigkeit und Korrektheit der Use-Case-Analyse gewährleistet.
- **Abgrenzung & Grenzen:** Akteur Identifikation sollte nicht genutzt werden, wenn das System keine externen Interaktionen aufweist oder wenn die Akteure bereits vollständig und eindeutig definiert sind. Alternativ kann bei sehr einfachen Systemen auf eine detaillierte Akteur-Analyse verzichtet werden, da der Aufwand den Nutzen übersteigt. Im Gegensatz zur Ereignis-basierten Identifikation von Use Cases liegt der Fokus hier auf den handelnden Entitäten, nicht auf den auslösenden Ereignissen. Akteure sind zudem keine Systemkomponenten oder internen Module, sondern immer externe Entitäten.
- **Beispiel / Code:** ```java
// Beispiel: Akteure in einem Use-Case-Diagramm (UML-Notation als Text)
@startuml
actor Vereinsmanager
actor MailClient
actor Abteilungsleiter

Vereinsmanager --> (Mitglieder verwalten)
MailClient --> (Mitglieder verwalten)
Abteilungsleiter --> (Mitglieder verwalten)
@enduml
```

// Alternativ: Akteure in einer textuellen Use-Case-Beschreibung
UseCase: Mitglieder verwalten
Akteure:
- Vereinsmanager (primär)
- MailClient (sekundär, automatisiert)
- Abteilungsleiter (sekundär, informiert)

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1e1
- **Vorgänger / Parent:** [[Use_Case_Akteure]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Akteur]]
  - [[Use_Case]]
