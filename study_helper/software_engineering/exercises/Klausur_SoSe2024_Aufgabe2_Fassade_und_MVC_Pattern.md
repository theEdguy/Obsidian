---
id: d8a09fd3-7799-4502-bfc9-8ad6ebb149ce
title: "Klausur_SoSe2024_Aufgabe2_Fassade_und_MVC_Pattern"
date: 2026-05-30
tags:
  - software_engineering
  - sose2024
  - klausur_sose_2024
  - entwurfsmuster
  - fassade_pattern
  - mvc_pattern
  - software_architektur
  - entkopplung
  - exercise
  - draft
source: "SWE-SoSe-2024 - (Loesung).pdf"
---

# [[Klausur_SoSe2024_Aufgabe2_Fassade_und_MVC_Pattern]]

- **Aufgabenstellung:** 
  - **a:** Typischerweise nutzt man Fassaden für den Zugriff auf Komponenten. Worin liegen die zentralen Aufgaben einer Fassade? (4 Punkte)
  - **b:** In Desktop- sowie in Web-Anwendungen findet oftmals das MVC-Pattern Anwendung. Welches Ziel wird mit dem Einsatz dieses Patterns verfolgt und wie wird dieses Ziel erreicht? (6 Punkte)
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **zentrale_aufgaben:**
  - Eine Fassade kanalisiert den Zugriff auf eine [[Komponente|Komponente]] und dient als zentrale Anlaufstelle für externe Aufrufe.
      - Sie kapselt die externen [[Schnittstelle|Schnittstellen]] und schottet die internen Implementierungsdetails der [[Komponente]] ab, um [[Information_Hiding]] zu gewährleisten.
      - Die Fassade überwacht den Zugriff auf die [[Komponente]] und sorgt für [[Thread_Safety|Thread-Safety]], falls erforderlich.
      - Sie delegiert externe Aufrufe an die verantwortlichen internen Objekte der [[Komponente]] und vereinfacht so die Nutzung komplexer Systeme.
  - **b:**
  - **ziel:** Das MVC-Pattern (Model-View-Controller) verfolgt das Ziel der [[Entkopplung]] und [[Separation_of_Concerns|Separierung]] von Benutzeroberfläche (UI) und Geschäftslogik.
    - **umsetzung:**
  - Das [[Modell]] (Model) kapselt die Geschäftslogik und den Zustand des Systems.
      - Der [[Controller]] verarbeitet Nutzereingaben und wandelt sie in Aufrufe der entsprechenden [[Systemoperation|Systemoperationen]] des Modells um.
      - Die [[View|Views]] visualisieren den aktuellen Zustand des Systems und stellen die Benutzeroberfläche dar.
      - Die Kommunikation zwischen [[Modell]] und UI erfolgt über das [[Observer_Pattern|Observer-Pattern]]: Controller und Views registrieren sich als [[Observer]] beim Modell (Subject) und werden über Zustandsänderungen informiert.
- **Theoretischer Bezug:** 
  - [[Fassade_Pattern|Fassade]]
  - [[MVC_Pattern|Model-View-Controller (MVC)]]
  - [[Observer_Pattern]]
  - [[Information_Hiding]]
  - [[Schnittstelle]]
  - [[Komponente]]
  - [[Thread_Safety]]
  - [[Entkopplung]]
  - [[Separation_of_Concerns]]
  - [[Modell]]
  - [[Controller]]
  - [[View]]
  - [[Systemoperation]]
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung der Fassade mit einer einfachen [[Wrapper_Klasse|Wrapper-Klasse]]: Eine Fassade bietet mehr als nur eine einfache Weiterleitung, z. B. [[Thread_Safety]] oder Zugriffskontrolle.
  - Unklare Trennung der Verantwortlichkeiten im MVC-Pattern: Das [[Modell]] darf keine UI-Logik enthalten, und die [[View]] sollte keine Geschäftslogik implementieren.
  - Fehlende Registrierung der [[Observer]] beim [[Modell]]: Ohne korrekte Anwendung des [[Observer_Pattern|Observer-Patterns]] funktioniert die Benachrichtigung über Zustandsänderungen nicht.
  - Vermischung von [[Controller]] und [[View]]: Der [[Controller]] sollte ausschließlich Nutzereingaben verarbeiten, während die [[View]] nur für die Darstellung zuständig ist.
  - Überladung der Fassade mit zu vielen Verantwortlichkeiten: Eine Fassade sollte den Zugriff vereinfachen, nicht selbst komplexe Logik implementieren.
