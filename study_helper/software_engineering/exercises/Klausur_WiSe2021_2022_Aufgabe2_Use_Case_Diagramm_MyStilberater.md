---
id: cf0518e3-2af1-43ed-ab69-e3a7e66abd62
title: "Klausur_WiSe2021_2022_Aufgabe2_Use_Case_Diagramm_MyStilberater"
date: 2026-05-30
tags:
  - software_engineering
  - wise2021_2022
  - klausur_ws2021_2022
  - use_case_diagramm
  - anforderungsanalyse
  - uml
  - systemmodellierung
  - exercise
  - draft
source: "SWE 2021-2022 mit Loesung.pdf"
---

# [[Klausur_WiSe2021_2022_Aufgabe2_Use_Case_Diagramm_MyStilberater]]

- **Aufgabenstellung:** 
  Skizzieren Sie den beschriebenen Sachverhalt aus Sicht des Entwicklungsteams der neuen App 'MyStilberater' in Form eines [[Use_Case_Diagramm|Use-Case-Diagramms]]. Gehen Sie dabei wie folgt vor:
  
  1. Identifizieren Sie alle relevanten [[Akteur|Akteure]] (Actors) im System.
  2. Leiten Sie die zentralen [[Use_Case|Use-Cases]] aus der Aufgabenbeschreibung ab. Achten Sie darauf, dass jeder Use-Case eine klare, atomare Funktionalität beschreibt.
  3. Modellieren Sie die Beziehungen zwischen Akteuren und Use-Cases sowie zwischen Use-Cases untereinander (z. B. <<include>>, <<extend>>).
  4. Geben Sie eine kurze textuelle Beschreibung (1–2 Sätze) für jeden identifizierten Use-Case an.
  5. Skizzieren Sie das Use-Case-Diagramm in UML-Notation. Falls keine grafische Darstellung möglich ist, beschreiben Sie die Struktur präzise in Textform.
