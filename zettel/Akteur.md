---
id: d0bd4260-7632-4af1-8b2d-78eb44035b99
title: "Akteur"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - requirements_engineering
  - anforderungsanalyse
  - modellierung
  - akteure
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Akteur]]

- **Kernkonzept:** Ein [[Akteur]] ist eine [[Rolle]] (z. B. [[Endbenutzer]], [[Fremdsystem]], [[Hardware-Komponente|Hardware-Komponenten]] oder [[Gerät|Geräte]]) außerhalb des [[Softwaresystem|Systems]], die mit diesem interagiert, um ein [[Ziel]] zu erreichen. [[Akteur|Akteure]] können [[Mensch|Menschen]] oder andere [[Systemkomponente|Systeme]] sein und definieren die [[Systemgrenze|Systemgrenzen]] für die Modellierung von [[Use_Case|Use-Cases]] aus externer Perspektive.
- **Nutzen & Zweck:** [[Akteur|Akteure]] helfen, die [[Systemgrenze|Systemgrenzen]] präzise zu definieren und [[Use_Case|Use-Cases]] aus der Perspektive der [[Nutzer]] oder externen [[Systemkomponente|Systeme]] zu modellieren. Sie sind essenziell für die [[Use-Case-Analyse]] und ermöglichen eine klare Abgrenzung, *wer* mit dem [[Softwaresystem|System]] interagiert und *welche* [[Funktionalität]] benötigt wird. Dadurch wird sichergestellt, dass das [[Softwaresystem]] die [[Anforderung|Anforderungen]] aller relevanten [[Stakeholder]] abdeckt, funktionale Lücken vermieden werden und die [[Anforderungsanalyse]] strukturiert erfolgt. Ohne [[Akteur|Akteure]] fehlt die systematische Grundlage für die Identifikation und Priorisierung von [[Anforderung|Anforderungen]]. Zudem unterstützen sie die zielgerichtete Erfassung von [[Anforderung|Anforderungen]] aus externer Sicht, ohne die interne [[Logik]] oder [[Architektur]] des [[Softwaresystem|Systems]] vorwegzunehmen.
- **Abgrenzung & Grenzen:** Ein [[Akteur]] ist keine interne [[Komponente]] des [[Softwaresystem|Systems]] selbst (z. B. ist eine [[Datenbank]] kein [[Akteur]], wenn sie intern genutzt wird). Im Gegensatz zu [[Stakeholder|Stakeholdern]] müssen [[Akteur|Akteure]] direkt mit dem [[Softwaresystem|System]] interagieren und ersetzen keine [[Datenmodellierung]] oder interne [[Logik]]. Sie beschreiben ausschließlich externe [[Schnittstelle|Schnittstellen]] und Interaktionen, nicht die innere Arbeitsweise des [[Softwaresystem|Systems]]. Für die Darstellung von [[Prozessablauf|Prozessabläufen]], zeitlichen Abfolgen oder technischen Details sind andere [[UML-Diagramm|UML-Diagramme]] wie [[Aktivitätsdiagramm|Aktivitätsdiagramme]] oder [[Sequenzdiagramm|Sequenzdiagramme]] besser geeignet. Zudem sollten [[Akteur|Akteure]] nicht mit internen [[Rolle|Rollen]] oder [[Systemkomponente|Komponenten]] verwechselt werden, da sie ausschließlich externe Entitäten repräsentieren. [[Akteur|Akteure]] sind keine [[Benutzerrolle|Benutzerrollen]] im Sinne von Berechtigungen, sondern definieren lediglich, *wer* oder *was* mit dem [[Softwaresystem|System]] interagiert. Sie liegen stets außerhalb der [[Systemgrenze|Systemgrenzen]] und sind nicht Teil der [[Systemarchitektur]].
- **Beispiel / Code:** ```plantuml
@startuml
actor [[Vereinsmanager|Vereinsmanager]] as Manager
actor [[Mitglied]] as Member
actor [[Mail_Client|Mail-Client]] as Client
actor [[Zahlungsdienstleister|Zahlungsdienstleister]] as Payment
actor [[IoT_Gerät|IoT-Gerät]] as Device

Manager -> (Mitglieder verwalten)
Member -> (Mitgliedsdaten einsehen)
Client -> (Benachrichtigung senden)
Payment -> (Zahlung bestätigen)
Device -> (Daten synchronisieren)
@enduml
```

**Erläuterung:**
- Der [[Vereinsmanager]] und das [[Mitglied]] sind menschliche [[Akteur|Akteure]], die spezifische [[Ziel|Ziele]] verfolgen (z. B. Mitgliederverwaltung oder Dateneinsicht).
- Der [[Mail_Client]], der [[Zahlungsdienstleister]] und das [[IoT_Gerät]] sind externe [[Systemkomponente|Systeme]] oder [[Gerät|Geräte]], die als [[Akteur|Akteure]] mit dem [[Softwaresystem|System]] interagieren.
- Die [[Use_Case|Use-Cases]] zeigen die Interaktionen zwischen den [[Akteur|Akteuren]] und dem [[Softwaresystem|System]], ohne interne [[Logik]] oder [[Architektur]] zu offenbaren.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1
- **Vorgänger / Parent:** [[Use-Case-Diagramm]]
- **Folgezettel / Unterzettel:**
  - [[Primärer_Akteur]]
  - [[Sekundärer_Akteur]]
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Systemgrenze]]
