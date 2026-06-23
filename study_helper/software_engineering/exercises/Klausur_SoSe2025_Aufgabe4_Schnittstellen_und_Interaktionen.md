---
id: 4a245cd5-32e9-41a3-8dd0-d630ce31a95d
title: "Klausur_SoSe2025_Aufgabe4_Schnittstellen_und_Interaktionen"
date: 2026-05-30
tags:
  - software_engineering
  - sose_2025
  - exercise
  - draft
source: "SWE-SoSe-2025-Loesung.pdf"
---

# [[Klausur_SoSe2025_Aufgabe4_Schnittstellen_und_Interaktionen]]

- **Aufgabenstellung:** 
  - **a:** Geben Sie jeder Operation an der Schnittstelle zwischen den Komponenten 'A' und 'B' einen Namen und ordnen Sie ihr die Aktionen aus dem Activity-Diagramm zu, für deren Bearbeitung sie verantwortlich ist. (3 Punkte)
  - **b:** Skizzieren Sie mithilfe eines [[System_Sequenzdiagramm|System-Sequenzdiagramms]] die Interaktionen, die im Rahmen dieses Use Cases zwischen den Komponenten 'A' und 'B' stattfinden. (4 Punkte)
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:** Die Schnittstelle der Komponente 'B' stellt der Komponente 'A' folgende Operationen zur Verfügung:
    - **operationen:**
  - - **name:** op1()
        - **verantwortung:** Verantwortlich für die Durchführung der Aktionen B1 und B3.
      - - **name:** op2()
        - **verantwortung:** Verantwortlich für die Durchführung der Aktionen B2 und B3.
      - - **name:** op3()
        - **verantwortung:** Verantwortlich für die Durchführung der Aktion B5.
    - **hinweis:** Die Zuordnung basiert auf der Analyse des Activity-Diagramms, wobei jede Operation klar abgegrenzte Verantwortlichkeiten für bestimmte Aktionen übernimmt.
  - **b:**
  - **beschreibung:** Das [[System_Sequenzdiagramm|System-Sequenzdiagramm]] skizziert die Interaktionen wie folgt:
    - **diagramm_skizze:**
  - **teilnehmer:**
  - Komponente A (Aktor)
        - Komponente B (System)
      - **interaktionen:**
  - A ruft op1() auf B auf → B führt B1 und B3 aus → Rückmeldung an A.
        - A ruft op2() auf B auf → B führt B2 und B3 aus → Rückmeldung an A.
        - A ruft op3() auf B auf → B führt B5 aus → Rückmeldung an A.
      - **darstellung:** ```plaintext
      - **A -> B: op1()
  :** B --> A: Bestätigung (B1, B3)
      - **A -> B: op2()
  :** B --> A: Bestätigung (B2, B3)
      - **A -> B: op3()
  :** B --> A: Bestätigung (B5)
      - **```:** hinweis
      - **Die Pfeile repräsentieren Nachrichtenaufrufe (Operationen) und deren Rückmeldungen. Die Ausführung der Aktionen (B1, B2, B3, B5) erfolgt innerhalb der Komponente 'B'.:** }
  - **theoretischer_bezug:**
  - Die Aufgabe bezieht sich auf [[Schnittstelle|Schnittstellen]] in der [[Komponentenbasierte_Entwicklung|komponentenbasierten Entwicklung]] und deren Modellierung in [[Aktivitätsdiagramm|Aktivitätsdiagrammen]].
    - Die Interaktionen werden mittels [[System_Sequenzdiagramm|System-Sequenzdiagrammen]] dargestellt, die ein zentrales Werkzeug der [[UML|UML]] zur Beschreibung von [[Dynamisches_Verhalten|dynamischem Verhalten]] sind.
    - Die Zuordnung von Operationen zu Aktionen folgt dem Prinzip der [[Kohäsion|hohen Kohäsion]] und [[Lose_Kopplung|losen Kopplung]].
  - **stolpersteine:**
  - Fehlerhafte Zuordnung von Aktionen zu Operationen: Oft werden Aktionen wie B3 mehreren Operationen zugeordnet, ohne die Verantwortlichkeiten klar zu trennen.
    - Vermischung von [[Aktivitätsdiagramm|Aktivitätsdiagrammen]] und [[Sequenzdiagramm|Sequenzdiagrammen]]: Im System-Sequenzdiagramm werden keine internen Aktionen (z. B. B1, B2) dargestellt, sondern nur Nachrichtenaufrufe und Rückmeldungen.
    - Unklare Benennung der Operationen: Operationen sollten präzise und verständlich benannt werden, um ihre Verantwortlichkeit widerzuspiegeln (z. B. nicht 'doSomething()', sondern 'processData()').
    - Vergessen von Rückmeldungen: Im Sequenzdiagramm müssen Rückmeldungen (z. B. Bestätigungen) explizit modelliert werden, um den Kontrollfluss korrekt abzubilden.
  - **tags:**
  - klausur_sose_2025
    - schnittstelle
    - aktivitätsdiagramm
    - sequenzdiagramm
    - komponenten_interaktion
    - uml
    - software_analyse
- **Theoretischer Bezug:** 
- **Stolpersteine / Fehlerquellen:** 
