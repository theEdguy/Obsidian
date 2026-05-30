---
id: a598c733-b22a-40ef-b2bf-c1fa97a3c844
title: "SQLite"
date: 2026-05-30
tags:
  - software_engineering
  - datenbanken
  - persistenz
  - softwarearchitektur
  - embedded_systems
  - acid
  - sql
  - draft
source: "Klausur_Referenz"
---

# [[SQLite]]

- **Kernkonzept:** SQLite ist eine eingebettete, serverlose, nullkonfigurierte [[Datenbank_Engine]], die relationale Daten in einer einzigen plattformunabhängigen Datei speichert. Im Gegensatz zu klassischen [[Client-Server_Datenbanken]] wie MySQL oder PostgreSQL läuft SQLite direkt in der Anwendung und benötigt keinen separaten Datenbankprozess. Sie implementiert den Großteil des [[SQL_Standard]] (SQL-92) und unterstützt Transaktionen, ACID-Eigenschaften sowie komplexe Abfragen, bleibt dabei jedoch extrem leichtgewichtig (ca. 500 KB Bibliotheksgröße).
- **Nutzen & Zweck:** SQLite wird primär eingesetzt, um lokale Persistenz in Anwendungen zu realisieren, ohne externe Abhängigkeiten oder Konfigurationen zu erfordern. Typische Anwendungsfälle sind:

1. **Mobile Apps & Embedded Systems**: Nutzung in [[Android]] (Standard-Datenbank) oder [[iOS]]-Apps, da keine Server-Infrastruktur benötigt wird.
2. **Desktop-Anwendungen**: Lokale Datenspeicherung in Tools wie [[Firefox]] (Lesezeichen) oder [[Skype]] (Chatverlauf).
3. **Prototyping & Testing**: Schnelle Integration in [[Unit_Tests]] oder [[MVP]]-Entwicklungen dank einfacher Einrichtung.
4. **IoT-Geräte**: Datenhaltung auf ressourcenbeschränkten Geräten (z. B. Sensoren).

Vorteile:
- **Keine Installation/Administration**: Die Datenbank ist eine einzelne Datei (z. B. `*.sqlite`), die einfach kopiert oder gelöscht werden kann.
- **Plattformunabhängigkeit**: Läuft auf allen gängigen Betriebssystemen und Architekturen.
- **Hohe Performance**: Durch direkte Dateizugriffe (kein Netzwerk-Overhead) und optimierte Abfrageausführung.
- **Vollständige SQL-Unterstützung**: Inklusive Joins, Subqueries, Indizes und [[Transaktionen]].
- **Öffentliche Domain**: Keine Lizenzkosten oder rechtlichen Einschränkungen.
- **Abgrenzung & Grenzen:** SQLite ist **nicht** für folgende Szenarien geeignet:

1. **Mehrbenutzerbetrieb mit hohen Schreiblasten**: Da die Datenbankdatei exklusiv von einer Anwendung gesperrt wird, skaliert SQLite schlecht bei konkurrierenden Schreibzugriffen (z. B. Webanwendungen mit vielen Nutzern). Hier sind [[Client-Server_Datenbanken]] wie PostgreSQL vorzuziehen.
2. **Große Datenmengen (> 1 TB)**: Die Performance leidet bei extrem großen Dateien, da die gesamte Datenbank im Arbeitsspeicher gehalten werden muss.
3. **Verteilte Systeme**: Fehlende Replikationsmechanismen oder Cluster-Unterstützung.
4. **Komplexe Sicherheitsanforderungen**: Keine integrierte Benutzerverwaltung oder Verschlüsselung (muss auf Anwendungsebene implementiert werden).

