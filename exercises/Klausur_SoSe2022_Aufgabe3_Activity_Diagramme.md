---
id: e45d0c4c-ffb0-46d2-9b5a-cfef5abd1ce6
title: "Klausur_SoSe2022_Aufgabe3_Activity_Diagramme"
date: 2026-05-30
tags:
  - software_engineering
  - sose2022
  - klausur_sose_2022
  - aktivitätsdiagramm
  - analyse
  - design
  - uml
  - workflow_modellierung
  - exercise
  - draft
source: "SWE 2022 mit Loesung.pdf"
---

# [[Klausur_SoSe2022_Aufgabe3_Activity_Diagramme]]

- **Aufgabenstellung:** 
  - **a:** Wozu können [[Aktivitätsdiagramm|Aktivitätsdiagramme]] im Rahmen von Analyse und Design eingesetzt werden? Geben Sie eine präzise und strukturierte Antwort.
  - **b:**
  Skizzieren Sie das durch die folgende Beschreibung gegebene [[Aktivitätsdiagramm]]: 
  
  Der Kontrollfluss beginnt mit der Durchführung von Action A in der einen Swimlane und endet in der anderen Swimlane, nachdem Action E abgeschlossen wurde. Im Anschluss an Action A existieren mehrere Möglichkeiten: Unter der Bedingung 'x' wird mit Action B in der anderen Swimlane fortgefahren, während unter der Bedingung 'not x' die Actions C und D in derselben Swimlane parallel ausgeführt werden, bevor nach deren beider Abschluss erneut mit der Durchführung von A begonnen wird. Auch nach Abschluss von B gibt es mehrere Möglichkeiten: Unter der Bedingung 'y' wird mit E fortgefahren, während unter der Bedingung 'not y' erneut mit der Durchführung von A begonnen wird.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  [[Aktivitätsdiagramme]] eignen sich im Rahmen von Analyse und Design für folgende Zwecke:
  
  1. **Beschreibung von [[Use_Case|Use Cases]] mithilfe von Szenarien**: Sie ermöglichen die detaillierte Darstellung von Abläufen und Workflows, die in einem [[Use_Case|Use Case]] beschrieben werden.
  
  2. **Modellierung von Workflows und funktionalen Bestandteilen**: Actions repräsentieren die einzelnen Schritte eines Workflows, während Pins den Datenfluss zwischen diesen Schritten abbilden können.
  
  3. **Trennung von Verantwortlichkeitsbereichen**: Durch [[Swimlane|Swimlanes]] können verschiedene Akteure oder Systemkomponenten und deren Verantwortlichkeiten klar voneinander abgegrenzt werden. Übergänge zwischen [[Swimlane|Swimlanes]] helfen dabei, [[Schnittstelle|Schnittstellen]] zu identifizieren und zu modellieren.
  
  4. **Darstellung von Parallelität und Entscheidungen**: [[Aktivitätsdiagramme]] ermöglichen die Modellierung von parallelen Abläufen (z. B. durch Fork- und Join-Knoten) sowie von bedingten Verzweigungen (z. B. durch Decision-Knoten).
  - **b:**
  Das beschriebene [[Aktivitätsdiagramm]] lässt sich wie folgt skizzieren:
  
  1. **Startknoten**: Der Kontrollfluss beginnt mit einem Startknoten, der zu Action A führt.
  
  2. **Action A**: Diese Action wird in der ersten [[Swimlane]] ausgeführt.
  
  3. **Decision-Knoten nach Action A**: 
     - Unter der Bedingung 'x' wird der Kontrollfluss zu Action B in der zweiten [[Swimlane]] geleitet.
     - Unter der Bedingung 'not x' wird der Kontrollfluss zu einem Fork-Knoten geleitet, der die parallele Ausführung von Action C und Action D in der ersten [[Swimlane]] ermöglicht.
  
  4. **Join-Knoten nach Actions C und D**: Nach Abschluss von C und D wird der Kontrollfluss durch einen Join-Knoten zusammengeführt und zurück zu Action A geleitet.
  
  5. **Action B**: Diese Action wird in der zweiten [[Swimlane]] ausgeführt.
  
  6. **Decision-Knoten nach Action B**: 
     - Unter der Bedingung 'y' wird der Kontrollfluss zu Action E in der zweiten [[Swimlane]] geleitet.
     - Unter der Bedingung 'not y' wird der Kontrollfluss zurück zu Action A geleitet.
  
  7. **Action E**: Diese Action wird in der zweiten [[Swimlane]] ausgeführt und markiert das Ende des Kontrollflusses.
  
  8. **Endknoten**: Der Kontrollfluss endet nach Action E mit einem Endknoten.
  
  ```mermaid
  activityDiagram
      title Activity-Diagramm mit Swimlanes
      swimlane Swimlane1
      swimlane Swimlane2
  
      start --> A
      A --> decision1
      decision1 -->|x| B
      decision1 -->|not x| fork1
      fork1 --> C
      fork1 --> D
      C --> join1
      D --> join1
      join1 --> A
  
      B --> decision2
      decision2 -->|y| E
      decision2 -->|not y| A
      E --> end
  
      A --> Swimlane1
      C --> Swimlane1
      D --> Swimlane1
      B --> Swimlane2
      E --> Swimlane2
  ```
- **Theoretischer Bezug:** 
  - [[Aktivitätsdiagramm]]
  - [[Use_Case]]
  - [[Swimlane]]
  - [[Schnittstelle]]
  - [[Kontrollfluss]]
  - [[Fork_Knoten]]
  - [[Join_Knoten]]
  - [[Decision_Knoten]]
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung von [[Fork_Knoten|Fork-]] und [[Join_Knoten|Join-Knoten]]: Ein Fork-Knoten teilt den Kontrollfluss in parallele Pfade auf, während ein Join-Knoten diese wieder zusammenführt.
  - Falsche Zuordnung der Actions zu den [[Swimlane|Swimlanes]]: Actions müssen korrekt den jeweiligen Verantwortlichkeitsbereichen zugeordnet werden, um die [[Schnittstelle|Schnittstellen]] zwischen diesen Bereichen klar darzustellen.
  - Unklare Bedingungen in den [[Decision_Knoten|Decision-Knoten]]: Die Bedingungen 'x' und 'not x' bzw. 'y' und 'not y' müssen präzise und eindeutig formuliert sein, um Missverständnisse zu vermeiden.
  - Vergessen des Rücksprungs zu Action A: Nach Abschluss der parallelen Actions C und D sowie bei der Bedingung 'not y' muss der Kontrollfluss zurück zu Action A geleitet werden, was leicht übersehen werden kann.
  - Fehlende Endknoten: Der Kontrollfluss muss nach Action E mit einem Endknoten abgeschlossen werden, um das Ende des Workflows korrekt zu modellieren.
