---
id: 5b4f38f5-5de6-473c-908d-092540b86cea
title: "Dynamische_Aspekte_im_MVC"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - software_architektur
  - verhaltensanalyse
  - draft
source: "SWE Slides (Folien 226-240)"
---

# [[Dynamische_Aspekte_im_MVC]]

- **Kernkonzept:** [[Dynamische_Aspekte_im_MVC|Dynamische Aspekte]] beschreiben das [[Verhalten]] des [[Model_View_Controller_Pattern|MVC-Musters]] zur Laufzeit, insbesondere die [[Interaktion]] zwischen [[Modell]], [[View]] und [[Controller]] sowie die [[Initialisierung]] des [[System|Systems]].
- **Nutzen & Zweck:** Sie verdeutlichen, wie [[Benutzereingabe|Benutzereingaben]] verarbeitet und [[Aktualisierung|Aktualisierungen]] propagiert werden, um die [[Konsistenz]] der [[Daten]] sicherzustellen.
- **Abgrenzung & Grenzen:** Kein eigenständiges [[Entwurfsmuster]], sondern eine [[Verhaltensbeschreibung]] des [[Model_View_Controller_Pattern|MVC-Musters]]. Unterscheidet sich von statischen [[Strukturdiagramm|Strukturdiagrammen]] durch die Fokussierung auf [[Ablauf|Abläufe]].
- **Beispiel / Code:** ```plaintext
// Sequenzdiagramm (vereinfacht):
1. Benutzer gibt Daten in View ein
2. Controller empfängt Eingabe
3. Controller ruft Modell-Methode auf
4. Modell aktualisiert Daten und benachrichtigt Beobachter
5. View aktualisiert Darstellung
```
