---
id: 38c9d7e2-304d-4f25-8caa-28fc57a9f34a
title: "Modularität"
date: 2026-05-30
tags:
  - software_engineering
  - designprinzip
  - architektur
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Modularität]]

- **Kernkonzept:** [[Modularität]] ist ein [[Designprinzip]], bei dem ein System in unabhängige, austauschbare [[Modul|Module]] oder [[Komponente|Komponenten]] zerlegt wird. Jedes [[Modul]] kapselt eine spezifische [[Funktionalität]] und interagiert über definierte [[Schnittstelle|Schnittstellen]].
- **Nutzen & Zweck:** Sie verbessert die [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Wiederverwendbarkeit]] des Systems. [[Modularität]] reduziert die Komplexität und ermöglicht die parallele Entwicklung von [[Modul|Modulen]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Kohäsion]] oder [[Lose_Kopplung]], sondern ein übergeordnetes Prinzip. Im Gegensatz zu [[Monolith]]-Architekturen fördert [[Modularität]] die Zerlegung in kleinere Einheiten.
- **Beispiel / Code:** ```text
Modulares System:
- Modul: Benutzerverwaltung (Authentifizierung, Profilverwaltung)
- Modul: Bestellabwicklung (Warenkorb, Zahlung)
- Modul: Produktkatalog (Suche, Filter)
```
