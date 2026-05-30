---
id: b7dbb606-ac92-48de-9545-100d586331cc
title: "Trennung_von_Belangen"
date: 2026-05-30
tags:
  - software_engineering
  - design_prinzip
  - software_architektur
  - draft
source: "SWE Slides (Folien 256-270)"
---

# [[Trennung_von_Belangen]]

- **Kernkonzept:** Die [[Trennung_von_Belangen]] (Separation of Concerns) ist ein [[Designprinzip]], das die Aufteilung eines [[System|Systems]] in [[Modul|Module]] oder [[Komponente|Komponenten]] mit klar abgegrenzten Verantwortlichkeiten vorsieht.
- **Nutzen & Zweck:** Sie reduziert die [[Komplexität]] und verbessert die [[Wartbarkeit]] und [[Erweiterbarkeit]] von [[System|Systemen]], indem sie sicherstellt, dass jede [[Komponente]] nur eine spezifische Aufgabe erfüllt. Dies fördert die [[Modularität]] und [[Kohäsion]].
- **Abgrenzung & Grenzen:** Nicht geeignet für sehr kleine [[Anwendung|Anwendungen]], bei denen die Trennung von Verantwortlichkeiten zu Overhead führt. In solchen Fällen kann eine monolithische Struktur effizienter sein.
- **Beispiel / Code:** ```java
// Beispiel für Trennung von Belangen in MVC
// Model (Daten und Geschäftslogik)
public class MemberModel {
    // ...
}

// View (Präsentation)
public class MemberView {
    // ...
}

// Controller (Benutzerinteraktion)
public class MemberController {
    // ...
}
```
