---
id: 07aa828f-d5ad-4a0a-9cc2-50350c46dce2
title: "Klausur_SoSe2022_Aufgabe2_Use_Case_Diagramm"
date: 2026-05-30
tags:
  - software_engineering
  - sose2022
  - klausur_sose_2022
  - analyse
  - use_case_diagramm
  - anforderungsanalyse
  - uml
  - ki_anwendung
  - exercise
  - draft
source: "SWE 2022 mit Loesung.pdf"
---

# [[Klausur_SoSe2022_Aufgabe2_Use_Case_Diagramm]]

- **Aufgabenstellung:** 
  Skizzieren Sie den nachfolgend beschriebenen Sachverhalt aus Sicht des Entwicklungsteams der neuen Smartphone-App 'mayBee' in Form eines [[Use_Case_Diagramm|Use-Case-Diagramms]].
  
  Teilaufgaben:
  
  (a) Identifizieren Sie die relevanten [[Akteur|Akteure]] im beschriebenen Szenario.
  
  (b) Leiten Sie die zentralen [[Use_Case|Use-Cases]] aus der Gesprächsnotiz ab. Achten Sie darauf, dass alle beschriebenen Funktionalitäten abgedeckt sind.
  
  (c) Modellieren Sie die Beziehungen zwischen den [[Akteur|Akteuren]] und den [[Use_Case|Use-Cases]] sowie mögliche [[Include_Beziehung|Include]]- und [[Extend_Beziehung|Extend]]-Beziehungen zwischen den [[Use_Case|Use-Cases]].
  
  (d) Geben Sie eine kurze Erläuterung zu jedem identifizierten [[Use_Case]] (1–2 Sätze).
- **Lösungsweg / Musterlösung:** 
  - **a_akteure:**
  - - **name:** Hobby-Bienenkundler
      - **beschreibung:** Primärer [[Akteur]], der die App nutzt, um Bienenarten zu bestimmen und Sichtungen zu melden.
    - - **name:** Server (KI-Analyse)
      - **beschreibung:** Sekundärer [[Akteur]], der die Bildanalyse durchführt und Ergebnisse zurückliefert.
    - - **name:** Sichtungsdatenbank
      - **beschreibung:** Sekundärer [[Akteur]], der die gemeldeten Sichtungen speichert und für die öffentliche Abfrage bereitstellt.
    - - **name:** Location Service
      - **beschreibung:** Sekundärer [[Akteur]], der optional Ortsdaten bereitstellt (falls Nutzer zustimmt).
  - **b_use_cases:**
  - - **name:** Bienenart bestimmen
      - **beschreibung:** Hauptfunktionalität: Der Nutzer wählt Bilder aus, die an den Server gesendet und von der KI analysiert werden. Das Ergebnis (Bienenart) wird zurückgegeben.
    - - **name:** Bilder auswählen
      - **beschreibung:** Der Nutzer wählt ein oder mehrere Bilder der Biene aus, die für die Bestimmung verwendet werden sollen.
    - - **name:** Hintergrundinformationen abrufen
      - **beschreibung:** Nach der Bestimmung kann der Nutzer zusätzliche Informationen zur identifizierten Bienenart abrufen.
    - - **name:** Sichtung melden
      - **beschreibung:** Falls es sich um eine gefährdete Art handelt, wird der Nutzer aufgefordert, Name, Datum und Ort der Sichtung anzugeben.
    - - **name:** Ortsdaten abfragen
      - **beschreibung:** Optional: Der Location Service wird genutzt, um Ortsdaten automatisch zu erfassen (falls Nutzer zustimmt).
    - - **name:** Sichtung anonym speichern
      - **beschreibung:** Falls der Nutzer keine Daten preisgeben möchte, wird die Sichtung ohne persönliche oder Ortsangaben gespeichert.
  - **c_beziehungen:**
  - **akteur_use_case:**
  - - **akteur:** Hobby-Bienenkundler
        - **use_cases:**
  - Bilder auswählen
          - Bienenart bestimmen
          - Hintergrundinformationen abrufen
          - Sichtung melden
      - - **akteur:** Server (KI-Analyse)
        - **use_cases:** - Bienenart bestimmen
      - - **akteur:** Sichtungsdatenbank
        - **use_cases:**
  - Sichtung melden
          - Sichtung anonym speichern
      - - **akteur:** Location Service
        - **use_cases:** - Ortsdaten abfragen
    - **use_case_beziehungen:**
  - - **typ:** [[Include_Beziehung]]
        - **quelle:** Bienenart bestimmen
        - **ziel:** Bilder auswählen
      - - **typ:** [[Extend_Beziehung]]
        - **quelle:** Bienenart bestimmen
        - **ziel:** Hintergrundinformationen abrufen
        - **bedingung:** Nutzer wählt Option
      - - **typ:** [[Extend_Beziehung]]
        - **quelle:** Bienenart bestimmen
        - **ziel:** Sichtung melden
        - **bedingung:** Bienenart ist gefährdet und Bestimmung eindeutig
      - - **typ:** [[Include_Beziehung]]
        - **quelle:** Sichtung melden
        - **ziel:** Ortsdaten abfragen
        - **bedingung:** Nutzer stimmt zu
      - - **typ:** [[Extend_Beziehung]]
        - **quelle:** Sichtung melden
        - **ziel:** Sichtung anonym speichern
        - **bedingung:** Nutzer stimmt Datenübermittlung nicht zu
  - **d_erlaeuterungen:**
  - - **use_case:** Bienenart bestimmen
      - **erlaeuterung:** Kernfunktionalität der App. Der Nutzer interagiert direkt mit der KI, um eine unbekannte Biene zu identifizieren. Dieser [[Use_Case]] umfasst die Auswahl der Bilder und die Rückmeldung des Ergebnisses.
    - - **use_case:** Bilder auswählen
      - **erlaeuterung:** Unterstützender [[Use_Case]], der von 'Bienenart bestimmen' eingebunden wird. Der Nutzer wählt die relevanten Bilder aus, die an den Server gesendet werden.
    - - **use_case:** Hintergrundinformationen abrufen
      - **erlaeuterung:** Optionale Erweiterung von 'Bienenart bestimmen'. Der Nutzer kann nach der Bestimmung zusätzliche Details zur identifizierten Art abrufen.
    - - **use_case:** Sichtung melden
      - **erlaeuterung:** Wird nur ausgeführt, wenn die Bienenart gefährdet und die Bestimmung eindeutig ist. Der Nutzer gibt manuell Daten ein oder nutzt optional den Location Service.
    - - **use_case:** Ortsdaten abfragen
      - **erlaeuterung:** Wird nur eingebunden, wenn der Nutzer der Nutzung des Location Services zustimmt. Automatisiert die Erfassung der Ortsdaten.
    - - **use_case:** Sichtung anonym speichern
      - **erlaeuterung:** Erweiterung von 'Sichtung melden', falls der Nutzer keine persönlichen oder Ortsdaten preisgeben möchte. Die Sichtung wird ohne Metadaten gespeichert.
  - **use_case_diagramm:**
  - **beschreibung:**
  Das [[Use_Case_Diagramm]] sollte folgende Elemente enthalten:
  - Einen primären [[Akteur]] 'Hobby-Bienenkundler', der mit allen Haupt-[[Use_Case|Use-Cases]] interagiert.
  - Sekundäre [[Akteur|Akteure]] 'Server (KI-Analyse)', 'Sichtungsdatenbank' und 'Location Service', die unterstützende Rollen einnehmen.
  - Die zentralen [[Use_Case|Use-Cases]] 'Bienenart bestimmen', 'Bilder auswählen', 'Hintergrundinformationen abrufen', 'Sichtung melden', 'Ortsdaten abfragen' und 'Sichtung anonym speichern'.
  - [[Include_Beziehung|Include-Beziehungen]] für zwingend eingebundene [[Use_Case|Use-Cases]] (z. B. 'Bilder auswählen' in 'Bienenart bestimmen').
  - [[Extend_Beziehung|Extend-Beziehungen]] für optionale oder bedingte Erweiterungen (z. B. 'Hintergrundinformationen abrufen' oder 'Sichtung anonym speichern').
  
  Beispielhafte Darstellung (textuell):
  ```
  Hobby-Bienenkundler --> (Bienenart bestimmen)
  (Bienenart bestimmen) --> (Bilder auswählen) <<include>>
  (Bienenart bestimmen) --> (Hintergrundinformationen abrufen) <<extend>> {Nutzer wählt Option}
  (Bienenart bestimmen) --> (Sichtung melden) <<extend>> {Bienenart gefährdet und Bestimmung eindeutig}
  (Sichtung melden) --> (Ortsdaten abfragen) <<include>> {Nutzer stimmt zu}
  (Sichtung melden) --> (Sichtung anonym speichern) <<extend>> {Nutzer stimmt nicht zu}
  Server (KI-Analyse) --> (Bienenart bestimmen)
  Sichtungsdatenbank --> (Sichtung melden)
  Sichtungsdatenbank --> (Sichtung anonym speichern)
  Location Service --> (Ortsdaten abfragen)
  ```
