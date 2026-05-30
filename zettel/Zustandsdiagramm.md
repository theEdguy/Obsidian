---
id: a0ec8504-8cc2-41e0-adb4-06e9a60850f4
title: "Zustandsdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - systemmodellierung
  - draft
source: "SWE Slides (Folien 256-270)"
---

# [[Zustandsdiagramm]]

- **Kernkonzept:** Ein [[Zustandsdiagramm]] ist eine grafische Darstellung eines [[Protokollautomat|Protokollautomaten]], die die [[Zustand|Zustände]] eines [[Objekt|Objekts]] oder [[System|Systems]] und die [[Übergang|Übergänge]] zwischen diesen [[Zustand|Zuständen]] visualisiert.
- **Nutzen & Zweck:** Es veranschaulicht das dynamische Verhalten von [[Objekt|Objekten]] oder [[System|Systemen]] und hilft, [[Zustand|Zustandsabhängigkeiten]] und [[Übergang|Übergangsbedingungen]] zu verstehen. Dies ist essenziell für die [[Analyse]] und [[Design]] komplexer [[System|Systeme]].
- **Abgrenzung & Grenzen:** Nicht geeignet für die Darstellung von Algorithmen oder Datenflüssen. Für solche Zwecke sind [[Aktivitätsdiagramm|Aktivitätsdiagramme]] oder [[Sequenzdiagramm|Sequenzdiagramme]] besser geeignet.
- **Beispiel / Code:** ```mermaid
stateDiagram-v2
    [*] --> Inaktiv
    Inaktiv --> Aktiv: abheben
    Aktiv --> Inaktiv: auflegen
    Aktiv --> Wählen: Nummer wählen
    Wählen --> Verbunden: [Gegenstelle nimmt an]
    Verbunden --> Aktiv: auflegen
```
