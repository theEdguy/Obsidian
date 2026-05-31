---
id: 89cf51fb-127b-4d6e-b8cd-f951ef017c27
title: "Synchrone_vs_asynchrone_Kommunikation"
date: 2026-05-31
tags:
  - software_engineering
  - entwurfsmuster
  - softwarearchitektur
  - verteilte_systeme
  - nachrichtenorientierte_middleware
  - konkurrenz
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Synchrone_vs_asynchrone_Kommunikation]]

- **Kernkonzept:** Synchrone und asynchrone Kommunikation beschreiben zwei grundlegende Paradigmen des Nachrichtenaustauschs zwischen [[Prozess|Prozessen]], [[Thread|Threads]] oder [[Komponente|Komponenten]] in verteilten oder nebenläufigen Systemen. 

- **Synchrone Kommunikation**: Der Sender blockiert nach dem Absenden einer Nachricht, bis der Empfänger die Verarbeitung abgeschlossen und eine Antwort zurückgesendet hat. Die Ausführung des Senders wird erst fortgesetzt, wenn die Antwort vorliegt (z. B. [[Remote_Procedure_Call|RPC]] oder Methodenaufrufe in [[Monolithische_Architektur|monolithischen Systemen]]).
- **Asynchrone Kommunikation**: Der Sender setzt seine Ausführung unmittelbar nach dem Absenden der Nachricht fort, ohne auf eine Antwort zu warten. Die Verarbeitung erfolgt unabhängig, oft über [[Nachrichtenorientierte_Middleware|nachrichtenorientierte Middleware]] (z. B. [[Message_Broker]] wie RabbitMQ oder Kafka) oder [[Event_Driven_Architecture|ereignisgesteuerte Mechanismen]] (z. B. [[Observer_Pattern]]).
- **Nutzen & Zweck:** Die Wahl zwischen synchroner und asynchroner Kommunikation beeinflusst die [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Performance]] eines Systems:

- **Synchrone Kommunikation** eignet sich für:
  - Einfache, deterministische Abläufe mit klaren Abhängigkeiten (z. B. Datenbanktransaktionen).
  - Szenarien, in denen der Sender auf das Ergebnis angewiesen ist (z. B. Authentifizierung).
  - Systeme mit geringer Latenzanforderung, da Blockieren die [[Antwortzeit]] erhöht.

- **Asynchrone Kommunikation** wird bevorzugt für:
  - [[Entkopplung]] von Komponenten (z. B. in [[Microservices]] oder [[Event_Sourcing]]).
  - [[Lastverteilung]] und [[Skalierbarkeit]] durch nicht-blockierende Verarbeitung.
  - [[Fehlerbehandlung]] durch Pufferung (z. B. [[Retry_Pattern]]) oder [[Dead_Letter_Queue]].
  - Echtzeitanwendungen (z. B. Chat-Systeme, IoT-Datenverarbeitung).

Typische Anwendungsmuster sind [[Half_Sync_Half_Async]] (Kombination beider Ansätze) oder [[Active_Object]] (Objektorientierte Entkopplung).
- **Abgrenzung & Grenzen:** Die Abgrenzung ist nicht immer trennscharf:

- **Stolpersteine synchroner Kommunikation**:
  - **Blockierende Aufrufe** können zu [[Deadlock]]s oder [[Starvation]] führen, besonders in verteilten Systemen mit hoher Latenz.
  - **Kaskadierende Fehler**: Ein Ausfall des Empfängers blockiert den Sender (z. B. in [[SOAP]]-basierten Webservices).
  - **Skalierbarkeitsgrenzen**: Jeder Client benötigt eine dedizierte Verbindung (z. B. bei [[REST_API]]s mit langen Antwortzeiten).

- **Stolpersteine asynchroner Kommunikation**:
  - **Komplexität**: Erfordert zusätzliche Infrastruktur (z. B. [[Message_Broker]]) und Mechanismen zur [[Idempotenz]] oder [[Eventual_Consistency]].
  - **Debugging**: Fehlende direkte Rückmeldung erschwert die Nachverfolgbarkeit (z. B. bei [[Event_Storming]]).
  - **Zustandsmanagement**: Asynchrone Systeme benötigen oft explizite [[State_Management]]-Lösungen (z. B. [[Saga_Pattern]]).

- **Hybride Ansätze**: Muster wie [[Half_Sync_Half_Async]] oder [[Reactor_Pattern]] kombinieren beide Paradigmen, um Vorteile zu nutzen und Nachteile zu mildern (z. B. in [[Netzwerkprotokoll|Netzwerkprotokollen]] wie HTTP/2).
- **Beispiel / Code:** {'beschreibung': 'Vergleich synchroner (RPC) und asynchroner (Message Queue) Kommunikation in Java-ähnlicher Pseudocode-Notation:', 'synchron': {'beschreibung': 'Blockierender Aufruf über [[Remote_Procedure_Call|RPC]] (z. B. Java RMI):', 'code': '// Sender (Client)\nResult result = remoteService.processRequest(data); // Blockiert bis Antwort da\nSystem.out.println("Ergebnis: " + result);\n\n// Empfänger (Server)\npublic Result processRequest(Data data) {\n    return computeResult(data); // Verarbeitung erfolgt sofort\n}'}, 'asynchron': {'beschreibung': 'Nicht-blockierender Aufruf über [[Message_Broker]] (z. B. RabbitMQ):', 'code': '// Sender (Publisher)\nmessageBroker.publish("queue.requests", data); // Kein Warten auf Antwort\nSystem.out.println("Anfrage gesendet");\n\n// Empfänger (Consumer) - läuft in separatem Thread\nmessageBroker.subscribe("queue.requests", (data) -> {\n    Result result = computeResult(data);\n    messageBroker.publish("queue.responses", result); // Antwort optional\n});\n\n// Antwort-Handler (optional)\nmessageBroker.subscribe("queue.responses", (result) -> {\n    System.out.println("Asynchrone Antwort: " + result);\n});'}, 'uml_diagramm': {'beschreibung': 'Sequenzdiagramm (Mermaid-Syntax) zur Veranschaulichung:', 'code': 'sequenceDiagram\n    participant Sender\n    participant Empfänger\n    participant MessageBroker\n    \n    %% Synchrone Kommunikation\n    Sender->>Empfänger: processRequest(data)\n    Empfänger-->>Sender: Result (blockierend)\n    \n    %% Asynchrone Kommunikation\n    Sender->>MessageBroker: publish(data)\n    MessageBroker->>Empfänger: consume(data)\n    Empfänger->>MessageBroker: publish(result) (optional)\n    MessageBroker->>Sender: consume(result) (optional)'}}
