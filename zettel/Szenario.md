---
id: c2089a7d-2236-4831-81d6-35e83fc399b6
title: "Szenario"
date: 2026-05-30
tags:
  - software_engineering
  - requirements_engineering
  - use_case_modeling
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Szenario]]

- **Kernkonzept:** Ein [[Szenario]] ist eine konkrete Beschreibung der [[Interaktion|Interaktionen]] zwischen [[Akteur|Akteuren]] und dem [[System]] in einer spezifischen Situation, um [[Use_Case|Use Cases]] zu veranschaulichen.
- **Nutzen & Zweck:** Es hilft, [[Anwendungsfall|Anwendungsfälle]] detailliert zu verstehen und zu dokumentieren, insbesondere bei komplexen [[Ablauf|Abläufen]]. Es dient als Grundlage für die Erstellung von [[Testfall|Testfällen]] und [[Interaktionsdiagramm|Interaktionsdiagrammen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für die Darstellung allgemeiner [[Funktionalität|Funktionalitäten]] oder [[Geschäftsregel|Geschäftsregeln]]. Für solche Zwecke sind [[Aktivitätsdiagramm|Aktivitätsdiagramme]] oder [[Zustandsdiagramm|Zustandsdiagramme]] besser geeignet.
- **Beispiel / Code:** ```text
Szenario: Mitglied anmelden
1. Der Akteur „Mitglied“ gibt seine persönlichen Daten ein.
2. Das System validiert die Daten.
3. Das System speichert die Daten und bestätigt die Anmeldung.
```