- **Lösungsweg / Musterlösung:** 
  - **akteure:**
  - - **name:** Nutzer
      - **beschreibung:** Primärer Akteur, der die App verwendet, um Kleidungsvorschläge zu erhalten und Kleidungsstücke zu verwalten.
    - - **name:** Terminkalender-System
      - **beschreibung:** Externes System, das Termindaten des Nutzers bereitstellt (z. B. Google Calendar, Outlook).
    - - **name:** Wetterdienst
      - **beschreibung:** Externer Dienst, der Wetterdaten für den Standort des Nutzers liefert.
    - - **name:** Bilderkennungs-API
      - **beschreibung:** Externes System, das Kleidungsstücke anhand von Fotos identifiziert (z. B. für das Einpflegen von Kleidung).
    - - **name:** Shopping-Anbieter
      - **beschreibung:** Externer Dienst, der passende Kleidungsvorschläge für fehlende Kombinationen unterbreitet.
  - **use_cases:**
  - - **name:** Tagesoutfit vorschlagen
      - **beschreibung:** Schlägt dem Nutzer basierend auf Terminen, Wetter und verfügbaren Kleidungsstücken ein passendes Outfit vor.
      - **beziehungen:**
  - **include:**
  - Termine abrufen
          - Wetter abrufen
          - Kleidung prüfen
        - **extend:** - Shopping-Vorschläge unterbreiten
    - - **name:** Termine abrufen
      - **beschreibung:** Ruft die Termine des Nutzers aus dem Terminkalender-System ab und analysiert den Dresscode für jeden Termin.
    - - **name:** Wetter abrufen
      - **beschreibung:** Ruft die aktuellen Wetterdaten für den Standort des Nutzers vom Wetterdienst ab.
    - - **name:** Kleidung prüfen
      - **beschreibung:** Überprüft, welche Kleidungsstücke verfügbar sind (nicht in der Wäsche) und kombinierbar sind.
    - - **name:** Kleidung einpflegen
      - **beschreibung:** Ermöglicht dem Nutzer, neue Kleidungsstücke über die Kamera und Bilderkennung hinzuzufügen.
      - **beziehungen:** - **include:** - Bild analysieren
    - - **name:** Bild analysieren
      - **beschreibung:** Nutzt die Bilderkennungs-API, um Kleidungsstücke aus Fotos zu identifizieren und zu kategorisieren.
    - - **name:** Shopping-Vorschläge unterbreiten
      - **beschreibung:** Schlägt dem Nutzer passende Kleidungsstücke von Shopping-Anbietern vor, falls keine ausreichenden Kombinationen vorhanden sind.
      - **beziehungen:** - **include:** - Fehlende Kleidung identifizieren
    - - **name:** Fehlende Kleidung identifizieren
      - **beschreibung:** Analysiert, welche Kleidungsstücke für bestimmte Anlässe fehlen und leitet daraus Shopping-Vorschläge ab.
  - **use_case_diagramm_beschreibung:**
  - **struktur:**
  Das Use-Case-Diagramm zeigt den Akteur 'Nutzer' in der Mitte, der mit allen primären Use-Cases interagiert:
  - 'Tagesoutfit vorschlagen' (zentraler Use-Case)
  - 'Kleidung einpflegen'
  
  Die externen Systeme ('Terminkalender-System', 'Wetterdienst', 'Bilderkennungs-API', 'Shopping-Anbieter') sind als sekundäre Akteure dargestellt und interagieren mit den folgenden Use-Cases:
  - 'Terminkalender-System' → 'Termine abrufen'
  - 'Wetterdienst' → 'Wetter abrufen'
  - 'Bilderkennungs-API' → 'Bild analysieren'
  - 'Shopping-Anbieter' → 'Shopping-Vorschläge unterbreiten'
  
  Beziehungen zwischen Use-Cases:
  - 'Tagesoutfit vorschlagen' <<include>> 'Termine abrufen', 'Wetter abrufen', 'Kleidung prüfen'
  - 'Tagesoutfit vorschlagen' <<extend>> 'Shopping-Vorschläge unterbreiten'
  - 'Kleidung einpflegen' <<include>> 'Bild analysieren'
  - 'Shopping-Vorschläge unterbreiten' <<include>> 'Fehlende Kleidung identifizieren'
    - **hinweise:** Achten Sie darauf, dass <<include>>-Beziehungen obligatorisch sind (der inkludierte Use-Case wird immer ausgeführt), während <<extend>>-Beziehungen optional sind (der erweiternde Use-Case wird nur unter bestimmten Bedingungen ausgeführt).
- **Theoretischer Bezug:** 
  - [[Use_Case_Diagramm|Use-Case-Diagramme]]
  - [[Akteur|Akteure]] in der [[Anforderungsanalyse]]
  - [[Include_und_Extend|<<include>>- und <<extend>>-Beziehungen]]
  - [[UML|UML-Notation]]
  - [[Systemgrenze|Systemgrenzen]] in Use-Case-Diagrammen
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von Akteuren und Systemkomponenten: Externe Systeme (z. B. Wetterdienst) sind Akteure, keine internen Komponenten der App.
  - Zu grobe Use-Cases: Jeder Use-Case sollte eine atomare Funktionalität beschreiben (z. B. nicht 'App nutzen', sondern 'Tagesoutfit vorschlagen').
  - Falsche Verwendung von <<include>> und <<extend>>: <<include>> ist obligatorisch, <<extend>> ist optional und bedingungsabhängig.
  - Vernachlässigung der Systemgrenze: Nur die App selbst (z. B. 'MyStilberater') sollte innerhalb der Systemgrenze liegen, externe Systeme außerhalb.
  - Fehlende textuelle Beschreibungen: Jeder Use-Case sollte kurz beschrieben werden, um Missverständnisse zu vermeiden.
  - Überladung des Diagramms: Zu viele Use-Cases oder Beziehungen machen das Diagramm unübersichtlich. Fokussieren Sie sich auf die zentralen Funktionalitäten.
