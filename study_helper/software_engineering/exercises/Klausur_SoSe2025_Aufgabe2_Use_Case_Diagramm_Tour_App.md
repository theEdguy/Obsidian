---
id: 902db1c1-d048-45e5-a859-b14da1118981
title: "Klausur_SoSe2025_Aufgabe2_Use_Case_Diagramm_Tour_App"
date: 2026-05-30
tags:
  - software_engineering
  - sose_2025
  - klausur_sose_2025
  - use_case_diagramm
  - analyse
  - anforderungsermittlung
  - mobile_app
  - ki_integration
  - lokale_datenhaltung
  - sqlite
  - uml
  - exercise
  - draft
source: "SWE-SoSe-2025-Loesung.pdf"
---

# [[Klausur_SoSe2025_Aufgabe2_Use_Case_Diagramm_Tour_App]]

- **Aufgabenstellung:** 
  - **a:** Identifizieren Sie alle relevanten Akteure (Akteursrollen) für die beschriebene Tour-App aus der Perspektive des Entwicklungsteams. Begründen Sie kurz, warum jeder Akteur für die Umsetzung der App essenziell ist.
  - **b:** Erstellen Sie ein Use-Case-Diagramm für die Tour-App. Berücksichtigen Sie dabei folgende Anforderungen aus der Aufgabenstellung:
  - **b_i:** Nutzer können vorgefertigte Touren anpassen und individualisieren.
  - **b_ii:** Die App generiert KI-basierte Vorschläge für Sehenswürdigkeiten und Aktivitäten.
  - **b_iii:** Die App trackt den Standort des Nutzers und liefert kontextbezogene Informationen.
  - **b_iv:** Nutzer können ein Fotobuch erstellen, das automatisch mit KI analysiert und angereichert wird.
  - **b_v:** Das Fotobuch kann über das Reiseportal mit Familie und Freunden geteilt werden.
  - **b_vi:** Alle Daten werden lokal auf dem Smartphone gespeichert.
  - **c:** Diskutieren Sie, welche Datenbank sich für die lokale Speicherung der Tour-Daten und Nutzerinformationen eignet. Begründen Sie Ihre Wahl und gehen Sie auf Vor- und Nachteile ein.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **akteure:**
  - - **name:** Nutzer
        - **begründung:** Der primäre Akteur, der die App verwendet, um Touren zu planen, anzupassen, zu nutzen und Fotobücher zu erstellen. Ohne Nutzer gäbe es keine Interaktion mit der App.
      - - **name:** KI-System
        - **begründung:** Externer Akteur, der für die Generierung von Vorschlägen, die Analyse von Fotos und die Anreicherung von Fotobüchern verantwortlich ist. Die KI ist ein zentraler Bestandteil der intelligenten Funktionen der App.
      - - **name:** MediaStore (Smartphone)
        - **begründung:** Externer Akteur, der den Zugriff auf die auf dem Smartphone gespeicherten Fotos ermöglicht. Ohne diesen Zugriff wäre die Erstellung von Fotobüchern nicht möglich.
      - - **name:** Reiseportal (Backend)
        - **begründung:** Externer Akteur, der vorgefertigte Touren bereitstellt und das Teilen von Fotobüchern mit Familie und Freunden ermöglicht. Das Portal dient als Datenquelle und Veröffentlichungsplattform.
      - - **name:** GPS-Sensor (Smartphone)
        - **begründung:** Externer Akteur, der den aktuellen Standort des Nutzers trackt. Dies ist essenziell für die Standortverfolgung und kontextbezogene Informationen während der Tour.
      - - **name:** Product Owner (Frau Müller)
        - **begründung:** Interner Akteur, der die Anforderungen definiert und die Vision der App kommuniziert. Wichtig für das Entwicklungsteam, um die Use-Cases und Prioritäten zu verstehen.
      - - **name:** Entwicklungsteam
        - **begründung:** Interner Akteur, der die App implementiert, die Datenbank auswählt und die Integration der externen Akteure (KI, MediaStore, GPS) sicherstellt. Ohne das Team gäbe es keine Umsetzung.
  - **b:**
  - **use_case_diagramm:**
  - **beschreibung:** Das Use-Case-Diagramm sollte folgende Use-Cases und Beziehungen enthalten:
      - **use_cases:**
  - - **name:** Tour anpassen
          - **akteure:** - Nutzer
          - **beschreibung:** Der Nutzer kann vorgefertigte Touren individuell anpassen (z. B. Reihenfolge ändern, Stopps hinzufügen/entfernen).
        - - **name:** KI-Vorschläge generieren
          - **akteure:**
  - Nutzer
            - KI-System
          - **beschreibung:** Die KI generiert basierend auf den Interessen des Nutzers Vorschläge für Sehenswürdigkeiten und Aktivitäten.
        - - **name:** Standort tracken
          - **akteure:**
  - Nutzer
            - GPS-Sensor
          - **beschreibung:** Die App trackt kontinuierlich den Standort des Nutzers während der Tour.
        - - **name:** Kontextinformationen anzeigen
          - **akteure:** - Nutzer
          - **beschreibung:** Die App liefert Hintergrundinformationen, Tipps für Fotos und kreative Hinweise zu den aktuellen Orten.
        - - **name:** Fotobuch erstellen
          - **akteure:**
  - Nutzer
            - KI-System
            - MediaStore
          - **beschreibung:** Der Nutzer kann ein Fotobuch erstellen, das automatisch von der KI analysiert und mit Kommentaren/Storys angereichert wird.
        - - **name:** Fotobuch teilen
          - **akteure:**
  - Nutzer
            - Reiseportal
          - **beschreibung:** Das erstellte Fotobuch kann über das Reiseportal mit Familie und Freunden geteilt werden.
        - - **name:** Daten lokal speichern
          - **akteure:** - Nutzer
          - **beschreibung:** Alle Daten (Touren, Nutzerinformationen, Fotobücher) werden lokal auf dem Smartphone gespeichert.
      - **beziehungen:**
  - **include:**
  - - **von:** Tour anpassen
            - **zu:** KI-Vorschläge generieren
          - - **von:** Fotobuch erstellen
            - **zu:** Daten lokal speichern
        - **extend:**
  - - **von:** Kontextinformationen anzeigen
            - **zu:** Standort tracken
            - **bedingung:** Nur wenn der Nutzer kontextbezogene Informationen wünscht.
      - **diagramm_skizze:**
  ```plantuml
  @startuml
  left to right direction
  actor Nutzer
  actor "KI-System" as KI
  actor "MediaStore" as Media
  actor "GPS-Sensor" as GPS
  actor "Reiseportal" as Portal
  
  Nutzer --> (Tour anpassen)
  Nutzer --> (KI-Vorschläge generieren)
  KI --> (KI-Vorschläge generieren)
  Nutzer --> (Standort tracken)
  GPS --> (Standort tracken)
  Nutzer --> (Kontextinformationen anzeigen)
  (Standort tracken) .> (Kontextinformationen anzeigen) : <<extend>>
  Nutzer --> (Fotobuch erstellen)
  KI --> (Fotobuch erstellen)
  Media --> (Fotobuch erstellen)
  Nutzer --> (Fotobuch teilen)
  Portal --> (Fotobuch teilen)
  Nutzer --> (Daten lokal speichern)
  (Fotobuch erstellen) .> (Daten lokal speichern) : <<include>>
  (Tour anpassen) .> (KI-Vorschläge generieren) : <<include>>
  @enduml
  ```
  - **c:**
  - **datenbank_empfehlung:**
  - **empfehlung:** Für die lokale Speicherung der Tour-Daten und Nutzerinformationen eignet sich eine **SQLite-Datenbank**.
      - **begründung:**
  - **vorteile:**
  - SQLite ist eine leichtgewichtige, serverlose Datenbank, die direkt in die App integriert werden kann und keine separate Installation erfordert.
          - Sie unterstützt relationale Datenstrukturen, was für die Speicherung von Touren, Nutzerdaten und Fotobüchern mit ihren Beziehungen (z. B. Tour-Stopps, Fotos zu Highlights) ideal ist.
          - SQLite ist plattformübergreifend (Android, iOS) und bietet eine gute Performance für lokale Abfragen.
          - Die Datenbank ist ACID-konform, was die Datenintegrität sicherstellt.
          - SQLite unterstützt Verschlüsselung (z. B. SQLCipher), was für den Datenschutz relevant ist.
        - **nachteile:**
  - SQLite ist nicht für große Datenmengen oder hohe Schreiblasten ausgelegt, was für diese App jedoch kein Problem darstellt, da die Daten lokal und nutzerspezifisch sind.
          - Die Synchronisation mit einem Backend (z. B. Reiseportal) erfordert zusätzliche Implementierung, da SQLite keine eingebaute Sync-Funktionalität bietet.
          - Für komplexe Abfragen oder Volltextsuche sind zusätzliche Bibliotheken oder manuelle Optimierungen nötig.
        - **alternativen:**
  - **realm:**
  - **beschreibung:** Eine moderne, objektorientierte Datenbank, die für mobile Apps optimiert ist.
            - **vorteile:**
  - Schnellere Performance bei komplexen Abfragen
              - Einfache Integration mit Objektmodellen
              - Eingebaute Sync-Funktionalität (Realm Sync)
            - **nachteile:**
  - Größerer Footprint im Vergleich zu SQLite
              - Weniger verbreitet für relationale Datenstrukturen
          - **shared_preferences:**
  - **beschreibung:** Für einfache Schlüssel-Wert-Paare (z. B. Nutzerpräferenzen).
            - **nachteile:** - Nicht geeignet für strukturierte Daten wie Touren oder Fotobücher.
      - **fazit:** SQLite ist die beste Wahl für diese App, da sie eine gute Balance zwischen Funktionalität, Performance und Einfachheit bietet. Die relationale Struktur passt gut zu den Anforderungen der Tour-Daten und Fotobücher, und die lokale Speicherung ist ohne zusätzliche Serverinfrastruktur möglich.
