---
id: efa2de8d-883b-4e64-b77c-8617f57a5659
title: "Klausur_WiSe2023_2024_Aufgabe4_System_Sequenzdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - wise2023_2024
  - klausur_ws2023_2024
  - system_sequenzdiagramm
  - schnittstellen
  - uml
  - komponenten_interaktion
  - exercise
  - draft
source: "SWE 2023-2024 mit Loesung.pdf"
---

# [[Klausur_WiSe2023_2024_Aufgabe4_System_Sequenzdiagramm]]

- **Aufgabenstellung:** 
  Skizzieren Sie mithilfe eines [[System_Sequenzdiagramm|System-Sequenzdiagramms]] die Interaktionen an der [[Schnittstelle|Schnittstelle]] zwischen den beiden Komponenten A und B. Gehen Sie dabei wie folgt vor:
  
  1. Identifizieren Sie die beteiligten Akteure und Systemkomponenten.
  2. Stellen Sie die Nachrichtenflüsse (Aufrufe, Rückgaben) zwischen den Komponenten dar.
  3. Berücksichtigen Sie mögliche Kontrollflüsse (z. B. Schleifen, Bedingungen).
  4. Geben Sie an, ob es sich um synchrone oder asynchrone Kommunikation handelt.
- **Lösungsweg / Musterlösung:** 
  ### Musterlösung:
  
  1. **Beteiligte Akteure und Komponenten:**
     - **Komponente A**: Initiator der Kommunikation (z. B. Client oder Steuerungskomponente).
     - **Komponente B**: Empfänger der Anfrage (z. B. Server oder Dienstkomponente).
  
  2. **Nachrichtenflüsse im [[System_Sequenzdiagramm|System-Sequenzdiagramm]]:**
     - Komponente A sendet eine Nachricht (z. B. `operationAnfrage()`) an Komponente B.
     - Komponente B verarbeitet die Anfrage und sendet eine Antwort (z. B. `ergebnisRückgabe()`) zurück an Komponente A.
  
     ```plantuml
     @startuml
     actor KomponenteA
     participant KomponenteB
  
     KomponenteA -> KomponenteB: operationAnfrage()
     activate KomponenteB
     KomponenteB --> KomponenteA: ergebnisRückgabe()
     deactivate KomponenteB
     @enduml
     ```
  
  3. **Kontrollflüsse:**
     - Falls die Kommunikation bedingte Abläufe enthält (z. B. Fehlerbehandlung), können diese mit `alt`/`else` oder `loop` dargestellt werden:
  
     ```plantuml
     @startuml
     actor KomponenteA
     participant KomponenteB
  
     KomponenteA -> KomponenteB: operationAnfrage()
     activate KomponenteB
     alt Erfolg
         KomponenteB --> KomponenteA: ergebnisRückgabe()
     else Fehler
         KomponenteB --> KomponenteA: fehlerMeldung()
     end
     deactivate KomponenteB
     @enduml
     ```
  
  4. **Kommunikationsart:**
     - Standardmäßig wird synchrone Kommunikation angenommen (Komponente A wartet auf Antwort).
     - Bei asynchroner Kommunikation (z. B. mit [[Callback|Callbacks]] oder [[Event_Driven_Architecture|Event-basierten Systemen]]) muss dies explizit gekennzeichnet werden (z. B. durch `async` in der Nachricht).
- **Theoretischer Bezug:** 
  Diese Aufgabe bezieht sich auf:
  - [[System_Sequenzdiagramm|System-Sequenzdiagramme]] als Teil der [[UML|UML-Diagramme]].
  - [[Schnittstelle|Schnittstellen]] und deren Modellierung in der [[Komponentenbasierte_Entwicklung|komponentenbasierten Entwicklung]].
  - [[Synchrone_vs_asynchrone_Kommunikation|Synchrone vs. asynchrone Kommunikation]] in verteilten Systemen.
  - [[Kontrollfluss|Kontrollflüsse]] in [[Sequenzdiagramm|Sequenzdiagrammen]] (z. B. Schleifen, Bedingungen).
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von [[System_Sequenzdiagramm|System-Sequenzdiagrammen]] mit [[Detailliertes_Sequenzdiagramm|detaillierten Sequenzdiagrammen]] (System-Sequenzdiagramme zeigen nur die Interaktion an der Systemgrenze, nicht interne Abläufe).
  - Fehlende Aktivierungsbalken (`activate`/`deactivate`) zur Darstellung der Lebensdauer von Nachrichtenverarbeitung.
  - Unklare Unterscheidung zwischen synchroner und asynchroner Kommunikation (z. B. Rückantworten werden fälschlich als asynchron modelliert).
  - Überladung des Diagramms mit zu vielen Details (z. B. interne Methodenaufrufe statt Fokus auf die [[Schnittstelle|Schnittstelleninteraktion]]).
  - Falsche Richtung der Nachrichten (z. B. Antworten werden als neue Anfragen dargestellt).
