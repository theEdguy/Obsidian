---
id: fa69115b-76f5-4bb1-8843-8b57b2c74c24
title: "Klausur_WiSe2024_2025_Aufgabe5_Systemsequenzdiagramm_zu_Aktivitaetsdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - ws_2024_2025
  - klausur_ws_2024_2025
  - uml
  - aktivitaetsdiagramm
  - systemsequenzdiagramm
  - modelltransformation
  - analyse
  - dynamische_modellierung
  - exercise
  - draft
source: "SWE-WS-2024-2025 - Loesung.pdf"
---

# [[Klausur_WiSe2024_2025_Aufgabe5_Systemsequenzdiagramm_zu_Aktivitaetsdiagramm]]

- **Aufgabenstellung:** 
  - **a:**
  Skizzieren Sie ein [[Aktivitätsdiagramm]] für den gegebenen Use Case, dessen Kontrollfluss zum abgebildeten [[Systemsequenzdiagramm]] passt. Beachten Sie folgende Anforderungen:
  - Geben Sie jeder Aktion eine eindeutige Bezeichnung.
  - Stellen Sie sicher, dass Aktionen, die dieselbe Funktionalität repräsentieren, dieselbe Bezeichnung erhalten.
  - Vervollständigen Sie das vorgegebene Diagramm.
  - **b:**
  - **i:** Ordnen Sie die Aktionen Ihres [[Aktivitätsdiagramm|Aktivitätsdiagramms]] aus Teilaufgabe a) den Operationen op1, op2 und op3 zu. Geben Sie an, welche Aktionen Bestandteil welcher Operation sind.
    - **ii:** Identifizieren Sie, welche Aktionen in Ihrem Diagramm *nicht* Bestandteil einer dieser Operationen (op1, op2, op3) sind.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:**
  Das [[Aktivitätsdiagramm]] muss den Kontrollfluss des [[Systemsequenzdiagramm|Systemsequenzdiagramms]] abbilden. Folgende Aktionen und deren Beziehungen sind typisch:
  
  1. **Startknoten** → Aktion **A1** (z. B. 'Use Case starten').
  2. **A1** führt zu einer Entscheidung (z. B. 'Bedingung prüfen').
  3. Bei 'Ja': Aktion **B1** (z. B. 'Daten vorbereiten'), gefolgt von **B3** (z. B. 'Daten verarbeiten').
  4. Bei 'Nein': Aktion **B2** (z. B. 'Alternative Daten laden'), gefolgt von **B3**.
  5. **B3** führt zu Aktion **C1** (z. B. 'Ergebnis speichern').
  6. **C1** führt zum **Endknoten**.
  
  Hinweis: **B3** wird in beiden Pfaden verwendet und muss daher identisch benannt sein.
    - **beispiel_diagramm:**
  ```mermaid
  flowchart TD
      Start([Start]) --> A1[A1: Use Case starten]
      A1 --> Entscheidung{Bedingung?}
      Entscheidung -- Ja --> B1[B1: Daten vorbereiten]
      Entscheidung -- Nein --> B2[B2: Alternative Daten laden]
      B1 --> B3[B3: Daten verarbeiten]
      B2 --> B3
      B3 --> C1[C1: Ergebnis speichern]
      C1 --> Ende([Ende])
  ```
  - **b:**
  - **i:**
  - **op1:** Beinhaltet die Aktionen **B1** und **B3**.
      - **op2:** Beinhaltet die Aktionen **B2** und **B3**.
      - **op3:** Beinhaltet die Aktion **C1**.
    - **ii:** Die Aktionen **A1** und **A2** (falls vorhanden, z. B. als Startaktion oder Entscheidungsknoten) sind kein Bestandteil der Operationen op1, op2 oder op3.
- **Theoretischer Bezug:** 
  - [[Systemsequenzdiagramm|Systemsequenzdiagramme]] dienen der Darstellung von Interaktionen zwischen Systemkomponenten im Rahmen eines Use Cases.
  - [[Aktivitätsdiagramm|Aktivitätsdiagramme]] modellieren den Kontrollfluss und die Ablauflogik eines Prozesses.
  - Die Aufgabe bezieht sich auf die Transformation zwischen [[Modellierungsperspektive|unterschiedlichen Modellierungsperspektiven]] (hier: dynamische Sicht).
  - Die Wiederverwendung von Aktionen (z. B. **B3**) ist ein Beispiel für [[Wiederverwendung|Wiederverwendung]] im [[Softwareentwurf]].
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von [[Aktivitätsdiagramm|Aktivitätsdiagrammen]] und [[Sequenzdiagramm|Sequenzdiagrammen]]: Aktivitätsdiagramme zeigen *Kontrollfluss*, Sequenzdiagramme *Nachrichtenfluss*.
  - Fehlende Konsistenz in Aktionsbezeichnungen: Gleiche Funktionalität muss identisch benannt werden (z. B. **B3** in beiden Pfaden).
  - Vergessen von Entscheidungsknoten oder Start-/Endknoten im [[Aktivitätsdiagramm]].
  - Falsche Zuordnung von Aktionen zu Operationen: Operationen repräsentieren oft *logische Einheiten* (z. B. 'Daten verarbeiten' = **B3**), nicht einzelne Schritte wie Startaktionen (**A1**).
  - Übersehen, dass **B3** in beiden Pfaden (op1 und op2) vorkommt und daher nicht dupliziert werden darf.
