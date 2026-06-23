---
id: c338029d-dbda-4992-855d-d5755537875c
title: "Klausur_SoSe2025_Aufgabe1_Analyse_vs_Design"
date: 2026-05-30
tags:
  - software_engineering
  - sose_2025
  - klausur_sose_2025
  - analyse
  - design
  - aktivitätsdiagramm
  - klassendiagramm
  - system_sequenzdiagramm
  - anforderungsanalyse
  - exercise
  - draft
source: "SWE-SoSe-2025-Loesung.pdf"
---

# [[Klausur_SoSe2025_Aufgabe1_Analyse_vs_Design]]

- **Aufgabenstellung:** 
  - **a:** Worin unterscheiden sich die Zielsetzungen von [[Analyse|Analyse]] und [[Design|Design]] im Software-Engineering? (4 Punkte)
  - **b:**
  Welche Auswirkungen haben diese unterschiedlichen Zielsetzungen auf die Verwendung der folgenden drei [[Diagrammtyp|Diagrammtypen]]? Gehen Sie jeweils auf die Perspektive der Analyse und des Designs ein: (6 Punkte)
  
  1. [[Aktivitätsdiagramm|Aktivitätsdiagramme]]
  2. [[Klassendiagramm|Klassendiagramme]]
  3. [[System-Sequenzdiagramm|System-Sequenzdiagramme]]
- **Lösungsweg / Musterlösung:** 
  - **a:** Die [[Analyse]] zielt darauf ab, die fachlichen [[Anforderung|Anforderungen]] und Abläufe (das Problem) aus Sicht der [[Anwender]] (Kunden) zu verstehen und zu dokumentieren – unabhängig von der späteren [[Implementierung]]. Im Gegensatz dazu besteht das Ziel des [[Design|Designs]] darin, auf Basis der Analyse eine Vorlage für die Umsetzung bzw. die Realisierung zu erstellen. Hier steht das 'Wie' der Lösung im Fokus, also die technische Umsetzung innerhalb der gewählten [[Systemarchitektur]].
  - **b:**
  - **Aktivitätsdiagramme:**
  - **Analyse:** In der [[Analyse]] beschreiben [[Aktivitätsdiagramm|Aktivitätsdiagramme]] die Details von [[Anwendungsfall|Anwendungsfällen]] und Prozessen auf fachlicher Ebene. Sie zeigen insbesondere die Aufteilung von Aufgaben (Verantwortlichkeiten) zwischen dem System (bzw. seinen Teilen) und den [[Akteur|Akteuren]].
      - **Design:** Im [[Design]] beschreiben sie die konkreten Abläufe innerhalb der [[Systemarchitektur]] und damit die zu realisierende Aufgabenverteilung auf die einzelnen [[Komponente|Komponenten]], als Vorlage für die [[Implementierung]].
    - **Klassendiagramme:**
  - **Analyse:** In der [[Analyse]] beschreiben [[Klassendiagramm|Klassendiagramme]] die [[Entität|Entitäten]] und [[Beziehung|Beziehungen]] aus der Fachdomäne (dem Problemraum).
      - **Design:** Im [[Design]] stellen sie die konkreten Strukturen der Software dar, einschließlich [[Klasse|Klassen]], [[Attribut|Attributen]] und [[Methode|Methoden]].
    - **System-Sequenzdiagramme:**
  - **Analyse:** In der [[Analyse]] beschreiben [[System-Sequenzdiagramm|System-Sequenzdiagramme]] das Zusammenspiel zwischen den [[Akteur|Akteuren]] und dem System auf fachlicher Ebene. Sie verdeutlichen das Wesen der [[Schnittstelle|Schnittstelle]].
      - **Design:** Im [[Design]] liegt der Fokus auf der konkreten, zu realisierenden [[Schnittstelle]], einschließlich technischer Details wie [[Nachricht|Nachrichten]], [[Parameter|Parametern]] und [[Rückgabewert|Rückgabewerten]].
- **Theoretischer Bezug:** 
  - [[Analyse]] vs. [[Design]] im Software-Engineering
  - [[Aktivitätsdiagramm|Aktivitätsdiagramme]] in [[Analyse]] und [[Design]]
  - [[Klassendiagramm|Klassendiagramme]] in [[Analyse]] und [[Design]]
  - [[System-Sequenzdiagramm|System-Sequenzdiagramme]] in [[Analyse]] und [[Design]]
  - [[Anforderung|Anforderungen]] und [[Problemraum]] in der [[Analyse]]
  - [[Systemarchitektur]] und [[Lösungsraum]] im [[Design]]
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung der Perspektiven: In der [[Analyse]] darf keine technische Umsetzung (z. B. [[Datenbank]]-Strukturen oder [[Programmiersprache|Programmiersprachen]]) berücksichtigt werden, während im [[Design]] genau diese Details im Vordergrund stehen.
  - Unklare Abgrenzung von [[Akteur|Akteuren]] und [[Komponente|Komponenten]]: In [[Aktivitätsdiagramm|Aktivitätsdiagrammen]] der [[Analyse]] werden oft [[Akteur|Akteure]] mit Systemteilen verwechselt, was zu falschen Verantwortlichkeiten führt.
  - Überladung von [[Klassendiagramm|Klassendiagrammen]] in der [[Analyse]]: Fachliche [[Entität|Entitäten]] werden fälschlich mit technischen [[Klasse|Klassen]] (z. B. Controller, Services) vermischt.
  - Fehlende Präzision in [[System-Sequenzdiagramm|System-Sequenzdiagrammen]]: In der [[Analyse]] werden [[Nachricht|Nachrichten]] oft zu vage beschrieben, während im [[Design]] konkrete [[Parameter]] und [[Rückgabewert|Rückgabewerte]] fehlen.
  - Vernachlässigung der [[Schnittstelle|Schnittstellen]]-Definition: Im [[Design]] wird oft vergessen, dass [[System-Sequenzdiagramm|System-Sequenzdiagramme]] die technische [[Schnittstelle]] präzise vorgeben müssen.
