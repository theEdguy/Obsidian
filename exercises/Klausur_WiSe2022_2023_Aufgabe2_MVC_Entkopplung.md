---
id: c3baa5e6-17e2-4184-b31e-f557f746ad81
title: "Klausur_WiSe2022_2023_Aufgabe2_MVC_Entkopplung"
date: 2026-05-30
tags:
  - software_engineering
  - wise2022_2023
  - klausur_ws2022_2023
  - software_architektur
  - entwurfsmuster
  - mvc
  - entkopplung
  - exercise
  - draft
source: "SWE 2022-2023 mit Loesung.pdf"
---

# [[Klausur_WiSe2022_2023_Aufgabe2_MVC_Entkopplung]]

- **Aufgabenstellung:** 
  1. Erläutern Sie, inwiefern das [[MVC_Pattern|MVC-Muster]] unterschiedliche Teile einer Anwendung entkoppelt und warum diese Form der Entkopplung sinnvoll ist.
  2. Beschreiben Sie die spezifischen Aufgaben der drei Komponenten Model (M), View (V) und Controller (C) im MVC-Muster.
- **Lösungsweg / Musterlösung:** 
  1. **Entkopplung durch das MVC-Muster:**
     Das [[MVC_Pattern|MVC-Muster]] trennt die Präsentationsschicht (View und Controller) von der Anwendungslogik und Datenhaltung (Model). Diese Trennung ermöglicht eine lose Kopplung zwischen den Komponenten, da Änderungen in einer Komponente (z. B. der View) keine direkten Auswirkungen auf die anderen Komponenten (z. B. das Model) haben. Die Entkopplung ist sinnvoll, weil sie:
     - die Wartbarkeit und Erweiterbarkeit der Anwendung verbessert,
     - die Wiederverwendbarkeit von Komponenten (z. B. mehrere Views für ein Model) fördert,
     - die parallele Entwicklung verschiedener Schichten (z. B. Frontend und Backend) ermöglicht und
     - die Testbarkeit der einzelnen Komponenten erleichtert.
  
  2. **Aufgaben der Komponenten:**
     - **Model (M):**
       Das Model kapselt die Daten und die Geschäftslogik der Anwendung. Es ist verantwortlich für die Speicherung, Verarbeitung und Validierung der Daten sowie für die Benachrichtigung der Views über Änderungen (z. B. durch das [[Observer_Pattern|Observer-Pattern]]). Das Model ist unabhängig von der Präsentationsschicht.
     - **View (V):**
       Die View ist für die Darstellung der Daten aus dem Model zuständig. Sie visualisiert den aktuellen Zustand des Models und nimmt Benutzereingaben entgegen, leitet diese jedoch nicht selbst weiter, sondern übergibt sie an den Controller. Eine View sollte keine Anwendungslogik enthalten.
     - **Controller (C):**
       Der Controller fungiert als Vermittler zwischen View und Model. Er empfängt Benutzereingaben (z. B. Klicks, Tastatureingaben) von der View, verarbeitet diese und aktualisiert das Model entsprechend. Anschließend sorgt er dafür, dass die View den aktuellen Zustand des Models anzeigt.
- **Theoretischer Bezug:** 
  - [[MVC_Pattern]]
  - [[Lose_Kopplung]]
  - [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]]
  - [[Observer_Pattern]]
  - [[Schichtenarchitektur]]
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung der Verantwortlichkeiten von View und Controller: Die View sollte keine Logik enthalten, während der Controller keine Daten visualisiert.
  - Falsche Annahme, dass das Model direkt mit der View kommuniziert. Tatsächlich erfolgt die Kommunikation oft über den Controller oder ein [[Observer_Pattern|Observer-Pattern]].
  - Vermischung von Geschäftslogik und Präsentationslogik, was die Entkopplung zunichtemacht.
  - Unklare Trennung zwischen Model und Datenbank: Das Model repräsentiert die Daten und Logik, nicht zwingend die physische Speicherung.
  - Übersehen der Notwendigkeit, dass das Model die Views über Änderungen informieren muss (z. B. durch Events oder das [[Observer_Pattern|Observer-Pattern]]).
