---
id: 866301d5-c3c5-40ec-9778-0076dae16192
title: "Datenintegrität"
date: 2026-05-31
tags:
  - software_engineering
  - datenbanken
  - datenhaltung
  - transaktionen
  - constraints
  - mobile_entwicklung
  - datenschutz
  - compliance
  - draft
source: "Klausur_Referenz"
---

# [[Datenintegrität]]

- **Kernkonzept:** Datenintegrität bezeichnet die Sicherstellung der [[Konsistenz]], [[Korrektheit]] und [[Zuverlässigkeit]] von Daten über ihren gesamten Lebenszyklus hinweg. Sie umfasst Maßnahmen, die verhindern, dass Daten unautorisiert verändert, beschädigt oder unbrauchbar werden. Datenintegrität ist ein zentrales Qualitätsmerkmal in [[Datenbanken]] und [[Datenhaltungssystemen]] und wird durch technische (z. B. [[Transaktionen]], [[Constraints]], [[Checksummen]]) sowie organisatorische Maßnahmen (z. B. [[Zugriffskontrolle]]) gewährleistet.
- **Nutzen & Zweck:** Datenintegrität dient dazu, die Vertrauenswürdigkeit von Daten zu garantieren, was essenziell für die Funktionsfähigkeit von Anwendungen, die Einhaltung von [[Compliance]]-Vorgaben (z. B. [[DSGVO]]) und die Vermeidung von Fehlentscheidungen aufgrund korrupter Daten ist. Im Kontext lokaler Speicherung auf Smartphones (wie im gegebenen Auszug) ist sie besonders relevant, um sicherzustellen, dass aggregierte Daten und individualisierte Touren nicht durch Systemabstürze, Hardwarefehler oder unautorisierte Zugriffe verfälscht werden. Zudem ermöglicht sie die [[Wiederherstellbarkeit]] von Daten nach Fehlern.
- **Abgrenzung & Grenzen:** Datenintegrität ist abzugrenzen von [[Datensicherheit]] (Schutz vor Zugriff) und [[Datenverfügbarkeit]] (Zugänglichkeit der Daten). Während Datensicherheit den Schutz vor externen Bedrohungen (z. B. [[Cyberangriffe]]) fokussiert, konzentriert sich Datenintegrität auf die innere Qualität der Daten. Typische Stolpersteine sind:
- **Fehlende Constraints**: Ohne [[Primärschlüssel]], [[Fremdschlüssel]] oder [[Datenvalidierung]] können inkonsistente Daten entstehen.
- **Transaktionsfehler**: Bei lokalen Datenbanken auf Smartphones können unterbrochene [[Transaktionen]] (z. B. durch App-Abstürze) zu partiell geschriebenen Daten führen.
- **Synchronisationskonflikte**: Bei Offline-Nutzung (z. B. Tourenplanung) können Konflikte durch spätere [[Datenreplikation]] entstehen.
- **Hardware-Limitierungen**: Begrenzter Speicher oder Prozessorleistung auf Smartphones kann die Implementierung komplexer Integritätsmechanismen erschweren.
- **Beispiel / Code:** {'beschreibung': 'Beispiel für eine lokale SQLite-Datenbank auf Android mit Integritätsmaßnahmen (Java/Kotlin-ähnlich):', 'code': {'schema': '-- Definition einer Tabelle mit Integritätsconstraints\nCREATE TABLE individualisierte_touren (\n    tour_id INTEGER PRIMARY KEY AUTOINCREMENT,\n    nutzer_id INTEGER NOT NULL,\n    startpunkt TEXT NOT NULL,\n    zielpunkt TEXT NOT NULL,\n    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,\n    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,\n    -- Fremdschlüssel-Constraint (referenzielle Integrität)\n    FOREIGN KEY (nutzer_id) REFERENCES nutzer(nutzer_id) ON DELETE CASCADE,\n    -- Check-Constraint für Datenvalidierung\n    CONSTRAINT chk_koordinaten CHECK (startpunkt != zielpunkt)\n);\n\n-- Trigger zur automatischen Aktualisierung von updated_at\nCREATE TRIGGER update_tour_timestamp\nAFTER UPDATE ON individualisierte_touren\nFOR EACH ROW\nBEGIN\n    UPDATE individualisierte_touren SET updated_at = CURRENT_TIMESTAMP WHERE tour_id = OLD.tour_id;\nEND;', 'transaktion': '// Beispiel für eine Transaktion mit Rollback bei Fehlern\nfun speichereTour(tour: Tour) {\n    val db = writableDatabase\n    db.beginTransaction()\n    try {\n        // Daten einfügen\n        db.insertOrThrow("individualisierte_touren", null, tour.toContentValues())\n        // Weitere Operationen (z. B. Wegpunkte speichern)\n        db.setTransactionSuccessful()\n    } catch (e: Exception) {\n        // Loggen und Rollback\n        Log.e("Datenbank", "Fehler bei Tour-Speicherung", e)\n    } finally {\n        db.endTransaction()\n    }\n}'}, 'uml_diagramm': {'typ': 'Mermaid-Klassendiagramm', 'inhalt': 'classDiagram\n    class Nutzer {\n        +nutzer_id: INTEGER [PK]\n        +name: TEXT\n    }\n    \n    class IndividualisierteTour {\n        +tour_id: INTEGER [PK]\n        +nutzer_id: INTEGER [FK]\n        +startpunkt: TEXT\n        +zielpunkt: TEXT\n        +created_at: TIMESTAMP\n        +updated_at: TIMESTAMP\n    }\n    \n    Nutzer "1" -- "0..*" IndividualisierteTour : besitzt\n    \n    note for IndividualisierteTour "Integritätsmaßnahmen:\n    - Primärschlüssel (tour_id)\n    - Fremdschlüssel (nutzer_id)\n    - NOT NULL-Constraints\n    - Check-Constraint (startpunkt != zielpunkt)\n    - Trigger (updated_at-Aktualisierung)"'}}