**Stolpersteine**:
- **Dateisperren**: Bei gleichzeitigen Zugriffen kann es zu `SQLITE_BUSY`-Fehlern kommen (Lösungsansatz: [[Retry-Mechanismen]] oder [[WAL-Modus]]).
- **Fehlende ALTER TABLE-Unterstützung**: Spalten können nicht einfach umbenannt oder gelöscht werden (Workaround: Neue Tabelle erstellen, Daten migrieren).
- **Keine Stored Procedures**: Logik muss in der Anwendung implementiert werden.
- **Datenbankgröße**: Standardmäßig auf 140 TB begrenzt (theoretisch), praktisch jedoch durch Dateisysteme eingeschränkt.
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer einfachen [[CRUD]]-Operation mit SQLite in Python (unter Verwendung des `sqlite3`-Moduls). Das Beispiel zeigt die Erstellung einer Tabelle `Mitglied` (analog zum Kontext), das Einfügen von Daten und eine Abfrage mit Transaktionssicherung.', 'code': 'import sqlite3\nfrom datetime import date\n\n# Verbindung zur Datenbank herstellen (erstellt die Datei, falls nicht vorhanden)\nconnection = sqlite3.connect(\'assocy.sqlite\')\ncursor = connection.cursor()\n\n# Tabelle erstellen (entspricht dem UML-Klassendiagramm aus dem Kontext)\ncursor.execute(\'\'\'\nCREATE TABLE IF NOT EXISTS Mitglied (\n    id INTEGER PRIMARY KEY AUTOINCREMENT,\n    name TEXT NOT NULL CHECK(LENGTH(name) <= 32),\n    adresse TEXT,\n    alter DATE,\n    leistung INTEGER DEFAULT 1\n)\n\'\'\')\n\n# Daten einfügen (Transaktion)\ntry:\n    cursor.execute(\'BEGIN TRANSACTION\')\n    cursor.execute(\n        "INSERT INTO Mitglied (name, adresse, alter, leistung) VALUES (?, ?, ?, ?)",\n        (\'Max Mustermann\', \'Musterstraße 1, 12345 Musterstadt\', date(1990, 5, 17), 2)\n    )\n    connection.commit()  # Transaktion abschließen\n    print("Mitglied erfolgreich hinzugefügt!")\nexcept sqlite3.Error as e:\n    connection.rollback()  # Bei Fehler zurückrollen\n    print(f"Fehler: {e}")\n\n# Abfrage mit Leistungsprognose (analog zur Methode `leistungsprognose` im Kontext)\ncursor.execute(\n    "SELECT name, leistung FROM Mitglied WHERE alter < ?",\n    (date(2000, 1, 1),)\n)\nmitglieder = cursor.fetchall()\nprint("Mitglieder mit Leistungsprognose:")\nfor name, leistung in mitglieder:\n    print(f"- {name}: {leistung} (Prognose: {leistung * 1.1:.1f})")\n\n# Verbindung schließen\nconnection.close()', 'uml_diagramm': {'beschreibung': 'Vereinfachtes [[Komponentendiagramm]] zur Einbettung von SQLite in eine Schichtenarchitektur (inspiriert vom Kontext). SQLite ersetzt hier eine klassische [[Client-Server_Datenbank]] in der Persistenzschicht.', 'mermaid': 'classDiagram\n    direction LR\n    class Anwendung {\n        +main()\n    }\n    class Persistenzschicht {\n        +speichern(daten: Objekt)\n        +laden(id: Integer): Objekt\n    }\n    class SQLiteConnector {\n        -db_path: String\n        +execute(sql: String, params: Tuple)\n        +commit()\n        +rollback()\n    }\n    class Mitglied {\n        +name: String\n        +adresse: String\n        -alter: Date\n        -leistung: Integer\n        +leistungsprognose(datum: Date): Integer\n    }\n\n    Anwendung --> Persistenzschicht : nutzt\n    Persistenzschicht --> SQLiteConnector : implementiert\n    SQLiteConnector ..> Mitglied : persistiert\n    SQLiteConnector ..> "1" assocy.sqlite : Datenbankdatei\n\n    note for SQLiteConnector "Eingebettete SQLite-Datenbank\\n(kein separater Serverprozess)"\n    note for Persistenzschicht "Isoliert die Anwendung\\nvon der Datenbank-Logik ([[Dependency_Inversion]])"'}}