- **Theoretischer Bezug:** 
  - [[Use_Case_Diagramm]]
  - [[Akteur]]
  - [[Use_Case]]
  - [[Include_Beziehung]]
  - [[Extend_Beziehung]]
  - [[Anforderungsanalyse]]
  - [[Funktionale_Anforderung|Funktionale Anforderungen]]
  - [[Nicht-funktionale_Anforderung|Nicht-funktionale Anforderungen]] (z. B. Datenschutz)
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von primären und sekundären [[Akteur|Akteuren]]: Der 'Server (KI-Analyse)' und die 'Sichtungsdatenbank' sind keine Nutzer der App, sondern Systemkomponenten, die als sekundäre [[Akteur|Akteure]] modelliert werden.
  - Falsche Verwendung von [[Include_Beziehung|Include]] und [[Extend_Beziehung|Extend]]: [[Include_Beziehung|Include]] wird für zwingend eingebundene [[Use_Case|Use-Cases]] verwendet, [[Extend_Beziehung|Extend]] für optionale oder bedingte Erweiterungen. Häufig werden diese vertauscht.
  - Unvollständige Abdeckung der Anforderungen: Wichtige Funktionalitäten wie die anonyme Speicherung von Sichtungen oder die optionale Nutzung des Location Services werden übersehen.
  - Überladung des [[Use_Case_Diagramm|Use-Case-Diagramms]]: Zu viele Details oder technische Aspekte (z. B. Datenformate wie JPG) gehören nicht in das Diagramm, sondern in die textuelle Beschreibung der [[Use_Case|Use-Cases]].
  - Fehlende Bedingungen bei [[Extend_Beziehung|Extend-Beziehungen]]: Bedingungen wie 'Nutzer stimmt zu' oder 'Bienenart ist gefährdet' müssen explizit angegeben werden.
  - Vernachlässigung von [[Nicht-funktionale_Anforderung|nicht-funktionalen Anforderungen]]: Datenschutzaspekte (z. B. keine Verarbeitung von Meta-Informationen) sollten in der Beschreibung der [[Use_Case|Use-Cases]] erwähnt werden, auch wenn sie nicht im Diagramm dargestellt werden.