- **Theoretischer Bezug:** 
  - [[Use_Case_Diagramm|Use-Case-Diagramme]] zur Modellierung der Anforderungen und Akteure.
  - [[Akteur_(UML)|Akteure]] in der UML, insbesondere die Unterscheidung zwischen primären und sekundären Akteuren.
  - [[KI_Integration_in_Software|KI-Integration in Software]] und deren Modellierung als externer Akteur.
  - [[Lokale_Datenhaltung|Lokale Datenhaltung]] in mobilen Apps und die Auswahl geeigneter [[Datenbank|Datenbanken]].
  - [[SQLite|SQLite]] als relationale Datenbank für mobile Anwendungen.
  - [[Datenschutz_in_mobilen_Apps|Datenschutz in mobilen Apps]] und die Bedeutung lokaler Speicherung.
  - [[Include_und_Extend_Beziehungen|Include- und Extend-Beziehungen]] in Use-Case-Diagrammen.
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von Akteuren: Oft werden interne Akteure (z. B. Entwicklungsteam) mit externen Akteuren (z. B. Nutzer, KI) verwechselt. Nur Akteure, die direkt mit dem System interagieren, gehören ins Use-Case-Diagramm.
  - Unklare Abgrenzung von Use-Cases: Use-Cases sollten atomar und unabhängig voneinander sein. Beispiel: 'Fotobuch erstellen' und 'Fotobuch teilen' sind zwei separate Use-Cases, da sie unterschiedliche Ziele verfolgen.
  - Fehlende Include/Extend-Beziehungen: Wichtige Abhängigkeiten zwischen Use-Cases (z. B. 'Fotobuch erstellen' setzt 'Daten lokal speichern' voraus) werden oft vergessen.
  - Überladung des Diagramms: Zu viele Use-Cases oder Akteure machen das Diagramm unübersichtlich. Fokus auf die zentralen Funktionen legen.
  - Falsche Datenbankwahl: Die Annahme, dass eine NoSQL-Datenbank (z. B. MongoDB) für lokale Speicherung besser geeignet ist als SQLite, obwohl relationale Strukturen (Touren mit Stopps, Fotos mit Metadaten) vorherrschen.
  - Vernachlässigung des Datenschutzes: Die lokale Speicherung wird oft als gegeben hingenommen, ohne die Implikationen für die Datenbankwahl zu diskutieren (z. B. Verschlüsselung, Zugriffskontrolle).
  - Unklare KI-Modellierung: Die KI wird oft als Teil des Systems statt als externer Akteur dargestellt, obwohl sie eine separate Komponente mit eigener Logik ist.
