---
id: a4970a84-b604-4fd5-81b0-97f3d75efc07
title: "Assembly_Connector"
date: 2026-05-30
tags:
  - software_engineering
  - softwarearchitektur
  - komponentenbasierte_entwicklung
  - uml
  - entwurfsmuster
  - schichtenmodell
  - schnittstellen
  - draft
source: "Klausur_Referenz"
---

# [[Assembly_Connector]]

- **Kernkonzept:** Ein **Assembly_Connector** ist ein [[Konnektor]] in der [[Softwarearchitektur]], der Komponenten durch direkte Verbindung ihrer [[Schnittstellen]] miteinander koppelt. Er dient der strukturellen Integration von Komponenten innerhalb einer Schicht oder zwischen klar definierten Schichten, wobei die Kommunikation über explizit definierte Schnittstellen erfolgt. Im Gegensatz zum [[Delegation_Connector]] verbindet der Assembly_Connector gleichrangige oder hierarchisch angeordnete Komponenten, ohne eine externe Schnittstelle nach innen zu delegieren. Er folgt dem Prinzip der losen Kopplung und fördert die Modularität durch klare Abhängigkeitsdefinitionen.
- **Nutzen & Zweck:** Der **Assembly_Connector** wird eingesetzt, um:
- Komponenten in einer [[Schichtenarchitektur]] gezielt zu verbinden, ohne die Schichtenhierarchie zu verletzen (z. B. Verbindung der [[Persistenzschicht]] mit der Logikschicht).
- Die Austauschbarkeit von Komponenten zu ermöglichen, da Abhängigkeiten ausschließlich über [[Schnittstellen]] definiert sind.
- Die Wartbarkeit und Testbarkeit zu erhöhen, indem Abhängigkeiten explizit und lokal begrenzt werden.
- Die Einhaltung des [[Dependency_Inversion_Principle]] zu unterstützen, indem höhere Schichten nur von Abstraktionen (Schnittstellen) abhängen.

Typische Anwendungsfälle sind die Verbindung von [[Servicekomponenten]] (z. B. `Mailer` ↔ `Database`) oder die Integration von [[Adapter]]-Komponenten in ein System.
- **Abgrenzung & Grenzen:** - **Abgrenzung zum [[Delegation_Connector]]**: Während der Assembly_Connector Komponenten direkt verbindet, leitet der Delegation_Connector externe Schnittstellen an interne Subkomponenten weiter (z. B. bei [[Fassadenmuster]]).
- **Schichtenprinzip**: Ein Assembly_Connector darf **nicht** gegen die Schichtenhierarchie verstoßen (z. B. darf die [[Persistenzschicht]] nicht direkt auf die Präsentationsschicht zugreifen).
- **Kopplungsgrad**: Bei übermäßiger Verwendung kann der Assembly_Connector zu einer starren Architektur führen, wenn Schnittstellen zu spezifisch sind. Hier helfen [[Entwurfsmuster]] wie [[Brücke]] oder [[Mediator]] zur Entkopplung.
- **Nicht für dynamische Verbindungen**: Für Laufzeit-abhängige Verbindungen (z. B. [[Plugin-Systeme]]) sind [[Eventbasierte_Architekturen]] oder [[Dependency_Injection]] besser geeignet.
- **Beispiel / Code:** {'beschreibung': 'UML-Beispiel (textuell mit Mermaid-Syntax) für einen Assembly_Connector zwischen einer `Logic`-Komponente und einer `Database`-Komponente:', 'uml': '```mermaid\nclassDiagram\n    class Logic {\n        +processData()\n    }\n    class Database {\n        +store(data: Data)\n        +load(): Data\n    }\n    class IDatabase {\n        <<interface>>\n        +store(data: Data)\n        +load(): Data\n    }\n\n    Logic --> IDatabase : <<Assembly_Connector>>\n    Database ..|> IDatabase\n```', 'java_beispiel': {'beschreibung': 'Java-Codeausschnitt zur Veranschaulichung der Schnittstellenbindung:', 'code': 'public interface IDatabase {\n    void store(Data data);\n    Data load();\n}\n\npublic class Database implements IDatabase {\n    @Override\n    public void store(Data data) { /* Implementierung */ }\n    @Override\n    public Data load() { /* Implementierung */ }\n}\n\npublic class Logic {\n    private final IDatabase database;\n    \n    // Assembly_Connector: Dependency Injection über Konstruktor\n    public Logic(IDatabase database) {\n        this.database = database;\n    }\n    \n    public void processData() {\n        Data data = database.load();\n        // Verarbeitung...\n        database.store(data);\n    }\n}'}}
