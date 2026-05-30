---
id: a08f5742-4d91-43cc-97f8-51b8d8a66248
title: "Konnektor"
date: 2026-05-30
tags:
  - software_engineering
  - architektur
  - design
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Konnektor]]

- **Kernkonzept:** Ein [[Konnektor]] verbindet [[Komponente|Komponenten]] oder [[Schnittstelle|Schnittstellen]] in der [[Systemarchitektur]]. Es gibt zwei Typen: *Assembly Connector* (verbindet [[Komponente|Komponenten]] über [[Schnittstelle|Schnittstellen]]) und *Delegation Connector* (verbindet externe [[Schnittstelle|Schnittstellen]] mit internen [[Implementierung|Implementierungen]]).
- **Nutzen & Zweck:** Er ermöglicht die Kommunikation zwischen [[Komponente|Komponenten]] und fördert die [[Modularität]] und [[Erweiterbarkeit]] des Systems. [[Konnektor|Konnektoren]] sind essenziell für die Strukturierung komplexer Systeme.
- **Abgrenzung & Grenzen:** Kein Ersatz für die [[Implementierung]] von [[Komponente|Komponenten]] oder [[Schnittstelle|Schnittstellen]]. [[Konnektor|Konnektoren]] beschreiben nur die Verbindung, nicht die Logik. Im Gegensatz zu [[API]]s sind sie abstrakter und architekturbezogen.
- **Beispiel / Code:** ```plantuml
@startuml
component BestellService
component ZahlungsService
BestellService --> ZahlungsService : <<Assembly Connector>>
@enduml
```
