---
id: 03ccf3ed-5d0d-4930-9f3f-4339235f5fa4
title: "Akteur"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - requirements_engineering
  - anforderungsanalyse
  - modellierung
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Akteur]]

- **Kernkonzept:** Ein [[Akteur]] ist eine [[Rolle]] (z. B. [[Endbenutzer]], [[Fremdsystem]], [[Hardware-Komponente|Hardware-Komponenten]]) außerhalb des [[Softwaresystem|Systems]], die mit diesem interagiert, um ein [[Ziel]] zu erreichen. [[Akteur|Akteure]] können [[Mensch|Menschen]] oder andere [[Systemkomponente|Systeme]] sein und sind zentral für die Definition der [[Systemgrenze|Systemgrenzen]].
- **Nutzen & Zweck:** [[Akteur|Akteure]] helfen, die [[Systemgrenze|Systemgrenzen]] präzise zu definieren und [[Use_Case|Use-Cases]] aus der Perspektive der [[Nutzer]] oder externen [[Systemkomponente|Systeme]] zu modellieren. Sie sind essenziell für die [[Use-Case-Analyse]] und ermöglichen eine klare Abgrenzung, *wer* mit dem [[Softwaresystem|System]] interagiert und *welche* [[Funktionalität]] benötigt wird. Ohne sie fehlt die strukturierte Grundlage für die [[Anforderungsanalyse]].
- **Abgrenzung & Grenzen:** Ein [[Akteur]] ist keine interne [[Komponente]] des [[Softwaresystem|Systems]] selbst (z. B. ist eine [[Datenbank]] kein [[Akteur]], wenn sie intern genutzt wird). Im Gegensatz zu [[Stakeholder|Stakeholdern]] müssen [[Akteur|Akteure]] direkt mit dem [[Softwaresystem|System]] interagieren. Sie ersetzen keine [[Datenmodellierung]] oder interne [[Logik]] und beschreiben ausschließlich externe Interaktionen, nicht die innere Arbeitsweise des [[Softwaresystem|Systems]].
- **Beispiel / Code:** ```plantuml
@startuml
actor [[Vereinsmanager|Vereinsmanager]] as Manager
actor [[Mail_Client|Mail-Client]] as Client
actor [[Zahlungsdienstleister|Zahlungsdienstleister]] as Payment

Manager -> (Mitglieder verwalten)
Client -> (Benachrichtigung senden)
Payment -> (Zahlung bestätigen)
@enduml
```

**Erläuterung:**
- Der [[Vereinsmanager]] ist ein menschlicher [[Akteur]], der das [[Ziel]] der Mitgliederverwaltung verfolgt.
- Der [[Mail_Client]] und der [[Zahlungsdienstleister]] sind externe [[Systemkomponente|Systeme]], die als [[Akteur|Akteure]] mit dem [[Softwaresystem|System]] interagieren.
